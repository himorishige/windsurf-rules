---
description: プランニングモード開始時に新しいgit branchをmainブランチから作成するワークフロー
---
# プランニングモード開始ワークフロー

このワークフローは、プランニングモードを開始する際に自動的に新しいgitブランチをmainブランチから作成します。

## 1. 現在のブランチを確認

```bash
CURRENT_BRANCH=$(git branch --show-current)
echo "現在のブランチ: $CURRENT_BRANCH"
```

## 2. メインブランチに切り替え

```bash
git checkout main
```

## 3. 最新の変更をプル

```bash
git pull origin main
```

## 4. 新しいブランチ名を生成

現在の日付と機能名を組み合わせたブランチ名を生成します。

```bash
# 日付と機能名を含むブランチ名を生成 (例: feat/20240627-planning)
FEATURE_NAME="planning"  # デフォルトの機能名
BRANCH_NAME="feat/$(date +%Y%m%d)-${FEATURE_NAME}"
```

## 5. 新しいブランチを作成して切り替え

```bash
git checkout -b "$BRANCH_NAME"
```

## 6. リモートリポジトリにプッシュ（オプション）

必要に応じて、新しいブランチをリモートにプッシュします。

```bash
git push -u origin "$BRANCH_NAME"
```

## 7. ブランチ情報を表示

```bash
echo "新しいブランチを作成しました: $(git branch --show-current)"
echo "元のブランチ: $CURRENT_BRANCH"
```

## カスタマイズオプション

### ベースブランチの変更

デフォルトではmainブランチから作成しますが、別のブランチを指定することもできます：

```bash
BASE_BRANCH="develop"  # 任意のブランチ名に変更可能
git checkout "$BASE_BRANCH"
git pull origin "$BASE_BRANCH"
```

### ブランチ名のカスタマイズ

ブランチ名をカスタマイズするには、`FEATURE_NAME` 変数を変更します：

```bash
# 例: 機能名を指定
FEATURE_NAME="user-authentication"  # 機能名をハイフン区切りで指定
BRANCH_NAME="feat/$(date +%Y%m%d)-${FEATURE_NAME}"
```

例: 
- `feat/20240627-user-authentication`
- `feat/20240627-payment-integration`
