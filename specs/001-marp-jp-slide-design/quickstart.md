# Quick Start Guide: Marp 日本語スライドデザインテンプレート

**Date**: 2026-04-06  
**Theme Version**: 1.0  
**Marp CLI Version**: >=1.0.0

---

## はじめに

このテンプレートは、Marp で日本語の上司向け説明スライドを効率よく作成するための CSS テーマです。2 つのレイアウト（タイトルスライド・本文スライド）と 30+ のコンテンツパターンで、統一感のある資料を短時間で実現できます。

---

## インストール

### 1. Marp CLI をインストール

```bash
npm install -g @marp-team/marp-cli
```

または package.json に追加：

```bash
npm install --save-dev @marp-team/marp-cli
```

### 2. テーマファイルをコピー

このリポジトリから `theme-jp-exec.css` を `.styles/` フォルダにコピーします：

```bash
cp theme-jp-exec.css .styles/
```

### 3. Markdown ファイルを作成

```bash
cat > my-presentation.md << 'EOF'
---
theme: marp-jp-exec
lang: ja
---

# My Awesome Presentation
## Engineering Division
### Yamada Taro
EOF
```

---

## 基本的な使い方

### タイトルスライド

最初のスライドをタイトルスライドにします：

```markdown
# プレゼンテーションタイトル
## 部署名
### 担当者名
```

**自動レイアウト**:
- タイトルが中央に 28pt で表示
- 部署名・氏名が下に 12pt で表示（75% の不透明度）

---

### 本文スライド

本文スライドを作成します：

```markdown
---
<!-- class: body-slide -->

# スライドタイトル

リード文（要約）

**ポイント 1**: 説明文  
**ポイント 2**: 説明文
```

**自動レイアウト**:
- タイトルは右上に 18pt
- タイトル下に 3pt の水平線
- その下にリード文（16pt）
- 下に本文エリア

---

## デザインパターン使用例

### パターン 1: 3 カラムカード

```markdown
---
<!-- class: body-slide pattern-card-3col -->

# Key Features

- **Speed**: Fast performance
- **Reliability**: 99.9% uptime
- **Scalability**: Grows with you
```

**結果**: 3 つの箱形カードが横並びで表示されます。

---

### パターン 2: 表

```markdown
---
<!-- class: body-slide pattern-table-simple -->

# Comparison

| Feature | Option A | Option B |
|---------|----------|----------|
| Cost    | $100     | $150     |
| Speed   | 5ms      | 3ms      |
| Setup   | 1 hour   | 2 hours  |
```

**結果**: シンプルな表が表示されます。

---

### パターン 3: 情報ボックス

```markdown
---
<!-- class: body-slide pattern-highlight-info -->

# Implementation Note

This approach improves performance by 40% without increasing costs.
```

**結果**: 青い情報ボックスが表示（左に 4px の青い縁）

---

### パターン 4: 警告ボックス

```markdown
---
<!-- class: body-slide pattern-highlight-warning -->

# Important

Please note: Testing is required before deployment.
```

**結果**: 赤い警告ボックスが表示（左に 4px の赤い縁）

---

## すべての利用可能なパターン

### Card Layouts （4 種）
```markdown
<!-- class: pattern-card-2col --> 2 列カード
<!-- class: pattern-card-3col --> 3 列カード
<!-- class: pattern-card-4col --> 4 列カード
<!-- class: pattern-card-mixed --> 混合レイアウト
```

### Flowcharts （4 種）
```markdown
<!-- class: pattern-flowchart-h --> 横並びフロー
<!-- class: pattern-flowchart-v --> 縦並びフロー
<!-- class: pattern-flowchart-d --> 斜めフロー
<!-- class: pattern-flowchart-c --> 円形フロー
```

### Tables （3 種）
```markdown
<!-- class: pattern-table-simple --> シンプルな表
<!-- class: pattern-table-multiheader --> 複数ヘッダー表
<!-- class: pattern-table-fullwidth --> フル幅表
```

### Highlight Boxes （4 種）
```markdown
<!-- class: pattern-highlight-info --> 情報（青）
<!-- class: pattern-highlight-warning --> 警告（赤）
<!-- class: pattern-highlight-error --> エラー（濃赤）
<!-- class: pattern-highlight-success --> 成功（緑）
```

### List Patterns （5 種）
```markdown
<!-- class: pattern-list-bullet --> 箇条書き
<!-- class: pattern-list-numbered --> 番号付き
<!-- class: pattern-list-mixed --> 混合リスト
<!-- class: pattern-list-nested --> ネストされたリスト
<!-- class: pattern-list-indented --> インデント付き
```

### Media Patterns （4 種）
```markdown
<!-- class: pattern-media-fullbleed --> 画像全体表示
<!-- class: pattern-media-sidebyside --> 画像テキスト並置
<!-- class: pattern-media-gallery-2 --> 2 画像ギャラリー
<!-- class: pattern-media-gallery-3 --> 3 画像ギャラリー
```

