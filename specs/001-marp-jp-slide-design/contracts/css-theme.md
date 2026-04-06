# CSS Theme Contract: Marp 日本語スライドデザインテンプレート

**Date**: 2026-04-06  
**Version**: 1.0 (draft)  
**Scope**: Marp theme CSS specification and public API

---

## Overview

This contract defines the CSS classes, selectors, and properties that the Marp theme exposes to users and build automation. It is the **interface** between the theme implementation (`theme-jp-exec.css`) and user Markdown files.

---

## 1. Theme Root Selector

**Class Name**: `.title-slide`, `.body-slide` (layout selectors)  
**HTML Structure**:
```html
<!-- Marp generates section element for each slide -->
<section class="title-slide">
  <h1>Title</h1>
  <p>Department</p>
  <p>Author</p>
</section>

<section class="body-slide">
  <h1>Title</h1>
  <div class="divider"></div>
  <p>Lead text</p>
  <div class="content"><!-- Pattern content --></div>
</section>
```

**Usage in Markdown**:
```markdown
# Title Slide
## Department
### Author

---
<!-- class: body-slide -->
# Content Title
Lead text here...

Content body
```

---

## 2. Layout Classes (レイアウト指定)

### 2.1 Title Slide

**Selector**: `.title-slide`

```css
.title-slide {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.title-slide h1 {
  font-size: 28pt;
  color: #232F3E;
  font-weight: 700;
  margin: 0 0 20px 0;
}

.title-slide p {
  font-size: 12pt;
  color: #232F3E;
  opacity: 0.75;
  margin: 5px 0;
}
```

**Hierarchy** (Marp h1/h2/h3 → elements):
```markdown
# My Title          → <h1> (28pt, centered, bold)
## Department       → <p> (12pt, opacity 0.75)
### Author Name     → <p> (12pt, opacity 0.75)
```

---

### 2.2 Body Slide

**Selector**: `.body-slide`

```css
.body-slide {
  display: grid;
  grid-template-rows: auto auto auto 1fr;
  gap: 15px;
  padding: 40px;
  height: 100%;
}

.body-slide h1 {
  font-size: 18pt;
  color: #232F3E;
  text-align: right;
  margin: 0;
  padding: 0 20px 0 0;
}

.body-slide .divider {
  width: 100%;
  height: 3pt;
  background: #232F3E;
  margin: -10px 0 10px 0;
}

.body-slide p.lead {
  font-size: 16pt;
  color: #232F3E;
  opacity: 0.9;
  line-height: 1.5;
  margin: 0;
}

.body-slide .content {
  overflow: auto;
}
```

---

## 3. Pattern Classes (デザインパターン)

**Total Patterns**: 30+ (8 categories)

### Card Patterns (4)
- `.pattern-card-2col`
- `.pattern-card-3col`
- `.pattern-card-4col`
- `.pattern-card-mixed`

### Flowchart Patterns (4)
- `.pattern-flowchart-h` (horizontal)
- `.pattern-flowchart-v` (vertical)
- `.pattern-flowchart-d` (diagonal)
- `.pattern-flowchart-c` (circular)

### Table Patterns (3)
- `.pattern-table-simple`
- `.pattern-table-multiheader`
- `.pattern-table-fullwidth`

### List Patterns (5)
- `.pattern-list-bullet`
- `.pattern-list-numbered`
- `.pattern-list-mixed`
- `.pattern-list-nested`
- `.pattern-list-indented`

### Media Patterns (4)
- `.pattern-media-fullbleed`
- `.pattern-media-sidebyside`
- `.pattern-media-gallery-2`
- `.pattern-media-gallery-3`

### Highlight Patterns (4)
- `.pattern-highlight-info`
- `.pattern-highlight-warning`
- `.pattern-highlight-error`
- `.pattern-highlight-success`

### Layout Patterns (3)
- `.pattern-layout-2col`
- `.pattern-layout-3col`
- `.pattern-layout-asymmetric`

### Numeric Patterns (3)
- `.pattern-numeric-progress`
- `.pattern-numeric-badge`
- `.pattern-numeric-keynum`

---

## 4. Color Variables

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
```

---

## 5. Font Stack

```css
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;700&display=swap');

body, h1, h2, h3, h4, h5, h6, p, ul, ol, li {
  font-family: 'Hiragino Sans', 'Yu Gothic', 'Noto Sans JP', sans-serif;
}
```

---

## 6. Version Compatibility

**Supported**: Marp CLI `>=1.0.0`

---

**CSS Contract**: Ready for Implementation | 2026-04-06
