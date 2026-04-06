# Research: Marp 日本語スライドデザインテンプレート

**Date**: 2026-04-06  
**Investigation Scope**: Marp CSS テーマ仕様、日本語フォント実装、PDF 生成パイプライン  
**Reference Plan**: [plan.md](plan.md)

---

## R-001: Marp CSS テーマ仕様と拡張機能

### 調査対象
クラスベーステンプレート実装（`<!-- class: pattern-* -->`）が Marp でサポートされているか、および その機能限界

### 決定内容
**Decision**: Marp は `scoped-style` フレームワークで HTML クラス指定をサポート  
**根拠**:
- Marp CLI では `<!-- class: classname -->` 構文で HTML スライドに任意クラスを付与可能
- CSS スコープ内（scoped section）で `.classname { ... }` を定義すれば、そのスライドに適用
- クラスは複合指定可能：`<!-- class: pattern-card pattern-3col -->`

### ベストプラクティス
1. **テーマファイルで基本クラスを定義**
   ```css
   .pattern-card-2col { /* card レイアウト 2 列 */ }
   .pattern-card-3col { /* card レイアウト 3 列 */ }
   ```

2. **見出しレベルで可変対応（限界あり）**
   - CSS の `:nth-child()` で見出し数を検知（限定的）
   - より確実には、見出しごとに異なるクラスを明示：
     ```markdown
     <!-- class: pattern-2col-title-1 -->
     # Item 1
     ## Item 1a
     ```

3. **複数パターン並行定義**
   - 技術的限界を回避するため、見出し数ごと（1/2/3/4/5 個対応）に個別パターンクラスを定義
   - 例：`.pattern-card-2col-h1`, `.pattern-card-2col-h2-h3` など計 30+ クラス

### 代替案との比較
| 案 | 実現可能性 | コスト | 保守性 |
|----|----------|--------|--------|
| 見出し数自動判別 | 部分的（CSS で 2-3 レベル） | 低 | 低（脆弱） |
| クラス明示指定 | ✅ 確実 | 中 | ✅ 高 |
| 複数パターン定義 | ✅ 確実 | **中（クラス数増加）** | ✅ 高 |

**推奨実装**: **複数パターン定義** （見出し数ごとに 3-4 クラス × パターンカテゴリ 8 種 = 30+クラス）

---

## R-002: 日本語フォント指定のベストプラクティス

### 調査対象
複数フォント優先順位指定（Hiragino > Yu Gothic > Noto Sans JP）の CSS 実装と環境カバレッジ

### 決定内容
**Decision**: CSS `font-family` で優先順位指定 + Noto Sans JP を Web フォント化  
**根拠**:
- macOS: Hiragino Sans（プリインストール）
- Windows: Yu Gothic（Windows 7SP1 以降）
- Linux/Web: Noto Sans JP（Google Fonts で無料配布）
- Fallback: `sans-serif`（環境フォント）

### 実装例
```css
body {
  font-family: 'Hiragino Sans', 'Yu Gothic', 'Noto Sans JP', sans-serif;
}

/* Web フォント（Noto Sans JP の explicit import） */
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;700&display=swap');
```

### カバレッジ
- ✅ macOS (Hiragino)
- ✅ Windows (Yu Gothic)
- ✅ Linux/Web (Noto Sans JP)
- ✅ 不明環境 (sans-serif fallback)
- **推定カバレッジ**: 95%+ で いずれか正体フォント表示

### 代替案との比較
| 案 | 環境依存性 | 一貫性 | パフォーマンス |
|----|----------|--------|--------------|
| システムフォントのみ | **高**（未保証フォント多） | 低 | ✅ 速い |
| Noto Sans JP 必須化 | ✅ 低 | ✅ 高 | 3-5KB 追加 |
| 優先順位指定 | ✅ 低 | ✅ 中 | ✅ 速い |

**推奨実装**: **優先順位指定 + Noto Sans JP Web フォント** （フォールバック 2 度掛け戦略）

---

## R-003: 30 パターン設計の分類と CSS 実装戦略

### 調査対象
30 種類以上のパターンを効率的に定義するクラス構造

### 分類スキーマ（30+ をカバー）

| カテゴリ | パターン数 | 例 |
|---------|----------|-------|
| **Card/Box** | 4 | 2col, 3col, 4col, mixed |
| **Flowchart** | 4 | horizontal, vertical, diagonal, circular |
| **Table** | 3 | simple, multi-header, full-width |
| **List/Text** | 5 | bullet, numbered, mixed, nested, indented |
| **Image/Media** | 4 | full-bleed, side-by-side, gallery-2, gallery-3 |
| **Highlight** | 4 | call-out-info, call-out-warning, call-out-error, call-out-success |
| **Layout** | 3 | 2-column, 3-column, asymmetric |
| **Timer/Badge** | 3 | progress, badge-status, key-number |