### Layout Patterns （3 種）
```markdown
<!-- class: pattern-layout-2col --> 2 列レイアウト
<!-- class: pattern-layout-3col --> 3 列レイアウト
<!-- class: pattern-layout-asymmetric --> 不定形レイアウト
```

### Numeric Patterns （3 種）
```markdown
<!-- class: pattern-numeric-progress --> プログレスバー
<!-- class: pattern-numeric-badge --> ステータスバッジ
<!-- class: pattern-numeric-keynum --> 大きな数字表示
```

---

## カラーパレット

このテンプレートは以下のカラーパレットを使用します：

| 用途 | 色コード | RGB |
|-----|--------|-----|
| **本文色** | #232F3E | 濃紺（日本語フォント向け） |
| **補助色** | #666666 | 灰色 |
| **強調色（赤）** | #BF4040 | 抑えた赤（75%） |
| **強調色（青）** | #4040BF | 抑えた青（75%） |
| **強調色（緑）** | #40BF40 | 抑えた緑（75%） |
| **背景色** | #FFFFFF | 白 |
| **区切り線** | #CCCCCC | 薄い灰色 |

---

## フォント

このテンプレートは日本語対応の複数フォント指定を使用します：

1. **Hiragino Sans** (macOS に標準搭載)
2. **Yu Gothic** (Windows 7 SP1 以降に標準搭載)
3. **Noto Sans JP** (Google Fonts から自動配信)
4. **sans-serif** (フォールバック)

環境にインストール済みのフォントが自動選択されるため、別途インストール不要です。

---

## Markdown 記法クイックリファレンス

### 見出し

```markdown
# 見出し 1 → h1 (タイトルスライドで 28pt)
## 見出し 2 → h2 (本文スライドで 18pt)
### 見出し 3 → h3
```

### 強調

```markdown
**太字**        → 太字
*イタリック*    → イタリック
`コード`        → 等幅フォント
```

### リスト

```markdown
- 箇条書き
  - ネストも可能

1. 番号付き
2. リスト
```

### リンク・画像

```markdown
[リンク](https://example.com)
![画像](image.jpg)
```

---

## PDF として出力

Marp CLI で PDF に変換：

```bash
marp my-presentation.md --output my-presentation.pdf
```

複数ファイルを一度に変換：

```bash
marp *.md --output build/ --pdf
```

---

## トラブルシューティング

### フォントが正しく表示されない

**原因**: Web フォント（Noto Sans JP）の読み込みに失敗している

**解決策**:
1. インターネット接続を確認
2. Google Fonts へのアクセスが可能か確認
3. Safari や特定ブラウザでは、Local フォント優先度が異なる可能性あり

---

### パターンが適用されない

**原因**: `<!-- class: pattern-* -->` コメント記法が誤っている

**確認**:
```markdown
<!-- class: body-slide pattern-card-3col -->
← 正しい（両方指定）

<!-- class: pattern-card-3col -->
← これだけでも OK（body-slide は自動適用される場合）
```

---

### PDF 出力が崩れている

**原因**: 画面幅が狭い環境での PDF 出力

**解決策**:
1. `--width 1920 --height 1080` オプションで解像度指定
   ```bash
   marp my-presentation.md --pdf --width 1920 --height 1080
   ```
2. または、モニター 1920x1080 で通常ビューにして画面キャプチャ

---

## よくある質問（FAQ）

### Q: パターンを追加できますか？

**A**: はい。CSS を編集して新しいクラスを追加できます。

```css
.pattern-my-custom {
  display: flex;
  gap: 20px;
}
```

その後、Markdown で使用：
```markdown
<!-- class: body-slide pattern-my-custom -->
```

---

### Q: 色を変更できますか？

**A**: はい。CSS 変数を上書きできます。

テーマファイルの最上部に追加：
```css
:root {
  --color-text-base: #333333; /* デフォルト #232F3E */
  --color-accent-red: #FF6B6B; /* デフォルト #BF4040 */
}
```

---

### Q: スライド数が多い場合、パターンを統一できますか？

**A**: はい。複数 Markdown ファイルで同じテーマを使用：

```bash
# 複数ファイルで同じテーマを適用
marp chapter1.md chapter2.md --theme-set ./styles/theme-jp-exec.css --pdf
```

---

### Q: Marp のバージョン互換性は？

**A**: Marp CLI **v1.0.0 以上** で動作検証済み。`package.json` で指定：

```json
{
  "marpConfig": {
    "marp": ">=1.0.0"
  }
}
```

---

## 次のステップ

1. **example.md を確認**: リポジトリの `examples/` フォルダからテンプレートをコピー
2. **PDF サンプルを確認**: `samples/` フォルダから完成形を確認
3. **自分のスライドを作成**: 上記の例を参考に、Markdown で編集開始

---

## サポート・フィードバック

質問や改善提案は、GitHub Issues で報告してください。

---

**Quick Start Guide**: Revised 2026-04-06 | Version 1.0
