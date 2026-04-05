---
marp: true
theme: theme
lang: ja
size: 1280px 720px
paginate: true
---

<!-- markdownlint-disable MD033 -->
<!-- markdownlint-disable MD025 -->

<!-- _class: title -->
<!-- paginate: skip -->
# Marp デザインパターン完全ガイド

スライド作成用CSSの実装例

---
<!-- paginate: true -->
# 基本的なページ構成

<div class="lead">
タイトル・リード文・オブジェクト配置の3要素で、わかりやすいスライドが完成します。
</div>

このスライドでは、Cone-c-slideで紹介されている39のデザインパターンをMarp環境で実装した方法を解説します。

---

# 【1】要素間の関係が存在するパターン

<div class="lead">
情報を構成する要素間に対立や比較、並列などの関係がある場合に用います
</div>

---

# 横並び（3列）

## 各要素に入れ込むテキスト量が少ない場合に用います

<div class="horizontal-layout">

  <div class="card">
    <span class="card-icon">📱</span>
    <div class="card-title">高速</div>
    <div class="card-description">最新の技術で業務効率を大幅に向上させます</div>
  </div>

  <div class="card">
    <span class="card-icon">🔒</span>
    <div class="card-title">セキュア</div>
    <div class="card-description">エンタープライズグレードのセキュリティ</div>
  </div>

  <div class="card">
    <span class="card-icon">⚙️</span>
    <div class="card-title">カスタマイズ可能</div>
    <div class="card-description">ニーズに合わせた柔軟な設定が可能</div>
  </div>
  
</div>

---

# 横並び（2列）

<div class="lead">
2つの要素を比較する場合に効果的です
</div>

<div class="horizontal-layout two-column">
  <div class="card">
    <span class="card-icon">❌</span>
    <div class="card-title">従来の方法</div>
    <div class="card-description">時間がかかり、コストも高い</div>
  </div>
  <div class="card">
    <span class="card-icon">✅</span>
    <div class="card-title">新しい方法</div>
    <div class="card-description">効率的でコスト削減が可能</div>
  </div>
</div>

---

# 縦並び

<div class="lead">
テキスト量が多い場合は、縦並びで配置するときれいなデザインになります
</div>

<div class="vertical-layout">
  <div class="vertical-item">
    <div class="vertical-item-title">📊 データ分析</div>
    <div class="vertical-item-text">
      リアルタイムのデータ分析により、ビジネスインテリジェンスを可視化します。経営判断に必要な情報を瞬時に得ることができます。
    </div>
  </div>
  <div class="vertical-item">
    <div class="vertical-item-title">🚀 高速導入</div>
    <div class="vertical-item-text">
      わずか30日でシステムを導入可能。既存システムとの統合も簡単で、運用チームの負担を最小限に抑えます。
    </div>
  </div>
  <div class="vertical-item">
    <div class="vertical-item-title">🌍 グローバル対応</div>
    <div class="vertical-item-text">
      50カ国以上で利用されており、多言語・多通貨に対応しています。世界中のチームでシームレスに協働できます。
    </div>
  </div>
</div>

---

# 複数羅列

<div class="lead">
4つ以上の情報を並べたい場合は、「伝えたいものを大きくする」ことを意識しましょう
</div>

<div class="multiple-grid">
  <div class="grid-item">
    <div class="grid-item-number">500+</div>
    <div class="grid-item-label">導入企業</div>
  </div>
  <div class="grid-item">
    <div class="grid-item-number">98%</div>
    <div class="grid-item-label">満足度</div>
  </div>
  <div class="grid-item">
    <div class="grid-item-number">24/7</div>
    <div class="grid-item-label">サポート</div>
  </div>
  <div class="grid-item">
    <div class="grid-item-number">50+</div>
    <div class="grid-item-label">機能</div>
  </div>
</div>

---

# 規模比較

<div class="lead">
市場や数字の大きさの違いを視覚的に表現します
</div>

<div class="scale-comparison">
  <div class="scale-item">
    <div class="scale-bar" style="height: 60px;"></div>
    <div class="scale-label">
      <strong>100</strong><br>
      <small>2020年</small>
    </div>
  </div>
  <div class="scale-item">
    <div class="scale-bar" style="height: 120px;"></div>
    <div class="scale-label">
      <strong>220</strong><br>
      <small>2022年</small>
    </div>
  </div>
  <div class="scale-item">
    <div class="scale-bar" style="height: 180px;"></div>
    <div class="scale-label">
      <strong>350</strong><br>
      <small>2024年</small>
    </div>
  </div>
</div>

---

# 比較テーブル

<div class="lead">
比較する項目が多い場合は表を用いるとわかりやすくなります
</div>

