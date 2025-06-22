# Windsurf 設定ファイル管理リポジトリ

このリポジトリは、Windsurf の各種設定ファイルや運用ルール、ワークフローを一元管理するためのものです。プロジェクトの運用効率や品質向上を目的とし、共通ルールや自動化フローを明文化・共有します。

## 目次

- [グローバルルール](#グローバルルール)
- [TypeScript コーディングルール](#typescript-コーディングルール)
- [ワークフロー一覧](#ワークフロー一覧)
    - [context7](#context7)
    - [gh-pr-summary-review](#gh-pr-summary-review)
    - [git-commit](#git-smart-commit)
    - [ultra-think](#ultra-think)

---

## グローバルルール

- **ファイル:** `global_rules.md`
- **概要:**
    - このリポジトリや Windsurf プロジェクト全体で適用されるAIアシスタント用の共通運用ルールです。
    - 指示の分析・タスク計画・実行・品質管理・最終確認・報告までのプロセスを体系的に定義しています。

## TypeScript コーディングルール

- **ファイル:** `.windsurf/rules/typescript.md`
- **概要:**
    - TypeScript/TSX ファイルを対象としたコーディング規約です。
    - 英語による記述、型宣言の徹底、`any`の禁止、JSDocによるドキュメント化、命名規則（PascalCase, camelCase, kebab-case, UPPERCASE）などを定めています。
    - 関数やロジックの単純化、データの不変性重視、RO-ROパターンの推奨など、保守性・可読性向上のためのルールを網羅しています。

## ワークフロー一覧

### context7
- **ファイル:** `.windsurf/workflows/context7.md`
- **概要:**
    - MCP の context7 を活用して関連ドキュメントを検索・取得し、課題解決に役立てるためのワークフローです。
    - 課題の明確化、context7の有無確認、関連情報の取得・要約・活用、ユーザーへの共有などのプロセスを定義しています。

### gh-pr-summary-review
- **ファイル:** `.windsurf/workflows/gh-pr-summary-review.md`
- **概要:**
    - gh CLI を使って GitHub Pull Request の内容を取得し、要約・レビューするためのワークフローです。
    - PR の一覧取得、詳細確認、diff・変更ファイルの要約、改善点やレビューコメントの提案までの流れを具体的に記載しています。

### git-smart-commit
- **ファイル:** `.windsurf/workflows/git-smart-commit.md`
- **概要:**
    - 変更ファイルの確認から、Conventional Commits 形式のコミットメッセージ生成・コミット・push までをサポートするワークフローです。
    - 変更内容の確認、メッセージ案の作成、ユーザー承認、コミット・push の手順を明確化しています。

### ultra-think
- **ファイル:** `.windsurf/workflows/ultra-think.md`
- **概要:**
    - Sequential Thinking MCP・MECEフレームワーク・ユーザー参加型分岐を活用し、ユーザー指示の背景や最適な解決策を多角的に深掘りするワークフローです。
    - 問題分解、MECE分類、仮説立案・検証、ユーザーとの対話的分岐、最終提案までの思考プロセスを段階的に整理しています。

---

## 利用方法

1. 各種ルールやワークフローは、該当するドキュメントを参照してください。
2. 新たなルールやワークフロー追加時は、README.md の目次・説明も更新してください。

---

## 参考
- 各ドキュメントはプロジェクト標準化・品質向上・運用効率化を目的としています。
- 内容の不明点や改善提案があれば、Issue もしくは Pull Request でご連絡ください。
