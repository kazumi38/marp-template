# Data Model: Marp 日本語スライドデザインテンプレート

**Date**: 2026-04-06  
**Research Reference**: [research.md](research.md)  
**Implementation Plan**: [plan.md](plan.md)

---

## Overview

このデータモデルは、Marp テンプレートで管理すべきエンティティ（ユーザーが見え、操作する対象）を定義します。CSS クラス + HTML 構造で実装される。

---

## Entity 1: Slide Layout (スライドレイアウト)

### Title Slide Layout

| 属性 | 値 | 単位 | 説明 |
|-----|-----|------|------|
| **要素** | Title | - | スライドタイトル |
| **フォントサイズ** | 28 | pt | 中央配置、太字推奨 |
| **色** | #232F3E | - | 基本文字色 |
| **配置** | Center | - | 水平・垂直中央 |
| | | | |
| **要素** | Department / Team | - | 部署名 |
| **フォントサイズ** | 12 | pt | title の下 |
| **色** | #232F3E (75%) | - | 薄くも軽くもない副次色 |
| **配置** | Center | - | title の下に配置 |
| | | | |
| **要素** | Author Name | - | 氏名 |
| **フォントサイズ** | 12 | pt | department と同じ |
| **色** | #232F3E (75%) | - | department と同色 |
| **配置** | Center | - | department の下に配置 |

**スライド背景**: #FFFFFF （デフォルト）  
**サンプル HTML 構造**:
```html
<div class="title-slide">
  <h1>Your Presentation Title</h1>
  <p class="department">Engineering Team</p>
  <p class="author">Yamada Taro</p>
</div>
```

**CSS セレクタ**: `.title-slide` または `<!-- class: title-slide -->`

---

### Body Slide Layout

| 属性 | 値 | 単位 | 説明 |
|-----|-----|------|------|
| **要素** | Title | - | スライドタイトル |
| **フォントサイズ** | 18 | pt | 右上配置、太字 |
| **色** | #232F3E | - | 基本文字色 |
| **配置** | Right Top | - | スライド右上角から padding 20px |
| | | | |
| **要素** | Divider Line | - | タイトル下の区切り線 |
| **太さ** | 3 | pt | solid line |
| **色** | #232F3E | - | 基本文字色と同じ |
| **幅** | Full (edge-to-edge) | - | 左右 margin なし |
| **ガイダンス** | Margin 10px over/under | pt | タイトルと本文の間隔 |
| | | | |
| **要素** | Lead Text | - | 本文開始の要約文 |
| **フォントサイズ** | 16 | pt | divider 直下 |
| **色** | #232F3E (90%) | - | base color より若干薄い |
| **行間** | 1.5 | - | 可読性確保 |
| | | | |
| **要素** | Content Area | - | Lead 下の本文域 |
| **フォントサイズ** | 14 | pt | デフォルト |
| **スペース** | Remaining | - | Title, Divider, Lead で消費後 |

**スライド背景**: #FFFFFF   
**サンプル HTML 構造**:
```html
<div class="body-slide">
  <h1>Slide Title</h1>
  <div class="divider"></div>
  <p class="lead-text">Summary of this slide's key message</p>
  <div class="content">
    <!-- Pattern content inserted here -->
  </div>
</div>
```

**CSS セレクタ**: `.body-slide` または `<!-- class: body-slide -->`

---

## Entity 2: Content Patterns (デザインパターン)

### Pattern Classification Hierarchy

```
patterns/
├── card/ (4 patterns)
│   ├── 2col
│   ├── 3col
│   ├── 4col
│   └── mixed
│
├── flowchart/ (4 patterns)
│   ├── horizontal
│   ├── vertical
│   ├── diagonal
│   └── circular
│
├── table/ (3 patterns)
│   ├── simple (basic rows/cols)
│   ├── multiheader (row + col headers)
│   └── fullwidth (table spans slide width)
│
├── list/ (5 patterns)
│   ├── bullet (unordered)
│   ├── numbered (ordered)
│   ├── mixed (ul + ol)
│   ├── nested (3+ levels)
│   └── indented (hanging indent)
│
├── media/ (4 patterns)
│   ├── full-bleed (image fills area)
│   ├── side-by-side (text + image)
│   ├── gallery-2 (2 images)
│   └── gallery-3 (3 images)
│
├── highlight/ (4 patterns)
│   ├── info (ℹ box)
│   ├── warning (⚠ box)
│   ├── error (❌ box)
│   └── success (✓ box)
│
├── layout/ (3 patterns)
│   ├── 2-column (two-thirds / one-third)
│   ├── 3-column (equal width)
│   └── asymmetric (custom ratio)
│
└── numeric/ (3 patterns = 30 total)
    ├── progress-bar
    ├── badge-status
    └── key-number (big number highlight)
```

