# cell-ui

[![CI](https://github.com/urthr-products/cell-ui/actions/workflows/ci.yml/badge.svg)](https://github.com/urthr-products/cell-ui/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)

An Excel-like spreadsheet UI library for the browser, maintained by **urthr products**. It is framework-free (TypeScript + DOM only) and keeps formula evaluation outside the core so applications can add it through plugins.

> **Pre-1.0 status:** the public API is usable, but may change before the first stable release. The npm package is prepared as `@urthr-products/cell-ui` and will become installable with the first npm release.

- **Copy & paste to/from Microsoft Excel** — values and formatting round-trip through Excel-compatible `text/html` and `text/plain`.
- **Excel keyboard shortcuts** — navigation, selection, editing, clipboard, undo/redo, formatting, row/column selection and more.
- **Styling toolbar** — fonts, text decoration, colours, fill, alignment, wrapping, borders and clear formatting.
- **Built for cell UIs** — virtual scrolling, resize and auto-fit, fill handle, row/column operations, menus, formula bar, status bar and undo/redo.
- **Data validation** — number and list-selection rules with an in-cell dropdown.
- **Extensible** — command registry, keymap, toolbars, menus, value parsers, display resolvers, cell renderers and per-cell metadata.
- **Three embedding options** — ES module, single-file IIFE build and the `<cell-ui-sheet>` Web Component.

## Documentation

Documentation is available in English and Japanese:

- [English documentation](./docs/en/README.md)
- [日本語ドキュメント](./docs/ja/README.md)

| Document | Contents |
| --- | --- |
| [Getting started](./docs/en/getting-started.md) | Installation, minimal setup, development commands |
| [Options](./docs/en/options.md) | Constructor options and Web Component attributes |
| [Embedding guide](./docs/en/embedding.md) | Script tag, Web Component, React, Vue and iframe integration |
| [Layout and UI parts](./docs/en/layout.md) | Fixed-size tables, rows, columns, headers and bars |
| [Keyboard shortcuts](./docs/en/keyboard-shortcuts.md) | Excel-compatible key list |
| [Clipboard](./docs/en/clipboard.md) | Copy and paste with Excel |
| [Styling](./docs/en/styling.md) | Formatting, borders, toolbar and themes |
| [Validation](./docs/en/validation.md) | Number and list-selection validation |
| [Extensibility](./docs/en/extensibility.md) | Plugin API |
| [API reference](./docs/en/api.md) | Classes and methods |
| [Data format](./docs/en/data-format.md) | Snapshot JSON |
| [Architecture](./docs/en/architecture.md) | Internal design |
| [Development guide](./docs/en/development.md) | Build, test and CI |

## Installation

The npm package has not been published yet. To evaluate the current source build:

```bash
git clone https://github.com/urthr-products/cell-ui.git
cd cell-ui
npm ci
npm run build
```

Starting with the first npm release, installation will be:

```bash
npm install @urthr-products/cell-ui
```

```ts
import { Spreadsheet } from '@urthr-products/cell-ui';
import '@urthr-products/cell-ui/style.css';

const sheet = new Spreadsheet(document.getElementById('app')!, {
  rows: 1000,
  cols: 52,
  locale: 'en',
});

sheet.model.setValue(0, 0, 'Hello');
sheet.model.setCell(0, 1, {
  value: 42,
  style: { bold: true, color: '#c00000' },
});
```

For an unbundled Web Component deployment, build the project and serve the generated files:

```html
<link rel="stylesheet" href="cell-ui.css">
<script src="cell-ui.iife.js"></script>
<cell-ui-sheet rows="10" cols="5" fit-content column-labels="Item,Qty,Price,Notes"></cell-ui-sheet>
```

## Development

```bash
npm ci
npm run dev       # Demo at http://localhost:5173; embedding samples at /embed.html
npm run typecheck
npm test
npm run build
npx playwright install chromium
npm run e2e
```

## Support

Please read [SUPPORT.md](./SUPPORT.md) before opening an issue. Maintenance is provided on a best-effort basis; individual integration work and guaranteed response times are not included.

Financial support is optional and does not affect access to features. Funding links will appear through GitHub's Sponsor button after the sponsorship account is activated.

## Contributing and security

- Contributions: [CONTRIBUTING.md](./CONTRIBUTING.md)
- Security reports: [SECURITY.md](./SECURITY.md)
- Community expectations: [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md)
- Changes: [CHANGELOG.md](./CHANGELOG.md)

## License

MIT © 2026 urthr products. See [LICENSE](./LICENSE).
