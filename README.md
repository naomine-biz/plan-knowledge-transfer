# plan-knowledge-transfer

テーマと想定読者から、読者をLv5またはLv6の理解へ導く知識移転計画を完成させるスキルです。
計画は、執筆時に説明する内容と順序を選び、校正時に目的に必要な理解・論理・条件が保たれているか確認する基準になります。

## 担当すること

- テーマ、執筆目的、想定読者、前提知識、説明が答える問いの整理
- Lv5のシステム理解、またはLv6の戦略的判断という到達目標の選択
- 到達目標と、読者が獲得すべき理解・前提・つながりを含む計画の作成
- 執筆目的に必要な理解がそろっているかの点検
- 目標レベルと前提知識を設定した読者ペルソナによる、計画の不足と分解の止めどころの点検
- Humanによる計画の承認
- 完成した計画、根拠の確認状況、未解決事項の提示

このスキルの成果物は計画です。本文の作成、原稿のレビュー・校正、制作工程の設計は担当しません。

## プランの完成条件

完成したプランでは、執筆目的に必要な理解と、その前提・つながりがそろっています。
対象分野を網羅することや、本文を長くすることを完成条件にはしません。

各項目には、読者がその説明を読むことで理解すべき具体的な因果、関係、条件、区別や判断を書きます。複数の関係を含む項目は子項目へ分け、到達目標へどうつながるかを確認します。
具体的な本文、例の筋書き、見出し、図表の仕様や配置は、計画に含めません。

分解の止めどころを確かめるため、読者ペルソナの応答も使います。既知の内容から到達目標へ進む経路と、必要な理解の不足を確認し、計画と根拠へ照合します。

## 世界知識と検索の使い分け

