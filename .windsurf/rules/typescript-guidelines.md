---
trigger: glob
globs: *.ts,*tsx
---

# TypeScript 開発ガイドライン

## Type System & Type Safety

### Strict Type Configuration

- tsconfig.json で `strict: true` を必須設定にする
- `noImplicitAny`, `strictNullChecks`, `strictFunctionTypes` を有効にする
- 未使用の変数とパラメーターの検出を有効にする
- switch 文のフォールスルーを防止する設定を有効にする

### Type Declaration Patterns

- 関数のパラメーターと戻り値には必ず型を宣言する
- 単純な変数宣言では TypeScript の型推論を活用する
- `any` の使用を禁止し、本当に未知の型には `unknown` を使ってから絞り込む
- Utility Types（`Partial`, `Required`, `Pick`, `Omit`）を積極的に使用する
- 読み取り専用プロパティで不変性を表現する
- リテラル型と `as const` アサーションで定数を表現する

## AI-Optimized Code Organization

### Import Organization

- 型 importには（`import type` を使用）

## Naming Conventions

### Files and Directories

- Components: kebab-case（例: `user-profile.tsx`）
- 型定義ファイル: `.types.ts` 拡張子
- Hooks: kebab-case かつ `use-` プレフィックス
- Utilities: kebab-case

### Code Entities

- Components: PascalCase
- Variables: camelCase
- Functions/Hooks: camelCase
- Constants: UPPER_SNAKE_CASE
- Types/Interfaces: PascalCase
- Enums: PascalCase、値は UPPER_SNAKE_CASE

## Function & Component Guidelines

### Component Best Practices

- 複雑な props よりも composition を優先する
- Single Responsibility Principle を遵守する
- 条件付きレンダリングは早期 return で実装する
- コンポーネントは 20 行以内を目標とする

### Function Design Principles

- 各関数は単一の目的を持つ
- テスト容易性と AI の理解を高めるために pure function を優先する
- 早期 return の guard clause を使いネストを減らす
- 関数名はその動作を明確に表現する

## Documentation for AI Context

- 複雑なロジックには JSDoc コメントを追加する
- パラメーター、戻り値、例外を明確にドキュメント化する
- `AI Note:` プレフィックスで AI 向けの実装メモを含める

## Structured Error Messages

- コンテキストを保持するためにカスタム Error クラスを使用する
- エラーには関連フィールド、値、制約を含める
- 具体的なエラー名（`ValidationError`, `ApiError` など）を用いる

## Configuration & Environment

### Type-Safe Configuration

- 環境変数を `ProcessEnv` インターフェイスで定義する
- 設定オブジェクトを `as const` で不変にする
- 必須環境変数を起動時に検証する

## Best Practices Summary

1. すべてに型を付けることで AI へのインラインドキュメントとする
2. 複雑な UI は単純で型付けされたコンポーネントから構築する
3. 厳密な型付けとバリデーションでエラーを早期に捕捉する
4. 公開 API と複雑なロジックには JSDoc を使用する
5. 既存のパターンに従い予測可能な AI 支援を得る
6. type tests で型安全性を保証する
7. 自明な場合は TypeScript に推論させ、そうでなければ明示する

## Anti-Patterns to Avoid

- `any` の使用や `@ts-ignore` でエラーを抑制すること
- 同一ファイルで named export と default export を混在させること
- 特異性を失う過度に汎用的な型を作成すること
- 宣言的代替手段があるのに命令的コードを書くこと
- 過剰な責務を持つ "God component" を作ること
- 動的リストで index を key に使うこと
- 参照を新しくせずに state を直接変更すること