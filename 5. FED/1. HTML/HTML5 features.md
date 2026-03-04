# HTML5 features

[[5. FED/1. HTML/Semantic HTML]] · [[5. FED/1. HTML/ARIA attributes]]

## Обзор

HTML5 — спецификация 2014 года. Вводит новые семантические элементы, API, медиа-поддержку и упрощённый синтаксис.

## Семантические элементы

См. [[5. FED/1. HTML/Semantic HTML]]. `<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<aside>`, `<footer>`, `<figure>`, `<figcaption>`, `<mark>`, `<time>`, `<details>`, `<summary>`.

## Медиа

### `<audio>` и `<video>`

```html
<video controls width="640">
  <source src="video.mp4" type="video/mp4">
  <source src="video.webm" type="video/webm">
  Fallback текст
</video>

<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
</audio>
```

- `controls` — встроенные элементы управления
- `autoplay`, `muted`, `loop`, `preload`
- `<source>` — несколько форматов для fallback

### `<canvas>`

2D-рисование через JavaScript API. Пиксельный bitmap.

```html
<canvas id="c" width="300" height="150"></canvas>
<script>
  const ctx = document.getElementById('c').getContext('2d');
  ctx.fillRect(10, 10, 100, 50);
</script>
```

## Формы

### Новые типы `input`

| Тип | Назначение |
| :-- | :-- |
| `email`, `url`, `tel` | Семантика + валидация/клавиатура на мобильных |
| `number`, `range` | Числа, слайдер |
| `date`, `time`, `datetime-local` | Дата и время |
| `search`, `color` | Поиск, выбор цвета |
| `file` | Файлы (`accept`, `multiple`) |

### Новые атрибуты

- `required` — обязательное поле
- `placeholder` — подсказка
- `autofocus` — фокус при загрузке
- `pattern` — regex для валидации
- `min`, `max`, `step` — для `number`, `range`, `date`
- `minlength`, `maxlength` — длина строки

## API

| API | Назначение |
| :-- | :-- |
| **Geolocation** | `navigator.geolocation` — координаты |
| **Local Storage** | `localStorage`, `sessionStorage` — хранение данных |
| **History** | `history.pushState`, `replaceState` — SPA-навигация без перезагрузки |
| **Drag and Drop** | События `dragstart`, `dragover`, `drop` |
| **Web Workers** | Выполнение скрипта в фоновом потоке |
| **WebSocket** | Двусторонняя связь с сервером |
| **Intersection Observer** | Отслеживание видимости элемента |

## Документ и синтаксис

- `<!DOCTYPE html>` — минимальный doctype
- `<meta charset="UTF-8">` — кодировка
- Самозакрывающие теги: `<br>`, `<hr>`, `<img>`, `<input>` — без слэша
- Атрибуты без кавычек допустимы, но не рекомендуются