モデルの世界知識と依頼の文脈から、必要な概念・因果・成立条件を組み立てることを基本にします。理解のつながりを点検し、前提の抜けや曖昧さを具体化します。
題材自体が未知で全体像を組み立てられない場合は、提供資料や原典で調べ、得られた題材理解をHumanに確認してもらってから計画を作ります。この確認は、完成した計画の承認と分けて記録します。
検索・資料確認は、重要な成立条件、不確かな因果、具体的な仕様・数値・最新情報などを確認するために使います。確認の要否は、誤りが到達目標に与える影響で判断します。
世界知識からの整理、与えられた前提、原典で確認した事実、未確認事項を区別して計画に残します。手順の詳細は[計画の作り方](references/knowledge-transfer-plan.md#世界知識で構造を作り必要な事実を確認する)に記載しています。

## Codexへのインストール

### skill-installerを使う

Codexに次のように依頼します。

```text
$skill-installer を使って、
https://github.com/naomine-biz/plan-knowledge-transfer
のスキルをインストールしてください。
スキルはリポジトリ直下にあります。
パスは .、インストール名は plan-knowledge-transfer と指定してください。
```

### 手動で導入する

ユーザー共通のスキルとして使う場合は、次のコマンドで取得します。

```sh
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/naomine-biz/plan-knowledge-transfer.git \
  "$HOME/.agents/skills/plan-knowledge-transfer"
```

Codexは新しく導入したスキルを自動で検出します。表示されない場合はCodexを再起動してください。
導入方法と配置先は、[OpenAIのAgent Skillsドキュメント](https://developers.openai.com/codex/skills/)で確認できます。

Codexのプラグイン一覧から導入する形で配布する場合は、[プラグインとしてのパッケージ化](https://developers.openai.com/codex/plugins/build/)が必要です。
このリポジトリは単独スキルとしてインストールできます。

## 使い方

[SKILL.md](SKILL.md)を読み込み、テーマと想定読者を指定します。
たとえば、次のように依頼します。

```text
$plan-knowledge-transfer を使い、テーマ・想定読者・執筆目的から、
読者が獲得すべき理解を分解した計画を作ってください。
```

技術リーダーやアーキテクトにはLv5、CxOや部門長など組織の意思決定を担う立場にはLv6を目標にします。
目標が不明な場合はHumanに確認します。
到達目標と理解の項目を含む計画を提示し、Humanの承認を得て、完成した計画を成果物として終了します。
承認待ち、修正中、承認済みの状態を区別します。

## 思考モデルと説明の順序

各段階で参照する概念名と、計画での使い方は[thinking-levels.md](references/thinking-levels.md)に記載しています。
スキル側には、世界知識から意味を特定するための概念名・著者名を置き、出典リンクと借用・再解釈の説明は、このREADMEにまとめています。

計画の順序はLv2から始めます。論理のつながり、条件を変えたときの成立範囲、実例・実データが裏付ける範囲と前提を、理解の項目として具体化します。
Lv5では、それらをシステム全体の理解へ結び付けます。Lv6を目標にする場合は、組織の選択、実行、見直しの判断に必要な理解まで計画します。

### 7段階の枠組みの出典

この7段階は、深淵回廊の以下の資料を参考に、技術的な知識移転の設計用に整理したものです。

- 直接参考にした資料：[「【思考心理学】本当に頭が良い人は何を考えているのか?」](https://www.youtube.com/watch?v=4cCFqBsXZ2E)（YouTube）
- 提案者による補足説明：[「【思考心理学】思考力の7段階〜完全版〜」](https://note.com/shinen_kairo/n/nb7db02119df5)（note）

7段階という配置は、提案者が心理学・認知科学の概念を整理した独自のモデルです。学術的に検証された単一の能力尺度としては扱いません。

### 各段階で参照する概念と文献

以下は、各概念の意味を特定するための出典・参考文献です。これらの著者が、このスキルの7段階の配置や知識移転の手順を提唱したという位置づけではありません。

| 段階 | 概念 | 出典・参考文献 |
|---|---|---|
| Lv0 | 自動的処理・System 1 | Daniel Kahneman『[Thinking, Fast and Slow](https://us.macmillan.com/books/9780374533557/thinkingfastandslow/)』（2011）。自動的・直感的な処理の参照先。 |
| Lv1 | 基本的気づき・表面的パターン認識 | 元動画のBasic Awareness / Surface Pattern Recognitionという呼称。独立した理論や特定の著者への対応付けはしていません。 |
| Lv2 | ロジカルシンキング・論理的推論 | 元動画の表記はFormal Reasoning。推論研究の参考文献として、Philip N. Johnson-Laird「[Mental models and human reasoning](https://www.pnas.org/doi/full/10.1073/pnas.1012933107)」（2010）。 |
| Lv3 | クリティカルシンキング | Peter A. Facione『[Critical Thinking: A Statement of Expert Consensus for Purposes of Educational Assessment and Instruction](https://eric.ed.gov/fulltext/ed315423.pdf)』（1990、Delphi Report）。 |
| Lv4 | メタ認知 | John H. Flavell「[Metacognition and Cognitive Monitoring](https://jwilson.coe.uga.edu/EMAT7050/Students/Wilson/Flavell%20(1979).pdf)」（1979）。 |
| Lv5 | システム思考 | Peter M. Senge『[The Fifth Discipline](https://www.penguinrandomhouse.com/books/163984/the-fifth-discipline-by-peter-m-senge/)』。元動画でも参照されています。 |
| Lv6 | 戦略的思考 | Jeanne M. Liedtka「[Strategic Thinking: Can It Be Taught?](https://doi.org/10.1016/S0024-6301(97)00098-8)」（1998、Long Range Planning 31(1), 120–129）。このスキルで追加した参照先です。 |

### このスキルで借用・再解釈したこと

- 段階番号を、元動画のLevel1〜Level7からLv0〜Lv6へ変更しました。定義の表現も、知識移転を計画する用途に合わせて整理しています。
- Lv0の「思考しない」は、自動的な処理や反応を指す表現として使っています。System 1も認知の働きであり、認知そのものが存在しないという意味にはしていません。
- Lv4では、メタ認知を、自分が置いた前提・判断・事例選択を点検する役割として使います。実例や実データは、その点検に使う手段として計画します。
- **Lv6は、元動画の「実行機能と長期的計画」から「戦略的思考」へ変更しました。** 実行機能は、このスキルを使う計画担当が工程全体で担う働きと位置づけています。実行機能の概念はAdele Diamond「[Executive Functions](https://pmc.ncbi.nlm.nih.gov/articles/PMC4084861/)」（2013）を参照しています。
- このスキルでのLv5とLv6の関係は、システムの動きを理解し、その理解に目的・制約・時間軸・選択を加えて戦略を考える関係です。同じシステム理解からでも、目標や制約に応じた複数の選択を考えられることを、Lv6の到達目標に含めています。
- Lv2から目標まで理解を積み上げる計画、Lv5のシステム理解またはLv6の組織の戦略的判断を目的とする方針は、本スキルで具体化したものです。

### 雨の例の出典

分解を止める粒度の例で使う、冷却・凝結と水循環の関係は、NASA「[The Water Cycle](https://gpm.nasa.gov/education/water-cycle)」を参照しています。

## ファイル構成

| ファイル | 内容 |
|---|---|
| [SKILL.md](SKILL.md) | 計画の用途、入力、成果物、設計手順と作業範囲 |
| [thinking-levels.md](references/thinking-levels.md) | 7段階の定義、目標の選び方、説明の順序 |
| [knowledge-transfer-plan.md](references/knowledge-transfer-plan.md) | 理解の分解と粒度、目的の充足、根拠、計画の完成とHumanの承認 |
| [review-checklist.md](references/review-checklist.md) | 計画の完成条件と不足の点検 |
| [reader-review.md](references/reader-review.md) | 読者ペルソナによる計画の点検と、分解を止める判断 |
| [openai.yaml](agents/openai.yaml) | スキル表示と呼び出し用のメタデータ |