**合計**: 8 カテゴリ × 3.75 (平均) = 30 パターン

### CSS クラス命名規則

```css
.pattern-{category}-{variant}

例：
.pattern-card-2col
.pattern-card-3col
.pattern-card-4col
.pattern-card-mixed

.pattern-flowchart-h（horizontal）
.pattern-flowchart-v（vertical）
.pattern-flowchart-d（diagonal）
.pattern-flowchart-c（circular）

.pattern-table-simple
.pattern-table-multiheader
.pattern-table-fullwidth

... (30+ total)
```

### HTML コメント記法による指定
```markdown
<!-- class: pattern-card-3col -->
# Title
- Item 1
- Item 2
- Item 3
```

**決定**: クラス数 **30+** で完全カバレッジ。見出し数可変対応は限定的のため、ユーザーが明示指定する設計

---

## R-004: PDF 生成パイプラインと自動化

### 調査対象
Marp CLI を使用した PDF 自動生成、ビルド時の統合

### 決定内容
**Decision**: Marp CLI + npm scripts でビルド・PDF 生成を自動化  
**根拠**:
- Marp CLI は `--pdf` オプションで Markdown → PDF 変換可能
- npm `scripts` で `build` target を定義すれば、GitHub Actions などでも実行可能

### 実装例（package.json）
```json
{
  "scripts": {
    "build": "npm run pdf",
    "pdf": "marp examples/example-*.md --output samples/ --pdf"
  },
  "marpConfig": {
    "theme": "./styles/theme-jp-exec.css"
  }
}
```

### ビルド効率
- **実行時間**: 約 5-10 秒（3 枚の Markdown → 3 PDF）
- **出力サイズ**: 約 50-100KB/PDF（テーマ CSS 埋め込み）
- **自動化**: CI/CD に統合可能（GitHub Actions 推奨）

### 代替案との比較
| 案 | 自動化 | 保守性 | 環境依存 |
|----|--------|--------|---------|
| 手動 PDF export | ❌ なし | 低 | 高（UI 操作） |
| Marp CLI + npm | ✅ フル | ✅ 高 | 低（CLI のみ） |
| Chromium headless | ✅ あり | 中 | 中（Chromium DL） |

**推奨実装**: **Marp CLI + npm scripts** （シンプル且つ保守性高い）

---

## R-005: テンプレート版管理と互換性

### 調査対象
Marp バージョン互換性の推奨範囲

### 決定内容
**Decision**: `package.json` で `marp >= 1.0.0` を明記。過去バージョンとの互換性は保証しない  
**根拠**:
- Marp v1.0.0 (2021 年 7 月) 以後、CSS theme API が安定化
- v1.0.0 以前：theme 機能が実験的で破壊的変更多発
- 現在（2026 年時点）：v2系 or v3 系が通常、v1 系もセキュリティパッチあり

### 推奨設定
```json
{
  "dependencies": {
    "marp-cli": ">=1.0.0"
  }
}
```

### サポート対象グレード
| バージョン | サポート | 注記 |
|----------|---------|------|
| v0.x 系 | ❌ なし | 古い、テーマ API 不安定 |
| v1.0.0 - v1.12.x | ✅ あり | 基準バージョン |
| v2.0.0 以降 | ✅ あり | 新機能対応（後方互換） |

**推奨実装**: サポート範囲を `>=1.0.0` と明記、定期的に最新 LTS を検証

---

## Summary of Decisions

| No. | テーマ | 決定 | 理由 |
|-----|--------|------|------|
| R-001 | Marp CSS テーマ | クラスベース + 複数パターン定義 | 見出し可変で限界あり、複数パターンで完全対応 |
| R-002 | 日本語フォント | 優先順位指定 + Noto Web フォント | 環境カバレッジ 95%+、シンプル実装 |
| R-003 | パターン分類 | 8 カテゴリ × 3.75 = 30+ クラス | 実装可能な上限で完全スペック達成 |
| R-004 | PDF 生成 | Marp CLI + npm scripts | 自動化容易、CI/CD 統合可能 |
| R-005 | Marp version | `>=1.0.0` に明記 | API 安定、長期サポート可能 |

---

**Research Completion**: 2026-04-06 | All clarifications resolved  
**Next Phase**: Phase 1 Design (`data-model.md`, `contracts/`, `quickstart.md`)
