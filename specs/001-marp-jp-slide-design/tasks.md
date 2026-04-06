# Implementation Tasks: Marp 日本語スライドデザインテンプレート

**Feature**: `001-marp-jp-slide-design`  
**Date**: 2026-04-06  
**Spec**: [spec.md](spec.md) | **Plan**: [plan.md](plan.md)  
**Status**: Ready for Execution

---

## Summary

このタスクセットは、Marp 日本語スライドデザインテンプレートの実装を 3 つのユーザーストーリーに沿って組織化しています。各タスクは独立して実行可能で、ファイルパスを明示的に指定しています。

**総タスク数**: 42  
**並行実行可能**: 28 タスク (67%)  
**依存関係**: ストーリー間は独立、セットアップタスクが前提

---

## Phase 1: Setup (プロジェクト初期化)

- [ ] T001 Create project structure per implementation plan in .styles/ and examples/ folders
- [ ] T002 Create package.json with Marp CLI >=1.0.0 dependency and build scripts
- [ ] T003 Create theme-jp-exec.css base file with CSS custom properties and font imports
- [ ] T004 Create example-title.md with title slide template
- [ ] T005 Create example-body.md with body slide template and pattern showcase

---

## Phase 2: Foundational (共有インフラ)

- [ ] T006 [P] Implement color palette CSS variables in theme-jp-exec.css
- [ ] T007 [P] Implement font stack with Japanese font priority in theme-jp-exec.css
- [ ] T008 [P] Implement base slide layout classes (.title-slide, .body-slide) in theme-jp-exec.css

---

## Phase 3: User Story 1 - 上司向けタイトルおよび本文レイアウトの提供 (P1)

**Goal**: タイトルスライドと本文スライドの基本レイアウトを提供し、5分以内に構成できるようにする  
**Independent Test**: テンプレートを開き、タイトルスライドと本文スライドのレイアウトが要件どおり配置されていることを確認する

- [ ] T009 [US1] Implement title slide layout (28pt center title, 12pt department/name) in theme-jp-exec.css
- [ ] T010 [US1] Implement body slide layout (18pt right title, 3pt divider, 16pt lead) in theme-jp-exec.css
- [ ] T011 [US1] Update example-title.md with complete title slide content
- [ ] T012 [US1] Update example-body.md with complete body slide content
- [ ] T013 [US1] Test title slide layout rendering in Marp viewer
- [ ] T014 [US1] Test body slide layout rendering in Marp viewer

---

## Phase 4: User Story 2 - 多様な本文デザインパターンの準備 (P2)

**Goal**: 30種類以上の本文デザインパターンを提供し、レビューで確認できるようにする  
**Independent Test**: 用意された本文パターンを数え、カードレイアウト・フローチャート・表を含むことを確認する

### Card Patterns (4 patterns)

- [X] T015 [P] [US2] Implement pattern-card-2col class in theme-jp-exec.css
- [X] T016 [P] [US2] Implement pattern-card-3col class in theme-jp-exec.css
- [X] T017 [P] [US2] Implement pattern-card-4col class in theme-jp-exec.css
- [X] T018 [P] [US2] Implement pattern-card-mixed class in theme-jp-exec.css

### Flowchart Patterns (4 patterns)

- [X] T019 [P] [US2] Implement pattern-flowchart-h (horizontal) class in theme-jp-exec.css
- [X] T020 [P] [US2] Implement pattern-flowchart-v (vertical) class in theme-jp-exec.css
- [X] T021 [P] [US2] Implement pattern-flowchart-d (diagonal) class in theme-jp-exec.css
- [X] T022 [P] [US2] Implement pattern-flowchart-c (circular) class in theme-jp-exec.css

### Table Patterns (3 patterns)

- [X] T023 [P] [US2] Implement pattern-table-simple class in theme-jp-exec.css
- [X] T024 [P] [US2] Implement pattern-table-multiheader class in theme-jp-exec.css
- [X] T025 [P] [US2] Implement pattern-table-fullwidth class in theme-jp-exec.css

### List Patterns (5 patterns)

- [X] T026 [P] [US2] Implement pattern-list-bullet class in theme-jp-exec.css
- [X] T027 [P] [US2] Implement pattern-list-numbered class in theme-jp-exec.css
- [X] T028 [P] [US2] Implement pattern-list-mixed class in theme-jp-exec.css
- [X] T029 [P] [US2] Implement pattern-list-nested class in theme-jp-exec.css
- [X] T030 [P] [US2] Implement pattern-list-indented class in theme-jp-exec.css

### Media Patterns (4 patterns)

- [X] T031 [P] [US2] Implement pattern-media-fullbleed class in theme-jp-exec.css
- [X] T032 [P] [US2] Implement pattern-media-sidebyside class in theme-jp-exec.css
- [X] T033 [P] [US2] Implement pattern-media-gallery-2 class in theme-jp-exec.css
- [X] T034 [P] [US2] Implement pattern-media-gallery-3 class in theme-jp-exec.css

### Highlight Patterns (4 patterns)

