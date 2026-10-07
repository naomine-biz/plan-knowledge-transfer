# plan-knowledge-transfer

テーマと想定読者から、読者をLv5またはLv6の理解へ導く知識移転を設計するスキルです。
到達点となる説明を先に作り、技術が必要になる問題から、論理、反例、実証を段階ごとに計画します。承認後の執筆・推敲方法も計画に含めます。

## 担当すること

- テーマ、想定読者、前提知識、説明が答える問いの整理
- Lv5のシステム理解、またはLv6の戦略的判断という到達目標の選択
- 到達点となる説明文と、各段階の論点・例・根拠・つながりを含む計画の作成
- 承認後に使う執筆・推敲スキルと、完成稿を確認する工程の設計
- Humanによる計画の承認
- 計画や実際の説明構成のレビュー

本文の執筆、日本語の推敲、図表の作成、媒体の整形には、承認された計画を渡します。
このスキルは、知識移転の設計と説明構成のレビューに単独で使えます。

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
$plan-knowledge-transfer を使って、分散トランザクションを
現場のエンジニアリーダーへ説明する知識移転計画を作ってください。
```

技術リーダーやアーキテクトにはLv5、CxOや部門長など組織の意思決定を担う立場にはLv6を目標にします。
目標が不明な場合はHumanに確認します。
到達点の説明を含む計画を提示し、承認後に本文の執筆工程へ進みます。
承認済みの計画の範囲では、節ごとに承認を取り直しません。

計画には、技術的な執筆・推敲、読みやすさの推敲、完成稿との照合を含めます。日本語原稿では、利用可能な`japanese-tech-writing`と`yomiyasu`をそれぞれの工程へ割り当てます。他の環境では利用できるスキルや方法を指定でき、このスキルだけでも計画を作れます。

## 思考モデルと説明の順序

この7段階は、[深淵回廊の動画「【思考心理学】本当に頭が良い人は何を考えているのか?」](https://www.youtube.com/watch?v=4cCFqBsXZ2E)を参考に、技術的な知識移転の設計用に整理したものです。
学術的に検証された能力尺度としては扱いません。出典と本スキルでの整理は、[モデルの出典と位置づけ](references/thinking-levels.md#モデルの出典と位置づけ)に記載しています。

| 段階 | 思考の定義 |
|---|---|
| Lv0 | 思考しない |
| Lv1 | 思考が必要であることに気づく |
| Lv2 | 論理的思考 |
| Lv3 | 批判的思考 |
| Lv4 | バイアスを認識している |
| Lv5 | システム（構造）を認識している |
| Lv6 | 戦略的である |

説明はLv2から始めます。論理を一ステップずつつなぎ、反例から成立条件を検証し、実例・実データで裏付けられる範囲と前提を点検します。
そのうえで、実現されるシステム全体を説明します。Lv6を目標にする場合は、その理解を組織の選択、実行、見直しの方針へ結び付けます。

## ファイル構成

| ファイル | 内容 |
|---|---|
| [SKILL.md](SKILL.md) | 入力、成果物、設計手順と執筆工程への受け渡し |
| [thinking-levels.md](references/thinking-levels.md) | 7段階の定義、目標の選び方、説明の順序 |
| [knowledge-transfer-plan.md](references/knowledge-transfer-plan.md) | 導入の問題設定、計画の項目、材料、承認後の制作工程、Humanの承認手順 |
| [review-checklist.md](references/review-checklist.md) | 計画と説明構成のレビュー |
| [openai.yaml](agents/openai.yaml) | スキル表示と呼び出し用のメタデータ |
