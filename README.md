# tree-project

Small, framework-agnostic CSS: buttons, cards, inputs, lists, layout helpers and automatic dark mode.

## Install

```sh
npm install tree-project
```

## Use

With a bundler (Vite, webpack, etc.):

```js
import 'tree-project';
```

Or with a plain `<link>` from a CDN:

```html
<link rel="stylesheet" href="https://unpkg.com/tree-project/styles.css">
```

## Classes

| Group | Classes |
| --- | --- |
| Layout | `container`, `stack`, `row`, `grow`, `muted` |
| Card | `card` |
| Button | `btn`, `btn-primary`, `btn-soft`, `btn-danger`, sizes `btn-xs` `btn-sm` `btn-lg` `btn-xl` |
| Form | `input`, sizes `input-xs` `input-sm` `input-lg` `input-xl` |
| List | `list`, `done` |

```html
<div class="container stack">
  <div class="card">
    <h2>Hello</h2>
    <div class="row">
      <input class="input grow" placeholder="Type…">
      <button class="btn btn-primary">Save</button>
    </div>
  </div>
</div>
```

## Sizes

Everything uses one 5-step scale: `xs`, `sm`, `md`, `lg`, `xl`. Spacing utilities also have `0`.

| Utility | Classes | Variable |
| --- | --- | --- |
| Padding | `p-*`, `px-*`, `py-*`, `pt-*`, `pr-*`, `pb-*`, `pl-*` | `--ui-space-*` |
| Margin | `m-*`, `mx-*`, `my-*`, `mt-*`, `mr-*`, `mb-*`, `ml-*`, `mx-auto` | `--ui-space-*` |
| Gap | `gap-*` | `--ui-space-*` |
| Border radius | `rounded-*`, `rounded-0`, `rounded-full` | `--ui-radius-*` |
| Border width | `border-*`, `border-0` | `--ui-border-*` |
| Font size | `text-*` | `--ui-text-*` |

## Colour classes

`text-primary`, `text-muted`, `text-danger`, `text-success`, `text-warning`, `bg-primary`, `bg-primary-soft`, `bg-surface`, `border-primary`.

```html
<div class="card p-xl rounded-lg">
  <p class="text-sm mb-md">Small text</p>
  <button class="btn btn-primary btn-lg rounded-full">Go</button>
</div>
```

Buttons and inputs are `md` by default, so there is no `btn-md` or `input-md` class.

## Theming

Set **one** colour and the rest of the palette is generated from it:

```css
:root {
  --ui-theme: #0ea5e9;
}
```

From `--ui-theme` you get, in both light and dark mode:

- `--ui-primary`, `--ui-primary-hover`, `--ui-primary-active`: buttons, links, accents (lifted automatically in dark mode)
- `--ui-primary-soft`, `--ui-primary-soft-hover`, `--ui-primary-strong`: tinted backgrounds and the text that goes on them
- `--ui-primary-text`: black or white, whichever is readable on the primary colour
- `--ui-bg`, `--ui-surface`, `--ui-border`, `--ui-text`, `--ui-muted`: greys with a hint of the theme hue so everything matches

`--ui-tint` controls how much of the theme hue goes into the greys: `0` = neutral grey, `1` = default, `2` = stronger.

Give one section its own theme with the `ui-theme` class:

```html
<section class="ui-theme" style="--ui-theme: #e11d48">
  <button class="btn btn-primary">Rose button</button>
</section>
```

Any generated colour can still be overridden by hand, e.g. `--ui-bg: #fff;`. Status colours are `--ui-danger`, `--ui-success` and `--ui-warning`.

Change a whole size scale the same way, e.g. `--ui-space-md: 16px;` or `--ui-radius-lg: 20px;`. Other defaults: `--ui-radius`, `--ui-gap`, `--ui-font`.

Needs a browser from 2024 or later (`color-mix()` and relative colours).

## Publish

```sh
npm login
npm publish --access public
npm version patch   # before republishing
```
