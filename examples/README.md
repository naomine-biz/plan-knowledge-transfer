# 知識移転計画から執筆する出力サンプル

`plan-knowledge-transfer`で知識移転計画を作り、承認された計画をClaude Opus 5.5へ渡して技術記事を作るサンプル集。

## テーマ

| テーマ | 読者と到達目標 | 承認済み計画 | Opus 5.5の記事 | 点検と修正 |
|---|---|---|---|---|
| NoSQLとRDBMSの使い分け戦略 | CTO、Lv6 | [計画](01-nosql-rdbms-strategy/plan.md) | [記事](01-nosql-rdbms-strategy/article-opus-5.5.md) | [指摘の採否](01-nosql-rdbms-strategy/review-resolution.md) |
| MySQL最新アップデート | エンジニアリーダー、Lv5 | [計画](02-mysql-latest-updates/plan.md) | [記事](02-mysql-latest-updates/article-opus-5.5.md) | [指摘の採否](02-mysql-latest-updates/review-resolution.md) |

MySQLの「最新」は2026-10-08に確認した状態を指す。GAの26.7系列を中心に、LTSとEarly Access、配布物に限った更新の違いを計画する。

## 作成の条件

- 計画担当：Codex。スキルはcommit `e62e437`の`plan-knowledge-transfer`。
- 計画の点検：各テーマの読者条件を設定した別の文脈の読者役。記録と、計画担当による指摘の照合・採否を各フォルダに残す。
- 計画の承認：2026-10-08にHumanが両方を承認。[承認記録](approval.md)を保存した。
- 執筆担当：Claude Opus 5.5。CLIでは`claude-opus-5-5`を指定し、実行結果のモデル名も一致した。
- 執筆時の入力：完成した計画と、下記の短い依頼文。
- 記事：Claudeの実行結果の`result`をUTF-8ファイルへそのまま保存する。計画と記事は別ファイルとする。

知識移転スキルが担当するのは、計画の完成と承認までである。Claudeへの執筆依頼は、このサンプル作成の別工程として実行する。

## 執筆用のプロンプト

```text
次の知識移転計画に沿って、想定読者向けの日本語の技術記事を書いてください。
出力は記事本文だけにしてください。
```

この依頼文、空行、各承認済み計画の全文を順に連結して`input.md`に保存し、標準入力で渡した。文章量や文体の追加指定はしていない。

CLIは`--safe-mode`、`--strict-mcp-config`、`--tools ''`、`--disable-slash-commands`を指定し、リポジトリから独立した一時ディレクトリで実行した。Claude Codeの標準システム指示と管理設定は適用される。ユーザー入力の全量は各`input.md`で確認できる。

## 実際の生成手順

1. テーマと読者から目標を定め、世界知識で全体の関係と理解の経路を組み立て、目的に影響する仕様・最新情報を公式資料へ照合した。初版を`plan-v1.md`に保存した。
2. 計画担当の会話を引き継がない読者役へ、計画・読者条件・点検手順を渡した。問い、理解の経路、不足を`reader-review-v1.md`に保存した。
3. 計画担当が指摘を計画と根拠へ照合し、必要な理解を補った。採否を`review-resolution.md`に記録した。
4. 同じ読者役へ修正版を渡し、同じ読者条件で再点検した。渡した版を`plan-v2-reviewed.md`、応答を`reader-review-v2.md`に保存した。計画担当が残る注記を照合し、分解を止める理由と完成条件を`plan.md`に記録した。
5. 要約と詳細をHumanへ提示し、両方の承認を得た。`plan.md`の承認状態を更新し、計画スキルのタスクを終了した。
6. 別工程で二行の依頼文と承認済み計画をOpus 5.5へ渡した。各テーマを新しいセッションで1回ずつ生成し、返された記事を編集せずに保存した。
7. 実行モデル、入力と出力のハッシュ、CLIの終了状態を確認し、実際の工程を[READMEと照合](workflow-consistency.md)した。

最初の読者役は計画担当と別の文脈で実行し、再点検はその読者役の履歴を使った。初回応答にあった実行条件の自己申告の誤りは、起動条件に照らして訂正し、点検記録に訂正したことを明記している。
読者役の点検は計画の理解経路の確認である。実際の読者の理解や、計画を使わない執筆との品質差を測定した結果ではない。

## 保存する成果物

各フォルダに同じ構成で保存している。

| ファイル | NoSQL / RDBMS | MySQL |
|---|---|---|
| 承認済み計画 `plan.md` | [計画](01-nosql-rdbms-strategy/plan.md) | [計画](02-mysql-latest-updates/plan.md) |
| 初版 `plan-v1.md` | [初版](01-nosql-rdbms-strategy/plan-v1.md) | [初版](02-mysql-latest-updates/plan-v1.md) |
| 初回点検 `reader-review-v1.md` | [記録](01-nosql-rdbms-strategy/reader-review-v1.md) | [記録](02-mysql-latest-updates/reader-review-v1.md) |
| 再点検の入力 `plan-v2-reviewed.md` | [修正版](01-nosql-rdbms-strategy/plan-v2-reviewed.md) | [修正版](02-mysql-latest-updates/plan-v2-reviewed.md) |
| 再点検 `reader-review-v2.md` | [記録](01-nosql-rdbms-strategy/reader-review-v2.md) | [記録](02-mysql-latest-updates/reader-review-v2.md) |
| 指摘の照合・採否 `review-resolution.md` | [記録](01-nosql-rdbms-strategy/review-resolution.md) | [記録](02-mysql-latest-updates/review-resolution.md) |
| 二行の依頼文 `prompt.md` | [依頼文](01-nosql-rdbms-strategy/prompt.md) | [依頼文](02-mysql-latest-updates/prompt.md) |
| 実際のユーザー入力 `input.md` | [入力](01-nosql-rdbms-strategy/input.md) | [入力](02-mysql-latest-updates/input.md) |
| 生成記事 `article-opus-5.5.md` | [記事](01-nosql-rdbms-strategy/article-opus-5.5.md) | [記事](02-mysql-latest-updates/article-opus-5.5.md) |
| 実行記録 `run.json` | [記録](01-nosql-rdbms-strategy/run.json) | [記録](02-mysql-latest-updates/run.json) |

`run.json`は実行結果から必要な項目を抜き出した記録で、CLI全体のログではない。入力・出力のSHA-256、指定モデルと実行モデル、日時、終了状態、トークン数などを含む。

## 同じ入力で再実行する

各テーマの`input.md`を使い、リポジトリ外の空の一時ディレクトリから実行する。以下の`input.md`は絶対パスへ置き換える。

```sh
claude --safe-mode --strict-mcp-config --no-session-persistence \
  --tools '' --disable-slash-commands \
  --model claude-opus-5-5 --output-format json --print \
  < /absolute/path/to/input.md > result.json

jq -e '.subtype == "success" and .is_error == false
  and (.modelUsage | keys == ["claude-opus-5-5"])' result.json
jq -j '.result' result.json > article-opus-5.5.md
```

必要なのは、上記オプションとモデルを利用できる認証済みのClaude CLIである。同じ入力でも生成文章は変わり得るため、保存した記事はこの実行の出力サンプルとして扱う。
