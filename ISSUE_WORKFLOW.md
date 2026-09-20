# Issue Workflow

Issueを作成してから、実装・Pull Request・Mergeを経て `Done` にするまでの標準フロー。

---

## 全体フロー

```text
Issue作成
↓
Backlog
↓
Ready
↓
作業ブランチ作成
↓
In Progress
↓
実装
↓
Commit
↓
Push
↓
Pull Request
↓
Review
↓
Merge
↓
Issue Close
↓
Done
↓
ローカルのmainを更新
```

---

## 1. Issueを作成する

Repositoryで以下を選択する。

```text
Issues
↓
New issue
↓
Task
↓
Get started
```

Issueには原則として以下を記載する。

```text
目的
やること
完了条件
```

必要に応じて以下も設定する。

```text
Project
Milestone
```

作成直後のStatusは原則として、

```text
Backlog
```

とする。

---

## 2. 次に着手するIssueをReadyにする

近いうちに着手するIssueを、

```text
Backlog
↓
Ready
```

へ移動する。

`Ready` には、実際に次に着手できるIssueだけを置く。

---

## 3. 作業開始

Issueに着手するとき、

```text
Ready
↓
In Progress
```

へ変更する。

ターミナルで対象Repositoryへ移動する。

```bash
cd ~/Projects/<repository-name>
```

最新の `main` を取得する。

```bash
git switch main
git pull
```

Issue専用ブランチを作成する。

```bash
git switch -c <type>/<issue-number>-<description>
```

例：

```bash
git switch -c feature/4-csv-import
git switch -c docs/2-database-design
git switch -c fix/15-order-validation
```

---

## 4. 実装・編集する

Issueの内容に沿って作業する。

途中で状態を確認する。

```bash
git status
```

必要に応じてIssue本文のチェックリストも更新する。

---

## 5. Commitする

変更内容を確認する。

```bash
git status
```

ステージする。

```bash
git add .
```

Commitする。

```bash
git commit -m "<type>: <summary>"
```

例：

```bash
git commit -m "feat: add CSV import"
git commit -m "docs: add database design"
git commit -m "fix: prevent duplicate orders"
```

---

## 6. GitHubへPushする

ブランチの初回Push：

```bash
git push -u origin <branch-name>
```

例：

```bash
git push -u origin docs/2-database-design
```

同じブランチの2回目以降：

```bash
git push
```

---

## 7. Pull Requestを作成する

GitHubでPull Requestを作成する。

```text
base: main
compare: 作業ブランチ
```

PR本文では以下を確認する。

```text
概要
変更内容
確認内容
関連Issue
```

関連Issueには、

```text
Closes #<Issue番号>
```

を記載する。

例：

```text
Closes #2
```

PR作成後、IssueのStatusを、

```text
In Progress
↓
Review
```

へ変更する。

---

## 8. Reviewする

Pull Requestの `Files changed` を確認する。

主な確認項目：

* 意図した変更になっている
* 不要なファイルが含まれていない
* エラーが発生していない
* 必要な動作確認が完了している
* Issueの完了条件を満たしている

問題がある場合は修正して再Pushする。

```bash
git add .
git commit -m "fix: adjust implementation"
git push
```

Pull Requestは自動的に更新される。

---

## 9. Mergeする

確認が完了したら、

```text
Merge pull request
↓
Confirm merge
```

で `main` に取り込む。

PR本文に、

```text
Closes #<Issue番号>
```

がある場合、Merge時に対応IssueもCloseされる。

---

## 10. Doneにする

IssueがCloseされたことを確認する。

ProjectのStatusが自動で変更されない場合は、

```text
Review
↓
Done
```

へ手動で変更する。

これでIssueの作業は完了。

---

## 11. GitHub上の作業ブランチを削除する

Merge後に表示される、

```text
Delete branch
```

を実行してよい。

変更内容はすでに `main` に入っているため、作業ブランチは不要となる。

---

## 12. ローカルを整理する

ターミナルで `main` に戻る。

```bash
git switch main
```

GitHubの最新状態を取得する。

```bash
git pull
```

不要になったローカルブランチを削除する。

```bash
git branch -d <branch-name>
```

例：

```bash
git branch -d docs/2-database-design
```

最後に確認する。

```bash
git status
```

以下の状態なら完了。

```text
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

---

## Statusの意味

```text
Backlog
```

将来対応するIssue。

```text
Ready
```

次に着手できるIssue。

```text
In Progress
```

現在作業中。

```text
Review
```

実装が終わり、確認・テスト中。

```text
Done
```

Mergeまで完了したIssue。

---

## 基本原則

* 原則として1 Issueにつき1作業ブランチを作る
* `main` へ直接実装しない
* 作業開始前に `main` を最新化する
* Pull Requestで差分を確認してからMergeする
* PRとIssueは `Closes #番号` で紐付ける
* Merge後は作業ブランチを削除する
* `Done` は実装だけでなくMergeまで完了した状態とする
