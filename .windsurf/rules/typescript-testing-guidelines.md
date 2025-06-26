---
trigger: model_decision
description: TypeScript で開発中に test を実装する際に参照するガイドライン
---

# TypeScript Test Strategy Guidelines

## テストの基本原則

### テスト哲学

- 実装の詳細ではなくユーザーの振る舞いをテストする
- AI が生成したコードの信頼性を保証するテストを書く
- type coverage と code coverage の両方を高く維持する
- contract（interface）をテストし、実装はテストしない
- テストは仕様書として機能すべき

### test file の構成

- test file は対象 file と同じ directory に配置
- file 名は`*.test.ts`、`*.test.tsx`、`*.spec.ts`のいずれかを使用
- integration test は`__tests__` directory に配置
- E2E test は`e2e/`または`playwright/` directory に配置

## Unit Test 戦略

### Pure function のテスト

- Vitest を利用（vitest run を利用すること）
- すべての boundary value をテスト
- edge case を網羅的にカバー
- property-based test で複雑な logic を検証
- error case を必ずテスト
- side effect がないことを確認

### Custom hooks のテスト

- `@testing-library/react-hooks`を使用
- initial state を検証
- state の更新が正しく行われることを確認
- cleanup 処理をテスト
- error state の処理を検証

### Utility function のテスト

- input の type が正しく検証されることを確認
- output の type が期待通りであることを検証
- null や undefined の処理を必ずテスト
- 例外的な input に対する振る舞いを確認

## Component Test 戦略

### React Testing Library の活用

- `getByRole`を優先的に使用して accessibility を確保
- `data-testid`は最小限に留める
- user interaction を再現
- async 処理は`waitFor`で適切に待機
- snapshot test は慎重に使用

### Component test の focus

- Props の type が正しく定義されていることを確認
- conditional rendering のすべての path をテスト
- event handler が正しく呼ばれることを検証
- error boundary が適切に機能することを確認
- loading state と error state を明示的にテスト

### Mock の戦略

- 外部依存は boundary で mock
- custom render function で provider を wrap
- MSW を使用して API response を mock
- mock は最小限に留め、可能な限り実際の実装を使用
- type-safe な mock factory を作成

## Integration Test 戦略

### API との integration

- MSW で実際の API response を再現
- error response のテストを必須とする
- rate limit や timeout を simulate
- authentication flow を完全にテスト
- data の整合性を検証

### State 管理の integration

- 複数 component 間の state 同期をテスト
- global state の更新が正しく伝播することを確認
- state の persistence と restoration をテスト
- race condition を検証
- memory leak がないことを確認

### Routing integration

- navigation が正しく動作することを確認
- URL parameter の type safety を検証
- protected route の access control をテスト
- 404 error の処理を確認
- deep link が機能することを検証

## Server Components/Actions Test

### Server Components のテスト

- async data fetch の mock
- error boundary との integration をテスト
- cache の動作を検証
- streaming response を simulate
- type safety を維持したまま分離してテスト

### Server Actions のテスト

- form data の validation logic をテスト
- error response の type を検証
- redirect と revalidation を mock
- progressive enhancement を確認
- typed response を返すことを保証

## E2E Test 戦略

### Playwright の活用

- critical user path に focus
- Page Object pattern で type safety を確保
- parallel execution で高速化
- visual regression test を統合
- CI/CD pipeline で自動実行

### E2E test の範囲

- happy path のみに集中
- authentication flow 全体をカバー
- 決済や critical な workflow を重点的に
- mobile と desktop の両方をテスト
- performance metrics を記録

## Test Data 管理

### Factory pattern

- type-safe な test data factory を作成
- default 値を持つ builder pattern を実装
- random だが再現可能な data 生成
- 関連する entity を一括生成
- 無効な data の pattern も用意

### Fixture 管理

- type 定義された fixture file を使用
- 環境ごとに異なる fixture を用意
- 大量 data test 用の generator
- API response の fixture を typed 管理
- 更新が容易な構造を維持

## Best Practices

### Test の保守性

- DRY 原則を適用して helper function を共有
- test も type-safe に保つ
- 可読性を優先して過度な抽象化を避ける
- test の意図を明確にする命名
- 定期的に test を refactoring