| 機能 | 基本プラン | ビジネスプラン | エンタープライズ |
|------|----------|---------------|-----------------|
| ユーザー数 | 5名まで | 50名まで | 無制限 |
| ストレージ | 100GB | 1TB | 無制限 |
| サポート | メール | 優先対応 | 専任担当 |
| API | ✓ | ✓ | ✓ |
| カスタマイズ | - | ✓ | ✓ |

---

# 横型フロー

<div class="lead">
情報量が少ない場合は、アイコンを用いるとわかりやすくなります
</div>

<div class="flow-horizontal">
  <div class="flow-step">
    <div class="flow-step-number">1</div>
    <div class="flow-step-title">申し込み</div>
    <div class="flow-step-description">30秒で完了</div>
  </div>
  <div class="flow-step">
    <div class="flow-step-number">2</div>
    <div class="flow-step-title">設定</div>
    <div class="flow-step-description">自動で構成</div>
  </div>
  <div class="flow-step">
    <div class="flow-step-number">3</div>
    <div class="flow-step-title">運用開始</div>
    <div class="flow-step-description">その日から利用可能</div>
  </div>
</div>

---

# 縦型フロー

<div class="lead">
項目が多い場合は縦型のフローにします
</div>

<div class="flow-vertical">
  <div class="flow-step">
    <div class="flow-step-number">1</div>
    <div class="flow-step-title">要件定義</div>
    <div class="flow-step-description">ビジネス要件を詳しくヒアリング</div>
  </div>
  <div class="flow-step">
    <div class="flow-step-number">2</div>
    <div class="flow-step-title">カスタマイズ</div>
    <div class="flow-step-description">要件に合わせてシステム設定</div>
  </div>
  <div class="flow-step">
    <div class="flow-step-number">3</div>
    <div class="flow-step-title">テスト実行</div>
    <div class="flow-step-description">品質保証チームによる検証</div>
  </div>
  <div class="flow-step">
    <div class="flow-step-number">4</div>
    <div class="flow-step-title">本番運用</div>
    <div class="flow-step-description">24時間サポート体制で開始</div>
  </div>
</div>

---

# マトリクス図

<div class="lead">
4象限を用いてポジショニングを説明します
</div>

<div class="matrix">
  <div class="matrix-quadrant">
    <div class="matrix-label">Low Cost / Quick</div>
    <div class="matrix-title">フレームワーク</div>
    <div class="matrix-description">既成の枠組みで素早く導入</div>
  </div>
  <div class="matrix-quadrant">
    <div class="matrix-label">High Cost / Quick</div>
    <div class="matrix-title">SaaS</div>
    <div class="matrix-description">クラウドで即座に運用開始</div>
  </div>
  <div class="matrix-quadrant">
    <div class="matrix-label">Low Cost / Slow</div>
    <div class="matrix-title">Open Source</div>
    <div class="matrix-description">自由度は高い、構築に時間</div>
  </div>
  <div class="matrix-quadrant">
    <div class="matrix-label">High Cost / Slow</div>
    <div class="matrix-title">フルスクラッチ</div>
    <div class="matrix-description">完全カスタムで最適化</div>
  </div>
</div>

---

# ベン図

<div class="lead">
要素が重なっていることを表現します
</div>

<div class="venn-diagram">
  <div class="venn-circle left">
    プロダクト<br>A
  </div>
  <div class="venn-circle right">
    プロダクト<br>B
  </div>
  <div class="venn-center">
    相乗<br>効果
  </div>
</div>

---

# ピラミッド図

<div class="lead">
上位に向かうにつれて規模が小さくなる場合に用います
</div>

<div class="pyramid">
  <div class="pyramid-level level-1">戦略レベル - 全体方針</div>
  <div class="pyramid-level level-2">計画レベル - 実行計画</div>
  <div class="pyramid-level level-3">実装レベル - 具体的施策</div>
  <div class="pyramid-level level-4">評価 - KPI測定</div>
</div>

---

# 【2】要素間の関係が存在しないパターン

<div class="lead">
グラフや事例紹介など、ある程度デザインが決まっている場合に用います
</div>

---

# テキストのみ

<div class="text-only">
  <div class="text-only-title">デジタル変革への道</div>
  <div class="text-only-content">
    現代のビジネス環境では、デジタル化は必須要件となっています。組織内の業務プロセスを見直し、テクノロジーを活用することで、競争力の強化と顧客満足度の向上を同時に実現することができます。
  </div>
  <div class="text-only-content">
    ただし重要なのは、テクノロジーは手段であり、目的ではないということです。ビジネスゴールを明確にした上で、それを実現するためのテクノロジーを選択する必要があります。
  </div>
