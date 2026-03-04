# Debounce

## Общая информация

**Debounce** (отложенное выполнение) — это техника, которая откладывает выполнение функции до тех пор, пока не пройдёт определённый период времени без новых вызовов. Если за это время произойдёт новый вызов, таймер сбрасывается и отсчёт начинается заново.

### Зачем нужен debounce?

- **Поиск в реальном времени** — не отправлять запрос на сервер при каждом нажатии клавиши
- **Обработка resize/scroll** — не выполнять тяжёлые вычисления при каждом пикселе прокрутки
- **Валидация форм** — проверять поле после паузы ввода
- **Автосохранение** — сохранять документ только когда пользователь перестал печатать

### Debounce vs Throttle

- **Debounce** — выполняет функцию **после** паузы в вызовах. Подходит для поиска, автосохранения, валидации.
- **Throttle** — выполняет функцию **не чаще** чем раз в N мс. Подходит для scroll, resize, drag.

### Stale closure

**Stale closure** (устаревшее замыкание) — когда функция, отложенная по времени (например, через debounce или таймер), сохраняет в замыкании старые значения переменных. При вызове она «видит» не актуальный state/props, а те, что были на момент создания. В React это часто проявляется в debounced-колбэках: если передать callback напрямую в debounce, он будет вызывать версию с устаревшим state. Решение — хранить callback в `ref` и обновлять его при каждом рендере, вызывая `ref.current` в момент срабатывания таймера.

---

## 1. Простой пример на JavaScript

```javascript
function debounce(fn, delay) {
  let timeoutId;

  return function (...args) {
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => fn.apply(this, args), delay);
  };
}

// Использование
const handleSearch = debounce((query) => {
  console.log('Поиск:', query);
}, 300);

input.addEventListener('input', (e) => handleSearch(e.target.value));
```

### Объяснение (JavaScript)

- **`timeoutId`** — хранит идентификатор таймера. При каждом новом вызове предыдущий таймер отменяется через `clearTimeout`.
- **Возвращаемая функция** — создаёт замыкание над `timeoutId` и `fn`, поэтому каждый вызов «видит» актуальное состояние.
- **`fn.apply(this, args)`** — сохраняет контекст `this` (важно, если debounced-функция используется как метод объекта) и передаёт все аргументы.
- **`delay`** — функция выполнится только если за `delay` мс не было новых вызовов.

---

## 2. TypeScript версия

```typescript
function debounce<T extends (...args: unknown[]) => unknown>(
  fn: T,
  delay: number
): (...args: Parameters<T>) => void {
  let timeoutId: ReturnType<typeof setTimeout> | undefined;

  return function (this: ThisParameterType<T>, ...args: Parameters<T>) {
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => fn.apply(this, args), delay);
  };
}

// Использование с типизацией
const handleSearch = debounce((query: string) => {
  console.log('Поиск:', query);
}, 300);

// Ошибка типов — TypeScript поймает неверный аргумент
// handleSearch(123); // Error: Argument of type 'number' is not assignable to parameter of type 'string'
handleSearch('react'); // OK
```

### Объяснение (TypeScript)

- **`T extends (...args: unknown[]) => unknown`** — generic-тип для любой функции. Сохраняем сигнатуру исходной функции.
- **`Parameters<T>`** — встроенный утилитарный тип, извлекает типы аргументов из функции.
- **`ReturnType<typeof setTimeout>`** — тип идентификатора таймера (в браузере `number`, в Node.js может быть `NodeJS.Timeout`).
- **`ThisParameterType<T>`** — тип контекста `this` для функции.
- Типизация даёт автодополнение и проверку аргументов при вызове debounced-функции.

---

## 3. Custom Hook для React

```tsx
import { useCallback, useRef } from 'react';

function useDebounce<T extends (...args: unknown[]) => unknown>(
  callback: T,
  delay: number
): (...args: Parameters<T>) => void {
  const timeoutRef = useRef<ReturnType<typeof setTimeout> | null>(null);
  const callbackRef = useRef(callback);

  // Всегда держим актуальную ссылку на callback
  callbackRef.current = callback;

  const debouncedFn = useCallback(
    (...args: Parameters<T>) => {
      if (timeoutRef.current) {
        clearTimeout(timeoutRef.current);
      }

      timeoutRef.current = setTimeout(() => {
        callbackRef.current(...args);
        timeoutRef.current = null;
      }, delay);
    },
    [delay]
  );

  return debouncedFn;
}

// Использование в компоненте
function SearchInput() {
  const [query, setQuery] = useState('');
  const [results, setResults] = useState<string[]>([]);

  const searchAPI = useCallback(async (q: string) => {
    const res = await fetch(`/api/search?q=${q}`);
    const data = await res.json();
    setResults(data.results);
  }, []);

  const debouncedSearch = useDebounce(searchAPI, 300);

  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    const value = e.target.value;
    setQuery(value);
    debouncedSearch(value);
  };

  return (
    <>
      <input value={query} onChange={handleChange} />
      <ul>{results.map((r) => <li key={r}>{r}</li>)}</ul>
    </>
  );
}
```

### Объяснение (React Hook)

- **`useRef` для таймера** — `timeoutRef` сохраняет идентификатор между рендерами. При ре-рендере компонента ref не сбрасывается, в отличие от обычной переменной.
- **`callbackRef.current = callback`** — при каждом рендере обновляем ссылку на callback. Это защита от stale closure: debounced-функция всегда вызывает актуальную версию callback (с правильными state/props).
- **`useCallback` с `[delay]`** — debounced-функция пересоздаётся только при смене `delay`. Это предотвращает лишние ре-рендеры дочерних компонентов, если debounced-функция передаётся как prop.
- **Почему не `useState` для callback?** — если хранить callback в state, получим гонку: debounce может вызвать устаревшую версию. Ref обновляется синхронно при каждом рендере.

---

## Дополнительно: отмена при размонтировании

При размонтировании компонента таймер может «выстрелить» после unmount. Чтобы избежать утечек и вызовов `setState` на размонтированном компоненте:

```tsx
function useDebounce<T extends (...args: unknown[]) => unknown>(
  callback: T,
  delay: number
): (...args: Parameters<T>) => void {
  const timeoutRef = useRef<ReturnType<typeof setTimeout> | null>(null);
  const callbackRef = useRef(callback);
  const mountedRef = useRef(true);

  callbackRef.current = callback;

  useEffect(() => {
    mountedRef.current = true;
    return () => {
      mountedRef.current = false;
      if (timeoutRef.current) clearTimeout(timeoutRef.current);
    };
  }, []);

  return useCallback(
    (...args: Parameters<T>) => {
      if (timeoutRef.current) clearTimeout(timeoutRef.current);

      timeoutRef.current = setTimeout(() => {
        if (mountedRef.current) {
          callbackRef.current(...args);
        }
        timeoutRef.current = null;
      }, delay);
    },
    [delay]
  );
}
```
