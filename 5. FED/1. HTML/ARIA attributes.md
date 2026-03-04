# ARIA attributes (Accessibility)

[[5. FED/1. HTML/Semantic HTML]] · [[5. FED/1. HTML/HTML5 features]]

## Определение

**ARIA** (Accessible Rich Internet Applications) — набор атрибутов, которые дополняют HTML для вспомогательных технологий (скринридеры, браузерные расширения). Используется, когда нативного HTML недостаточно.

## Правило №1

**Сначала [[5. FED/1. HTML/Semantic HTML]].** ARIA — только когда нет подходящего нативного элемента или его поведения.

## Основные атрибуты

### Роли (`role`)

Определяют тип элемента для assistive tech.

```html
<div role="button" tabindex="0">Кнопка на div</div>
<div role="alert">Сообщение об ошибке</div>
<div role="dialog" aria-modal="true">Модальное окно</div>
```

### Состояния и свойства

| Атрибут | Назначение |
| :-- | :-- |
| `aria-label` | Текстовое описание элемента (когда видимый текст отсутствует) |
| `aria-labelledby` | ID элемента, который является подписью |
| `aria-describedby` | ID элемента с дополнительным описанием |
| `aria-hidden="true"` | Скрыть от дерева доступности |
| `aria-expanded` | Открыт/закрыт (меню, аккордеон) |
| `aria-pressed` | Нажата/не нажата (toggle-кнопка) |
| `aria-checked` | Состояние чекбокса/радио |
| `aria-current` | Текущий элемент (вкладка, пункт навигации) |
| `aria-live` | Область с динамическим контентом (`polite`, `assertive`, `off`) |
| `aria-modal="true"` | Модальное окно (фокус внутри, остальное недоступно) |

### Связи

```html
<button aria-controls="menu-id" aria-expanded="false" aria-haspopup="true">
  Меню
</button>
<div id="menu-id" role="menu">...</div>
```

## Частые ошибки

1. **Дублирование** — `role="button"` на `<button>` не нужен
2. **`aria-label` на видимом тексте** — скринридер может прочитать оба
3. **`aria-hidden` на фокусируемом элементе** — противоречие
4. **`role="presentation"`** — убирает семантику; использовать осторожно

## Живые регионы (`aria-live`)

Для динамического контента (уведомления, обновления без перезагрузки):

- `aria-live="polite"` — объявить при паузе
- `aria-live="assertive"` — объявить сразу (критичные сообщения)
- `aria-live="off"` — не объявлять (по умолчанию)
