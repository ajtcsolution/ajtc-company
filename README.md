# AI Company Builder

このリポジトリをAIに読ませると、導入先ごとのAI組織を対話形式で構築できます。

特定企業の組織名、理念、役職、事業内容は含みません。自社、個人事業、コンサルティング先ごとに、回答から生成します。

## 所有権

本リポジトリの著作権および所有権はAJTC株式会社に帰属します。導入先が生成した `.company/` 内の情報は、各導入先が管理します。

## 使い方

Claude Codeなど、ファイルを作成できるAIにこのGitHub URLを渡し、次のように依頼してください。

```text
このリポジトリの SETUP.md を読み、私の組織を構築してください。
質問は一度に一問ずつしてください。
```

GitHub URL:

```text
https://github.com/ajtcsolution/ajtc-company
```

AIは最初に秘書の名前と話し方を設定し、その後3問の組織ヒアリングを行います。名前や話し方は「任せる」でも構いません。その場合は、AIが親しみやすく実務的な秘書ペルソナを提案します。

回答後、利用者が確認した対象ディレクトリへ `.company/` を作成します。その後も日常業務を進めながら、一度に一問ずつ質問し、会社の憲法、権限、部署、業務フローを育てます。

## 生成されるもの

```text
.company/
├── CLAUDE.md
├── constitution.md
├── governance/
│   ├── authority.md
│   └── review-policy.md
├── registry/
│   ├── departments.yaml
│   ├── maturity.yaml
│   └── question-backlog.md
├── secretary/
│   ├── CLAUDE.md
│   ├── persona.md
│   ├── inbox/
│   ├── notes/
│   └── todos/
├── decisions/
├── departments/
├── projects/
└── reviews/
```

## 方針

- 秘書をすべての依頼の窓口にする
- 最初は小さく始め、必要な部署だけ追加する
- 特定企業の価値観を自動適用しない

実行仕様は [SETUP.md](SETUP.md) に集約しています。

## Claude Codeプラグインとして使う場合

```text
/plugin marketplace add ajtcsolution/ajtc-company
/plugin install ajtc-company@ajtc-company
/company
```

## License

MIT
