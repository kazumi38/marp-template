# Marp 日本語エグゼクティブプレゼンテーションスライドテーマ

このテーマは、日本語のエグゼクティブ向けプレゼンテーションスライドを作成するための Marp テーマです。30種類以上のデザインパターンを提供し、5分以内にプロフェッショナルなスライドを作成できます。

## 前提
Githubが提供しているspeckitがどこまで使えるのか検証しています。
あまりレビュー・修正しないで実装できるのか確認しております。

## 特徴

- **日本語対応**: Hiragino Sans、Yu Gothic、Noto Sans JP の優先フォントスタック
- **30+ デザインパターン**: カード、フローチャート、テーブル、リスト、メディア、ハイライト、レイアウト、数値パターン
- **モバイル対応**: レスポンシブデザインでタブレット・モバイル対応
- **アクセシビリティ**: WCAG AA 準拠の色コントラスト比
- **PDF エクスポート**: 高品質な PDF 出力に対応

## インストール

### 前提条件

- Node.js 16 以上
- npm または yarn

### インストール手順

1. リポジトリをクローンまたはダウンロード
2. 依存関係をインストール:

```bash
npm install
```

## 使用方法

### 基本的なスライド作成

1. `examples/` ディレクトリのサンプルファイルをコピー
2. テーマを指定:

```markdown
---
theme: marp-jp-exec
lang: ja
---

# タイトルスライド
<!-- class: title-slide -->

# プレゼンテーションタイトル

部署名 / 作成者名

---

# 本文スライド
<!-- class: body-slide -->

## セクションタイトル

本文の内容をここに記述します。
```

### デザインパターンの使用

各パターンは HTML コメントでクラスを指定します:

```markdown
<!-- class: body-slide pattern-card-3col -->

# 3カラムカード

- **機能 A**: 説明
- **機能 B**: 説明
- **機能 C**: 説明
```

利用可能なパターン:
- **カード**: `pattern-card-2col`, `pattern-card-3col`, `pattern-card-4col`, `pattern-card-mixed`
- **フローチャート**: `pattern-flowchart-h`, `pattern-flowchart-v`, `pattern-flowchart-d`, `pattern-flowchart-c`
- **テーブル**: `pattern-table-simple`, `pattern-table-multiheader`, `pattern-table-fullwidth`
- **リスト**: `pattern-list-bullet`, `pattern-list-numbered`, `pattern-list-mixed`, `pattern-list-nested`, `pattern-list-indented`
- **メディア**: `pattern-media-fullbleed`, `pattern-media-sidebyside`, `pattern-media-gallery-2`, `pattern-media-gallery-3`
- **ハイライト**: `pattern-highlight-info`, `pattern-highlight-warning`, `pattern-highlight-error`, `pattern-highlight-success`
- **レイアウト**: `pattern-layout-2col`, `pattern-layout-3col`, `pattern-layout-asymmetric`
- **数値**: `pattern-numeric-progress`, `pattern-numeric-badge`, `pattern-numeric-keynum`

### PDF エクスポート

```bash
# 単一ファイル
npx @marp-team/marp-cli slides.md --output slides.pdf --theme .styles/theme-jp-exec.css

# バッチエクスポート
npm run pdf
```

### ライブプレビュー

```bash
# ウォッチモード
npm run watch

# サーバーモード
npm run serve
```

## プロジェクト構造

```
marp-template/
├── .styles/
│   └── theme-jp-exec.css    # メインテーマファイル
├── examples/
│   ├── example-title.md     # タイトルスライド例
│   ├── example-body.md      # 本文スライド例
│   └── pattern-examples.md  # 全パターン例
├── samples/                 # 生成されたPDFサンプル
├── specs/                   # 仕様書とタスク
├── package.json             # プロジェクト設定
└── README.md               # このファイル
```

## カスタマイズ

### 色の変更

`.styles/theme-jp-exec.css` の CSS カスタムプロパティを編集:

```css
:root {
  --color-text-base: #232F3E;    /* 基本文字色 */
  --color-accent-blue: #4040BF; /* 青アクセント (75%ルール適用) */
  --color-accent-red: #BF4040;  /* 赤アクセント (75%ルール適用) */
  --color-accent-green: #40BF40; /* 緑アクセント (75%ルール適用) */
}
```

### フォントの変更

フォントスタックをカスタマイズ:

```css
body, h1, h2, h3, h4, h5, h6, p, ul, ol, li {
  font-family: 'Your Font', 'Hiragino Sans', 'Yu Gothic', 'Noto Sans JP', sans-serif;
}
```

## 対応環境

- **OS**: macOS, Windows, Linux
- **ブラウザ**: Chrome, Firefox, Safari, Edge
- **Marp CLI**: 1.0.0 以上

## ライセンス

このプロジェクトは MIT ライセンスの下で公開されています。

## 貢献

1. Fork してブランチを作成
2. 変更をコミット
3. Pull Request を作成

## サポート

問題や質問がある場合は、Issue を作成してください。
