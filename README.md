# Development Guide

このRepositoryには、すべてのプロジェクトで共通して使用する開発ルール・テンプレート・手順をまとめています。

## Guides

### [PROJECT_SETUP.md](./PROJECT_SETUP.md)

新しいプロジェクトを始めるときの手順。

内容：

* Template Repositoryから新規Repositoryを作成
* ローカルへClone
* GitHub Projectを作成
* Default repositoryを設定
* Statusを設定
* MVP Milestoneを作成
* 最初のIssueを作成
* 開発開始までの確認

---

### [ISSUE_WORKFLOW.md](./ISSUE_WORKFLOW.md)

Issueを作成してから `Done` にするまでの標準フロー。

基本フロー：

```text
Issue作成
↓
Backlog
↓
Ready
↓
Branch作成
↓
In Progress
↓
実装
↓
Commit / Push
↓
Pull Request
↓
Review
↓
Merge
↓
Done
```

---

### [CONTRIBUTING.md](./CONTRIBUTING.md)

すべてのプロジェクトで共通して使用する開発ルール。

主な内容：

* Branch運用
* Commit
* Push
* Pull Request
* Review
* Merge
* Status管理
* Merge後のローカル整理

---

### [MULTI_DEVICE.md](./MULTI_DEVICE.md)

複数PCで同じプロジェクトを安全に開発するための手順。

---

## Templates

### Issue Template

```text
.github/ISSUE_TEMPLATE/task.md
```

Issue作成時に以下の構成を使用する。

```text
目的
やること
完了条件
```

---

### Pull Request Template

```text
.github/pull_request_template.md
```

Pull Request作成時に以下の構成を使用する。

```text
概要
変更内容
確認内容
関連Issue
```

関連Issueは以下の形式で紐付ける。

```text
Closes #123
```

---

## Project Management

GitHub Projectでは、原則として以下のStatusを使用する。

| Status      | 意味        |
| ----------- | --------- |
| Backlog     | 将来対応する作業  |
| Ready       | 次に着手できる作業 |
| In Progress | 現在作業中     |
| Review      | 確認・テスト中   |
| Done        | Mergeまで完了 |

---

## Repository Structure

```text
.github/
├── README.md
├── PROJECT_SETUP.md
├── ISSUE_WORKFLOW.md
├── CONTRIBUTING.md
│
└── .github/
    ├── ISSUE_TEMPLATE/
    │   └── task.md
    │
    └── pull_request_template.md
```

---

## Standard Workflow

### 新しいプロジェクトを始める

→ `PROJECT_SETUP.md`

### Issueに着手する

→ `ISSUE_WORKFLOW.md`

### 開発ルールを確認する

→ `CONTRIBUTING.md`

---

## Principle

GitHubを単なるコードの保存場所ではなく、

```text
要件
↓
Issue
↓
実装
↓
Pull Request
↓
Review
↓
履歴
```

を一元管理する開発基盤として使用する。

---

### [MARKDOWN_CHEATSHEET.md](./MARKDOWN_CHEATSHEET.md)

GitHub、Issue、Pull Request、README、設計ドキュメントで使用するMarkdown記法のチートシート。

---

### [GIT_SETUP.md](./GIT_SETUP.md)

Gitセットアップの流れ