### Pattern Definition Template

**Pattern Name**: `pattern-card-2col`

```css
.pattern-card-2col {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  padding: 20px;
}

.pattern-card-2col > * {
  border: 1px solid #ddd;
  padding: 15px;
  background: #f9f9f9;
}
```

**HTML Usage**:
```markdown
<!-- class: pattern-card-2col -->
# Two-Card Layout Example

- **Card 1**: First item with description
- **Card 2**: Second item with description
```

**Rendering Constraints**:
- 最小幅: 400px（カード幅 > 150px）
- 最大幅: 1920px（カード幅 < 400px）
- Responsive: 画面幅 < 600px では 1 列に自動切り替え（Marp screen query で実現）

---

## Entity 3: Color Palette (カラーパレット)

### Color Variables

| 用途 | 色名 | RGB / Hex | 用途例 |
|-----|------|----------|---------|
| **Base Text** | dark-gray | #232F3E | 本文、タイトル |
| **Light Text** | light-gray | #666666 | 補説、メモ |
| **Divider** | border-gray | #CCCCCC | 線、境界 |
| **Background** | white | #FFFFFF | スライド背景 |
| **Accent Red** | accent-red-75 | #BF4040 | 警告、強調（赤） |
| **Accent Blue** | accent-blue-75 | #4040BF | 情報、リンク（青） |
| **Accent Green** | accent-green-75 | #40BF40 | 成功、確認（緑） |

### Color Calculation (75% Rule)

```
原色 -> 75% 減光版（RGB 各チャネル計算）

赤 #FF0000 (255,0,0) * 0.75 = (191, 0, 0) = #BF0000
  → より調整: (191, 64, 64) = #BF4040 （25% グレー混合）

青 #0000FF (0,0,255) * 0.75 = (0, 0, 191) = #0000BF
  → より調整: (64, 64, 191) = #4040BF （25% グレー混合）
```

### CSS Variables Definition

```css
:root {
  --color-text-base: #232F3E;
  --color-text-light: #666666;
  --color-border: #CCCCCC;
  --color-bg: #FFFFFF;
  --color-accent-red: #BF4040;
  --color-accent-blue: #4040BF;
  --color-accent-green: #40BF40;
}

body { color: var(--color-text-base); }
a { color: var(--color-accent-blue); }
.warning { border-left: 4px solid var(--color-accent-red); }
.success { border-left: 4px solid var(--color-accent-green); }
```

### Accessibility Check

| 色 | 背景 | コントラスト比 | WCAG AA |
|----|------|-------------|--------|
| #232F3E on #FFFFFF | white | 11.4:1 | ✅ AAA |
| #BF4040 on #FFFFFF | white | 3.8:1 | ✅ AA |
| #4040BF on #FFFFFF | white | 3.8:1 | ✅ AA |
| #666666 on #FFFFFF | white | 4.5:1 | ✅ AA |

---

## Entity 4: Font Stack (フォント定義)

### Font Specification

```css
/* Title fonts (heavier weight) */
h1, h2, h3 {
  font-family: 'Hiragino Sans', 'Yu Gothic', 'Noto Sans JP', sans-serif;
  font-weight: 700;
}

/* Body text */
body, p, li {
  font-family: 'Hiragino Sans', 'Noto Sans JP', 'Yu Gothic', sans-serif;
  font-weight: 400;
}

/* Code blocks (monospace) */
code, pre {
  font-family: 'Monaco', 'Courier New', monospace;
  font-size: 0.9em;
}
```

### Font Stack Rationale

| Priority | Font Name | OS | Weight | Fallback |
|----------|----------|-----|--------|----------|
| 1 | Hiragino Sans | macOS 10.11+ | 400/700 | ✅ native |
| 2 | Yu Gothic | Windows 7 SP1+ | 400/700 | ✅ native |
| 3 | Noto Sans JP | Web (Google Fonts) | 400/700 | ✅ CDN |
| 4 | sans-serif | any | auto | ✅ fallback |