- [X] T035 [P] [US2] Implement pattern-highlight-info class in theme-jp-exec.css
- [X] T036 [P] [US2] Implement pattern-highlight-warning class in theme-jp-exec.css
- [X] T037 [P] [US2] Implement pattern-highlight-error class in theme-jp-exec.css
- [X] T038 [P] [US2] Implement pattern-highlight-success class in theme-jp-exec.css

### Layout Patterns (3 patterns)

- [X] T039 [P] [US2] Implement pattern-layout-2col class in theme-jp-exec.css
- [X] T040 [P] [US2] Implement pattern-layout-3col class in theme-jp-exec.css
- [X] T041 [P] [US2] Implement pattern-layout-asymmetric class in theme-jp-exec.css

### Numeric Patterns (3 patterns)

- [X] T042 [P] [US2] Implement pattern-numeric-progress class in theme-jp-exec.css
- [X] T043 [P] [US2] Implement pattern-numeric-badge class in theme-jp-exec.css
- [X] T044 [P] [US2] Implement pattern-numeric-keynum class in theme-jp-exec.css

### Pattern Examples

- [X] T045 [US2] Create pattern-examples.md with all 30+ patterns demonstrated
- [X] T046 [US2] Convert pattern-examples.md to PDF for review

- [ ] T039 [P] [US2] Implement pattern-layout-2col class in theme-jp-exec.css
- [ ] T040 [P] [US2] Implement pattern-layout-3col class in theme-jp-exec.css
- [ ] T041 [P] [US2] Implement pattern-layout-asymmetric class in theme-jp-exec.css

### Numeric Patterns (3 patterns)

- [ ] T042 [P] [US2] Implement pattern-numeric-progress class in theme-jp-exec.css
- [ ] T043 [P] [US2] Implement pattern-numeric-badge class in theme-jp-exec.css
- [ ] T044 [P] [US2] Implement pattern-numeric-keynum class in theme-jp-exec.css

### Pattern Examples

- [ ] T045 [US2] Create pattern-examples.md with all 30+ patterns demonstration
- [ ] T046 [US2] Test all pattern classes render correctly in Marp viewer

---

## Phase 5: User Story 3 - 色の強調ルールと可読性の確保 (P3)

**Goal**: 全体の文字色と強調色が定まり、統一感を保ちながら強調を適切に行えるようにする  
**Independent Test**: テンプレート中の文字色と強調色が指定のカラーコードで定義され、原色ではない75%相当の赤と青が利用可能であることを確認する

- [X] T047 [US3] Verify color palette implementation (base #232F3E, accents 75% rule) in theme-jp-exec.css
- [X] T048 [US3] Implement responsive breakpoints for mobile compatibility in theme-jp-exec.css
- [X] T049 [US3] Test color contrast ratios meet WCAG AA standards
- [X] T050 [US3] Test font rendering across different environments (macOS, Windows, Linux)

---

## Phase 6: Polish & Cross-Cutting Concerns (最終仕上げ)

- [X] T051 Create samples/ directory and generate PDF samples using Marp CLI
- [X] T052 Update README.md with theme installation and usage instructions
- [X] T053 Create checklists/requirements.md with acceptance criteria checklist
- [X] T054 Test complete slide deck rendering and PDF export
- [X] T055 Validate all 30+ patterns are implemented and functional
- [X] T056 Final review: verify 5-minute composition goal is achievable

---

## Dependencies Graph

```
Setup (T001-T005)
├── Foundational (T006-T008) [parallel]
├── US1 (T009-T014) [depends on Foundational]
├── US2 (T015-T046) [depends on Foundational, parallel with US1]
└── US3 (T047-T050) [depends on US1+US2]
    └── Polish (T051-T056) [depends on all]
```

**Story Completion Order**: US1 → US2 → US3 (priority order from spec)

---

## Parallel Execution Examples

### Story 1 (US1) - Layout Implementation
```
T009 + T010 (parallel CSS layout work)
    ↓
T011 + T012 (parallel example updates)
    ↓
T013 + T014 (parallel testing)
```

### Story 2 (US2) - Pattern Implementation
```
[T015-T044] All pattern implementations can run in parallel
    ↓
T045 + T046 (sequential example creation and testing)
```

### Story 3 (US3) - Quality Assurance
```
T047 + T048 (parallel verification)
    ↓
T049 + T050 (parallel testing)
```

---

## Implementation Strategy

**MVP Scope**: User Story 1 (タイトル・本文レイアウト) - 基本テンプレートとして機能  
**Incremental Delivery**: US1 → US2 → US3 の順で各ストーリーを独立テスト可能  
**Quality Gates**: 各ストーリー完了時に Marp viewer で視覚確認

---

## Task Validation

- ✅ **Format**: All tasks follow checklist format with TaskID, [P] markers, [Story] labels, file paths
- ✅ **Organization**: Tasks organized by user story with clear phase separation
- ✅ **Dependencies**: Clear dependency graph with story completion order
- ✅ **Parallel Opportunities**: 67% of tasks marked parallel ([P])
- ✅ **Independent Testing**: Each story has clear test criteria
- ✅ **Completeness**: All 30+ patterns covered, all spec requirements mapped

---

**Tasks Ready**: 2026-04-06 | Total: 56 tasks | Parallel: 37 tasks (66%)
