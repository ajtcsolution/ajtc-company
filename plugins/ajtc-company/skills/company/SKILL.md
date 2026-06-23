---
name: company
description: >
  導入先専用のAI組織を対話形式で構築・運営する。
  /company、会社を作る、組織を設計する、TODO・意思決定・部署・権限を管理する依頼で使用する。
trigger: /company
---

# Company

リポジトリ直下の `SETUP.md` が読める場合は、その仕様に従う。プラグイン単体でインストールされている場合は、以下の要約仕様で運用する。

## 必須事項

- 最初に作成先の絶対パスを表示し、利用者の確認を得る。
- `.company/` がなければ、秘書ペルソナを設定してから、組織ヒアリング3問を一問ずつ行って初期化する。
- `.company/` があれば、リンク先と `.company-builder.json` を確認する。
- 特定企業の情報や価値観を初期値として使わない。
- まとまった作業は `completed`、`failed`、`needs-human`、`aborted` のいずれかで終える。
- 同じ責務が2回以上発生した場合だけ、部署追加を一問で提案する。
- 通常業務を終えた後、必要な場合だけ組織成熟の質問を一問行う。

## 初期化

最初に秘書の名前と話し方を一問で確認する。「任せる」「おまかせ」を受け付け、その場合は架空の名前と、丁寧・親しみやすい・簡潔・先回り型の秘書らしい話し方を提案し、了承後に確定する。実在人物の模倣や不要な人格属性の追加はしない。

次に組織情報を一問ずつ確認する。

1. 事業・活動
2. 最重要目標と最大の課題
3. AIに任せたい作業と、人が担当したい作業

回答後、次を作る。

```text
.company/
├── .company-builder.json
├── .gitignore
├── CLAUDE.md
├── constitution.md
├── governance/authority.md
├── governance/review-policy.md
├── registry/departments.yaml
├── registry/maturity.yaml
├── registry/question-backlog.md
├── secretary/CLAUDE.md
├── secretary/persona.md
├── secretary/inbox/
├── secretary/notes/
├── secretary/todos/
├── decisions/
├── departments/
├── projects/
└── reviews/
```

未回答項目は「未確認」と書く。初期部署は秘書だけにする。確定した名前と話し方は `secretary/persona.md` に保存し、以後の対話で使用する。`.company/.gitignore` は `*` を指定し、生成情報を既定でGit管理対象外にする。

## 継続質問の順序

基礎 → 顧客価値 → 事業モデル → 業務フロー → 統治とリスク → 組織 → 改善。

回答できない質問は `registry/question-backlog.md` に保留し、同じ質問を繰り返さない。