</div>

---

# 引用・メッセージ

<div class="lead">
代表メッセージや企業理念を伝えます
</div>

<blockquote>
  「イノベーションとは、顧客の未充足ニーズを発見し、それに対する独創的なソリューションを提供することである。」
</blockquote>

<div style="text-align: right; margin-top: 40px;">
  <strong>代表取締役 田中太郎</strong>
</div>

---

# 【3】ページ項目に応じて決まっているパターン

<div class="lead">
表紙や目次、会社概要など入れ込む情報が決まっている場合に用います
</div>

---

# 会社概要

<div class="company-info">
  <div class="company-logo">🏢</div>
  <div class="company-details">
    <div class="info-item">
      <div class="info-label">会社名</div>
      <div class="info-value">株式会社イノベーション</div>
    </div>
    <div class="info-item">
      <div class="info-label">設立</div>
      <div class="info-value">2015年4月</div>
    </div>
    <div class="info-item">
      <div class="info-label">事業内容</div>
      <div class="info-value">デジタルソリューション開発</div>
    </div>
    <div class="info-item">
      <div class="info-label">従業員数</div>
      <div class="info-value">250名</div>
    </div>
  </div>
</div>

---

## メンバー紹介

<div class="member-grid">
  <div class="member-card">
    <div class="member-avatar">👨</div>
    <div class="member-name">山田太郎</div>
    <div class="member-title">代表取締役</div>
    <div class="member-bio">MIT卒業後、Silicon ValleyでIT企業を起業。現在はアジア拡大を推進中。</div>
  </div>
  <div class="member-card">
    <div class="member-avatar">👩</div>
    <div class="member-name">佐藤花子</div>
    <div class="member-title">CTO</div>
    <div class="member-bio">東大工学部出身。AI・機械学習の専門家。複数の特許を保有。</div>
  </div>
  <div class="member-card">
    <div class="member-avatar">👨</div>
    <div class="member-name">鈴木次郎</div>
    <div class="member-title">営業責任者</div>
    <div class="member-bio">前職の大手IT企業で営業成績No.1。500社以上のクライアント開拓実績。</div>
  </div>
</div>

---

## ユーティリティクラスの活用

<div class="lead">
CSSクラスを組み合わせて柔軟にデザインを調整します
</div>

<div class="bg-light" style="padding: 30px; border-radius: 8px;">
  <div class="text-center color-primary font-bold text-large mb-medium">
    重要なメッセージ
  </div>
  <div style="font-size: 16px; line-height: 1.8;">
    <p class="mt-small">`.color-primary` - 強調色を適用</p>
    <p class="mt-small">`.font-bold` - テキストを太字に</p>
    <p class="mt-small">`.text-large` - フォントサイズを大きく</p>
    <p class="mt-small">`.bg-light` - 背景色を薄く</p>
  </div>
</div>

---

<!-- _class: title -->
## まとめ

CSSパターンを組み合わせることで、プロフェッショナルなスライドが効率的に作成できます。

---

# 使用方法

Marpファイルのフロントマッターで以下を記述してください：

```yaml
---
marp: true
theme: ./theme.css
lang: ja
size: 16:9
paginate: true
footer: "© Your Company"
---
```

その後、HTMLやMarkdownのクラス属性でCSSを適用します：

```html
<div class="horizontal-layout">
  <div class="card">コンテンツ</div>
</div>
```

---

# カスタマイズ例

CSS変数を編集することで、色やフォントを一括変更できます：

```css
:root {
  --color-primary: #2c3e50;    /* 主色 */
  --color-secondary: #3498db;  /* 副色 */
  --color-accent: #e74c3c;     /* アクセント色 */
  --font-title: 'メイリオ';    /* タイトルフォント */
  --font-body: 'メイリオ';     /* 本文フォント */
}
```

---

# トラブルシューティング

## よくある質問

**Q: フォント が反映されない**  
A: `theme.css`のフォント設定を確認し、システムにインストール済みのフォントを指定してください。

**Q: 色が思った通りに表示されない**  
A: CSSの色変数 (--color-*) を編集して、全体の色をカスタマイズしてください。

**Q: レイアウトが崩れた**  
A: 画面幅に応じたメディアクエリが適用されています。ブラウザのズームを確認してください。

---

# 参考資料

このスライドテーマは、以下の記事をベースに作成されました：

**[パワーポイントのデザインパターン集](https://cone-c-slide.com/see-sla/blog/design-pattern/)**

- 要素間の関係が存在するパターン（並列・比較・フローなど）
- 要素間の関係が存在しないパターン（グラフ・表・キャプチャなど）
- ページ項目に応じて決まっているパターン（表紙・目次・会社概要など）
