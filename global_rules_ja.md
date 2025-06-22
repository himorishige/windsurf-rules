# Global AI Coding Rules for Windsurf

これらのルールは、Windsurf AI の支援を受けて開発されるすべてのプロジェクトに適用される普遍的な基準と設定を定めます。

## Core Principles

- **Simplicity First (SF):** 常にもっとも単純な実行可能な解決策を選択します。複雑なパターンやアーキテクチャには明確な正当化が必要です。
- **Readability Priority (RP):** コードは将来の人間と AI の両方が即座に理解できるものでなければなりません。
- **Dependency Minimalism (DM):** 明確なリクエストや説得力のある理由がない限り、新しいライブラリやフレームワークを追加しません。
- **Industry Standards Adherence (ISA):** 関連する言語と技術スタックの確立された慣例に従います。
- **Strategic Documentation (SD):** 複雑なロジックや重要な関数のみコメントします。明白な内容はドキュメント化しません。
  新しいドキュメントは英語で書きます。他の言語のドキュメントがある場合は英語に書き換えます。
- **Test-Driven Thinking (TDT):** すべてのコードは最初からテストしやすいように設計します。

## Workflow Standards

- **Atomic Changes (AC):** 追跡性とロールバック能力を向上させるため、小さく自己完結した変更を行います。
- **Commit Discipline (CD):** 次の従来のフォーマットを使用して、意味のあるメッセージで定期的にコミットすることを推奨します:

  ```
  type(scope): concise description

  [optional body with details]

  [optional footer with breaking changes/issue references]
  ```

  Types: feat, fix, docs, style, refactor, perf, test, chore

- **Transparent Reasoning (TR):** コードを生成する際、どのグローバルルールが意思決定に影響したかを明示します。
- **Context Window Management (CWM):** AI のコンテキスト制限に注意し、必要に応じて新しいセッションを提案します。
- **Preserve Existing Code (PEC):** 明示的に指示されない限り、Windsurf は機能するコードを上書きまたは破壊しません。コードベースの整合性を維持するために保守的な変更を提案します [AC, CA]

## Code Quality Guarantees

- **DRY Principle (DRY):** 重複したコードは禁止します。既存の機能を再利用または拡張します。
- **Clean Architecture (CA):** 整然としたフォーマットで、論理的に構造化された一貫性のあるコードを生成します。
- **Robust Error Handling (REH):** すべてのエッジケースと外部インタラクションに適切なエラーハンドリングを統合します。
- **Code Smell Detection (CSD):** 次の場合に積極的にリファクタリングを提案します:
  - 30 行を超える関数
  - 300 行を超えるファイル
  - 2 段階を超えるネストされた条件分岐
  - パブリックメソッドが 5 つを超えるクラス

## Security & Performance Considerations

- **Input Validation (IV):** すべての外部データは処理前に検証されなければなりません。
- **Resource Management (RM):** 接続を閉じ、リソースを適切に解放します。
- **Constants Over Magic Values (CMV):** マジック文字列や数値を使用しません。名前付き定数を使用します。
- **Security-First Thinking (SFT):** 適切な認証、認可、およびデータ保護を実装します。
- **Performance Awareness (PA):** 計算量とリソース使用を考慮します。

## AI Communication Guidelines

- **Rule Application Tracking (RAT):** ルールを適用する際、括弧内に略語をタグ付けします (例: [SF], [DRY])。
- **Explanation Depth Control (EDC):** 複雑さに応じて説明の詳細度を調整します。簡潔から包括的まで。
- **Alternative Suggestions (AS):** 関連する場合、代替アプローチを長所と短所とともに提供します。
- **Knowledge Boundary Transparency (KBT):** 要求が AI の能力またはプロジェクトのコンテキストを超える場合、それを明確に伝えます。

## 開発プロセス中の継続的ドキュメント化 (CDiP)

- **進捗、TODO、および有益な情報を追跡するために使用される *.md ファイルはすべて最新の状態に保つこと** (例: TASK_LIST.md、README.md、LEARNING_FROM_JAVA.md、VAU_IMPLEMENTATION_PLAN.md など)

* 新しく作成された、またはリクエストされた md ファイルごとにメモリを生成し、AI または開発者がプロジェクトのコンテキストと進捗を把握できるようにします。
* 新しいタスクが追加・完了した場合、または新しい TODO が追加・完了した場合に md ファイルを更新します。

## Feature-Based Development Workflow

1. **Create Feature Branch:**

   - 新しい機能またはタスクごとに、main ブランチから専用のフィーチャーブランチを作成します。
   - ブランチ名は `feature/feature-name` または `task/task-name` [CD] の形式でわかりやすく付けます。

2. **Development Process:**

   - すべての開発作業はフィーチャーブランチ内で完了します [AC]。
   - タスクを完了と見なす前に、すべてのテストが成功することを確認します [CTC]。
   - クリーンアーキテクチャの原則とコーディング規範に従います [CA]。

3. **Task Completion in Feature Branch:**

   - フィーチャーブランチ内の `TASK_LIST.md` でタスクを完了としてマークします [CDiP]。
   - これらの変更をフィーチャーブランチにコミットします [CD]。
   - プルリクエストを作成する前にこれを行う必要があります。

4. **Pull Request Process:**

   - フィーチャーが完了したら main ブランチへプルリクエストを作成します [AC]。
   - 更新された `TASK_LIST.md` をプルリクエストに含めます [CDiP]。
   - レビュアーの承認を待ってから先に進みます。

5. **Merge Process:**

   - 承認後、フィーチャーブランチを main にマージします [AC]。
   - マージが成功したらフィーチャーブランチを削除します [AC]。

6. **Task Tracking:**
   - 更新された `TASK_LIST.md` はすでにマージされた変更に含まれています [CDiP]。
   - PR 承認後に `TASK_LIST.md` を追加で更新する必要はありません。

**このワークフローにより次が保証されます:**

- 各機能は必要に応じて個別にロールバックできます [AC]。
- コード品質はレビュー プロセスによって維持されます [CA]。
- main ブランチは常に動作するバージョンのアプリケーションを保持します [PEC]。
- 進捗が明確に追跡され、ドキュメント化されます [CDiP]。
- タスク完了はフィーチャー作業の一部であり、レビュー プロセスに含まれます [CD]。