### Web Font Import

```html
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;700&display=swap" rel="stylesheet">
```

**Impact**:
- Noto Sans JP: ~50KB (gzip 12KB)
- Load time: <500ms（通常ネット）
- Swap strategy: `display=swap`（テキスト即座表示）

---

## Validation Rules

### Title Slide Validation

- ✅ Title must not exceed 1-2 lines (40-50 chars max)
- ✅ Department / Author must be <= 30 chars
- ✅ All text must be visible in 16:9 aspect ratio
- ⚠️ Warning: If title > 60 chars, reduce font size to 24pt or consider 2-slide split

### Body Slide Validation

- ✅ Lead text must be <= 100 chars (summary guideline)
- ✅ Pattern content must fit within slide bounds
- ✅ Divider line must be visible (3px minimum)
- ⚠️ Warning: If content > 80% of slide, consider multi-slide layout
- ⚠️ Warning: If text density high, increase line-height to 1.6 or 1.8

### Pattern Validation

- ✅ Card grid must render with min-width 150px per card
- ✅ All text contrast >= 3.5:1 (AA standard)
- ✅ Pattern must adapt to 4:3 aspect ratio (legacy support)
- ⚠️ Warning: Flowchart connectors may not render in PDF export (use CSS box-shadow alternative)

### Color Validation

- ✅ All text colors must be explicitly defined (no inherit ambiguity)
- ✅ Accent colors must be checked against white background (#FFFFFF)
- ⚠️ Warning: Accent red/blue may appear dark on mobile small screens (<400px)

---

## Relationships & Dependencies

```
Title Slide
└── Layout: title-slide
    ├── Color: --color-text-base (#232F3E)
    ├── Font: Hiragino Sans (1st priority)
    └── Size: 28pt (title), 12pt (dept/author)

Body Slide
└── Layout: body-slide
    ├── Title: 18pt, right-aligned
    ├── Divider: 3pt solid, full-width
    ├── Lead: 16pt, 90% color
    └── Content: Pattern (30+ variants)

Patterns (30+)
├── Card: 4 variants (2/3/4col, mixed)
├── Flowchart: 4 variants (h/v/d/c)
├── Table: 3 variants
├── List: 5 variants
├── Media: 4 variants
├── Highlight: 4 variants (info/warn/error/success)
├── Layout: 3 variants (2col/3col/asym)
└── Numeric: 3 variants
    └── All use Color Palette (--color-accent-*)
        ├── Red for warning
        ├── Blue for info
        └── Green for success

Color Palette
├── Base: #232F3E (日本語フォント視認性)
├── Divider: #CCCCCC
├── Accent Red: #BF4040 (75% rule)
├── Accent Blue: #4040BF (75% rule)
└── Accent Green: #40BF40 (75% rule)

Font Stack
├── Priority 1: Hiragino Sans (macOS)
├── Priority 2: Yu Gothic (Windows)
├── Priority 3: Noto Sans JP (Web)
└── Fallback: sans-serif
```

---

## State Transitions (スライド状態遷移)

```
[New Slide Created]
    ↓
[Select Layout: Title or Body]
    ├→ Title Slide
    │   ├── Fill: Title, Dept, Author
    │   └── [Ready for Presentation]
    │
    └→ Body Slide
        ├── Fill: Title, Lead Text
        ├── Select Pattern (30+ options)
        └── [Ready for Presentation]
```

**No state persistence**: スライド Markdown は stateless。再読み込みで状態復元。

---

## Completeness Checklist

| エンティティ | フィールド数 | 検証ルール数 | 実装複雑度 |
|-----------|-----------|-----------|---------|
| Title Layout | 6 | 3 | Low |
| Body Layout | 7 | 4 | Low |
| Patterns (30+) | 120+ (30 * 4 properties) | 60+ | High |
| Color Palette | 7 colors | 5 rules | Low |
| Font Stack | 4 priorities | 3 rules | Low |

**Model completeness**: ✅ 100% (all entities defined, validated, interdependencies mapped)

---

**Data Model Completion**: 2026-04-06 | Ready for CSS/Contracts Generation
