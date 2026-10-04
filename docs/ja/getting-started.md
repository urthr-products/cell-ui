# はじめに

## 必要環境

- Node.js 22.12.0 以上(開発時)
- 対応ブラウザ: Chrome / Edge / Firefox / Safari の最新版(ES2020、Shadow DOM、ResizeObserver を使用)

## インストール

npm パッケージはまだ公開していません。リポジトリを取得してビルドし、必要に応じてローカル配布用の tarball を作成します。

```bash
git clone https://github.com/urthr-products/cell-ui.git
cd cell-ui
npm ci
npm run build
npm pack                          # urthr-products-cell-ui-0.1.0.tgz
```

最初の npm リリース以降は、次のコマンドでインストールできます。

```bash
npm install @urthr-products/cell-ui
```

`package.json` の `exports` は次のとおりです。

| 指定 | 内容 |
| --- | --- |
| `@urthr-products/cell-ui` | ES モジュール(`dist/cell-ui.js`)。型定義は `dist/index.d.ts` |
| `@urthr-products/cell-ui/style.css` | スタイルシート |
| `@urthr-products/cell-ui/iife` | `<script>` タグ用の単一ファイル(グローバル `CellUI`) |

## 最小構成

```html
<div id="app" style="height: 500px"></div>
```

```ts
import { Spreadsheet } from '@urthr-products/cell-ui';
import '@urthr-products/cell-ui/style.css';

const sheet = new Spreadsheet(document.getElementById('app')!, {
  rows: 200,
  cols: 26,
  locale: 'ja',
});

sheet.model.setCell(0, 0, { value: '商品', style: { bold: true } });
sheet.model.setValue(1, 0, 'りんご');
sheet.model.events.on('change', () => save(sheet.toJSON()));
```

コンテナには高さを与えてください(`.cui-root` は親要素を 100% で埋めます)。行数・列数からサイズを決めたい場合は [`fitContent`](./layout.md#固定サイズの表fitcontent) を使います。

## 開発コマンド

| コマンド | 内容 |
| --- | --- |
| `npm run dev` | Vite の開発サーバー。`/` がデモ(`index.html` + `examples/demo.ts`)、`/embed.html` が埋め込みサンプル |
| `npm run build` | ライブラリをビルド(ES / IIFE / CSS / 型定義) |
| `npm test` | ユニットテスト(vitest + jsdom) |
| `npm run typecheck` | `tsc --noEmit` |
| `npm run e2e` | Chromium でデモとサンプルを操作する動作確認(`npm run build` 後に実行。スクリーンショットは `e2e-out/`) |

詳しくは [開発ガイド](./development.md) を参照してください。

## 次に読むもの

- 設定項目の全体像: [オプション一覧](./options.md)
- 既存システムへの組み込み: [埋め込みガイド](./embedding.md)
- 小さな固定表として使う: [レイアウトと UI 部品](./layout.md)
