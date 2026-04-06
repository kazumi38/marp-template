# Implementation Plan: Marp 日本語スライドデザインテンプレート

**Branch**: `001-marp-jp-slide-design` | **Date**: 2026-04-06 | **Spec**: [spec.md](spec.md)
**Input**: Feature specification from `/specs/001-marp-jp-slide-design/spec.md`

**Note**: This plan is derived from a fully clarified feature specification with 5 confirmed design decisions. See `spec.md` for clarifications log.

## Summary

テンプレートは Marp ネイティブのテーマ CSS として実装され、タイトルスライド・本文スライド 2 つのレイアウトと 30 種類以上の本文デザインパターンを CSS クラスで提供します。ユーザーは Markdown で `theme:` 指定とクラス記法で使用。成果物は CSS ソース（メンテナンス用）と PDF サンプル集（ビジュアル検査用）の複合形式で納品。

## Technical Context

**Language/Version**: CSS3 + Markdown (Marp CLI v0.x 系 対応)  
**Primary Dependencies**: Marp CLI (テーマ CSS エンジン), Node.js (ビルド・PDF 生成用)  
**Storage**: ファイルベース（GitHub リポジトリ内 CSS + example Markdown）  
**Testing**: Visual regression testing (PDF 出力による視覚比較), 手作業レビュー  
**Target Platform**: Web browser (Marp viewer), PDF generation (Chromium via Marp)  
**Project Type**: Design template/Theme (オープンソース形式での配布)  
**Performance Goals**: 1 スライドの PDF 生成 <2 秒  
**Constraints**: Marp CSS 文法の互換性、日本語フォント環境依存性の最小化（複数フォント指定で対応）  
**Scale/Scope**: 30+ design patterns, 2 core layouts (title, body), color palette (base + 2 accent), font stack 4 levels

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

**No constitution file detected** — デフォルト設定で進行。質的要件の優先順位：視認性 > 再利用性 > 拡張性

## Project Structure

### Documentation (this feature)

```text
specs/001-marp-jp-slide-design/
├── plan.md                      # This file (speckit.plan output)
├── spec.md                      # Feature specification with clarifications
├── research.md                  # Phase 0 output (TBD)
├── data-model.md                # Phase 1 output (TBD)
├── quickstart.md                # Phase 1 output (TBD)
├── tasks.md                     # Phase 2 output (speckit.tasks command)
└── checklists/
    └── requirements.md          # Test & acceptance checklist
```

### Source Code (repository root)

```text
.styles/
├── theme-jp-exec.css            # Main theme CSS (30+ patterns + layouts)
└── theme-jp-exec-light.css      # (Optional) Light variant

examples/
├── example-title.md             # Title slide example
├── example-body.md              # Body slide with patterns showcase
├── example-complete.md          # Full deck example (5-10 slides)

samples/
├── title-slide.pdf              # Generated: Title slide sample
├── body-patterns.pdf            # Generated: All 30 patterns showcase
└── complete-deck.pdf            # Generated: Full example deck

README.md                          # Theme usage guide & installation
package.json                       # Marp CLI version spec
```

**Structure Decision**: Single project structure（テーマファイル + サンプル + PDF 出力）。Marp テンプレートはモノリシック CSS で実装され、拡張は CSS クラス追加で対応。

## Design Decisions Summary

| 決定 | 選択内容 | 根拠 |
|-----|--------|------|
| 出力形式 | Marp テーマ CSS | ネイティブ機能活用、メンテナンス容易 |
| 日本語フォント | 優先順位付き複数指定 | 環境依存性最小化 |
| パターン実装 | CSS クラス | ユーザー記法がシンプル、可変対応可能 |
| サンプル提供 | Markdown + CSS + PDF | メンテナンスとビジュアル検査の両立 |
| バージョン管理 | package.json で明記 | サポート範囲を明示 |

## Phase 0: Research （予定）

**実行対象**:
1. Marp CSS テーマ仕様の詳細確認（クラス記法、レスポンシブ対応）
2. 日本語フォント指定のベストプラクティス（複数フォント優先順位の実装例）
3. 30 パターン実装の CSS 構造検討（クラス ≥ 30 か、見出し数で動的化か）
4. PDF 生成パイプライン（Marp CLI + 自動化ツール）

**出力**: `research.md`（各項目の決定トレーサビリティ）

---

## Phase 1: Design & Contracts （予定）

### 1.1 Data Model

**エンティティ**:
- **スライドレイアウト**
  - Title Slide: center-aligned title (28pt), department (12pt), name (12pt)
  - Body Slide: right-aligned title (18pt), 3pt divider, lead text (16pt)

- **デザインパターン** (目標 30+)
  - Card layouts: 2col, 3col, 4col variants
  - Flow charts: horizontal, vertical, connectors
  - Tables: simple, multi-header
  - Mixed content: text + images, side-by-side
  - Call-out boxes: warning, info, success, error

- **Color Palette**
  - Base text: #232F3E
  - Accent Red: 75% of #FF0000 → ~#BF4040
  - Accent Blue: 75% of #0000FF → ~#4040BF
  - Background: #FFFFFF (default)

- **Font Stack**
  - Priority 1: Hiragino Sans (macOS)
  - Priority 2: Yu Gothic (Windows)
  - Priority 3: Noto Sans JP (Web)
  - Priority 4: sans-serif (fallback)

### 1.2 Interface Contracts

**Marp Theme CSS Interface** (ユーザーが使用する範囲):

```markdown
---
theme: marp-jp-exec
lang: ja
---

# Title Slide
## Department / Team Name
### Author Name

---
<!-- class: pattern-card-3col -->

# Content Title with 3-Card Pattern
```

**CSS Class Contract** (実装):

```css
/* Base theme identifier */
@import './theme-jp-exec.css';

/* Pattern classes */
.pattern-card-2col { /* ... */ }
.pattern-card-3col { /* ... */ }
.pattern-card-4col { /* ... */ }
.pattern-flowchart-h { /* ... */ }
.pattern-flowchart-v { /* ... */ }
.pattern-table-simple { /* ... */ }
/* ... 24+ more patterns ... */

/* Layout overrides */
.title-slide { /* ... */ }
.body-slide { /* ... */ }
```

### 1.3 Agent Context Update

実行予定: `.specify/scripts/bash/update-agent-context.sh copilot`

### 1.4 Quick Start Guide

出力名: `quickstart.md`

内容:
- インストール手順（theme CSS をコピー）
- テンプレート Markdown の最小構成
- パターン使用例（5-10 個のサンプル）
- FAQ（フォント表示、パターン追加方法）

---

## Complexity Justification

No violations detected. Constitution check not required (template-only project).

---

## Next Steps

1. **Phase 0 Research** (`/speckit.plan` で実行予定)
   - Marp CSS 仕様とベストプラクティスの詳細調査
   - PDF 生成自動化の実現可能性確認

2. **Phase 1 Design** (`/speckit.plan` で実行予定)
   - `data-model.md` 生成（エンティティ詳細 + 検証ルール）
   - `contracts/` ディレクトリで CSS クラス定義書
   - `quickstart.md` 作成

3. **Phase 2 Tasks** (`/speckit.tasks` で実行）
   - タスク生成と依存性分析
   - 実装スケジュール確定

---

**Prepared**: 2026-04-06 | **Status**: Ready for Phase 0 Research Launch
