# Getting started

## Requirements

- Node.js 22.12.0 or later (for development)
- Supported browsers: latest versions of Chrome / Edge / Firefox / Safari (uses ES2020, Shadow DOM, and ResizeObserver)

## Installation

```bash
npm install @urthr-products/cell-ui
```

The `exports` in `package.json` are as follows.

| Specifier | Description |
| --- | --- |
| `@urthr-products/cell-ui` | ES module (`dist/cell-ui.js`). Type definitions are in `dist/index.d.ts` |
| `@urthr-products/cell-ui/style.css` | Stylesheet |
| `@urthr-products/cell-ui/iife` | Single file for `<script>` tags (global `CellUI`) |

## Minimal setup

```html
<div id="app" style="height: 500px"></div>
```

```ts
import { Spreadsheet } from '@urthr-products/cell-ui';
import '@urthr-products/cell-ui/style.css';

const sheet = new Spreadsheet(document.getElementById('app')!, {
  rows: 200,
  cols: 26,
  locale: 'en',
});

sheet.model.setCell(0, 0, { value: 'Product', style: { bold: true } });
sheet.model.setValue(1, 0, 'Apple');
sheet.model.events.on('change', () => save(sheet.toJSON()));
```

Give the container a height (`.cui-root` fills 100% of its parent element). If you want the size to be determined by the number of rows and columns, use [`fitContent`](./layout.md#fixed-size-tables-fitcontent).

## Development commands

| Command | Description |
| --- | --- |
| `npm run dev` | Vite development server. `/` is the demo (`index.html` + `examples/demo.ts`) and `/embed.html` is the embedding samples |
| `npm run build` | Build the library (ES / IIFE / CSS / type definitions) |
| `npm test` | Unit tests (vitest + jsdom) |
| `npm run typecheck` | `tsc --noEmit` |
| `npm run e2e` | Behavior check that drives the demo and samples in Chromium (run after `npm run build`; screenshots go to `e2e-out/`) |

See the [Development guide](./development.md) for details.

## What to read next

- Overview of all settings: [Options](./options.md)
- Integrating into an existing system: [Embedding guide](./embedding.md)
- Using it as a small fixed table: [Layout and UI parts](./layout.md)
