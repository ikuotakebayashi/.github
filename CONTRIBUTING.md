# Development Workflow

このアカウントで管理するプロジェクトでは、原則として以下の開発フローを使用する。

## 基本フロー

Issue
↓
Ready
↓
Branch作成
↓
In Progress
↓
実装・Commit・Push
↓
Pull Request
↓
Review
↓
Merge
↓
Done
↓
mainを更新

---

## 1. Issueを作成する

Issueには原則として以下を記載する。

* 目的
* やること
* 完了条件

必要に応じてMilestoneとProjectを設定する。

着手前は `Backlog` または `Ready` とする。

---

## 2. 作業を開始する

着手するIssueを `In Progress` に変更する。

最新の `main` を取得する。

```bash
git switch main
git pull
```

Issue専用のブランチを作成する。

```bash
git switch -c feature/123-example
```

ブランチ名は原則として以下の形式とする。

```text
種類/Issue番号-内容
```

例：

```text
feature/4-csv-import
docs/1-finalize-requirements
fix/15-order-validation
```

---

## 3. 変更をCommitする

変更内容を確認する。

```bash
git status
```

変更をステージする。

```bash
git add .
```

Commitする。

```bash
git commit -m "feat: add example feature"
```

---

## 4. GitHubへPushする

初回：

```bash
git push -u origin ブランチ名
```

2回目以降：

```bash
git push
```

---

## 5. Pull Requestを作成する

Pull Requestは以下の方向で作成する。

```text
作業ブランチ
↓
main
```

PR作成後、Issueを `Review` に変更する。

PR本文の最後に、対応するIssueを記載する。

```text
Closes #123
```

これにより、Merge時にIssueを自動的にCloseできる。

---

## 6. Reviewする

Pull Requestの `Files changed` を確認する。

確認する内容：

* 意図した変更になっているか
* 不要なファイルが含まれていないか
* エラーや不整合がないか

問題がなければMergeする。

---

## 7. Merge後

Issueを `Done` にする。

GitHub上の作業ブランチは削除してよい。

ローカルを `main` に戻す。

```bash
git switch main
git pull
```

不要になったローカルブランチを削除する。

```bash
git branch -d ブランチ名
```

最後に確認する。

```bash
git status
```

以下の状態になっていれば完了。

```text
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

---

## Status

Projectでは原則として以下のStatusを使用する。

```text
Backlog
Ready
In Progress
Review
Done
```

* `Backlog`：将来対応する作業
* `Ready`：次に着手できる作業
* `In Progress`：作業中
* `Review`：確認・テスト中
* `Done`：完了
