# Project Setup

新しいWebアプリケーションを開始するときは、原則として以下の流れでプロジェクトを作成する。

---

## 全体フロー

```text
web-app-template
↓
新しいGitHub Repositoryを作成
↓
ローカルへClone
↓
GitHub Projectを作成
↓
Default repositoryを設定
↓
Statusを設定
↓
MVP Milestoneを作成
↓
最初のIssueを作成
↓
開発開始
```

---

## 1. Template Repositoryから新しいRepositoryを作成する

GitHubで `web-app-template` を開く。

```text
Use this template
↓
Create a new repository
```

新しいアプリのRepository名を設定する。

例：

```text
reading-ideas-app
```

通常は以下で作成する。

```text
Visibility: Private
```

Template Repositoryから以下の基本構成が引き継がれる。

```text
project/
├── data/
├── docs/
│   └── requirements.md
├── public/
├── src/
├── .gitignore
└── README.md
```

---

## 2. ローカルへCloneする

ターミナルで開発用ディレクトリへ移動する。

```bash
cd ~/Projects
```

GitHub RepositoryのHTTPS URLを使ってCloneする。

```bash
git clone <Repository URL>
```

例：

```bash
git clone https://github.com/USERNAME/reading-ideas-app.git
```

作成されたプロジェクトへ移動する。

```bash
cd reading-ideas-app
```

状態を確認する。

```bash
git status
```

以下のような状態なら準備完了。

```text
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

---

## 3. GitHub Projectを作成する

GitHubプロフィールから、

```text
Projects
↓
New project
```

を選択する。

Project名は以下の形式を基本とする。

```text
<App Name> Development
```

例：

```text
Reading & Ideas App Development
```

---

## 4. Default repositoryを設定する

Project Settingsを開き、

```text
Default repository
```

に新しく作成したRepositoryを指定する。

これによりProjectからIssueを作成するときの基準Repositoryを統一する。

---

## 5. Statusを設定する

Projectでは以下のStatusを基本とする。

```text
Backlog
Ready
In Progress
Review
Done
```

意味：

* `Backlog`：将来対応する作業
* `Ready`：次に着手できる作業
* `In Progress`：現在作業中
* `Review`：確認・テスト中
* `Done`：完了

---

## 6. MVP Milestoneを作成する

対象Repositoryで、

```text
Issues
↓
Milestones
↓
New milestone
```

を選択する。

最初のMilestoneは、

```text
MVP
```

とする。

Due dateは必要になるまで設定しなくてもよい。

Descriptionには、MVPとして達成する状態を簡潔に記載する。

---

## 7. 最初のIssueを作成する

対象Repositoryで、

```text
Issues
↓
New issue
↓
Task
↓
Get started
```

を選択する。

共通Issueテンプレートを使用し、原則として以下を記載する。

```text
目的
やること
完了条件
```

最初のIssueは基本的に、

```text
要件定義を確定してRepositoryに反映する
```

とする。

設定：

```text
Milestone: MVP
Project: 対象アプリのDevelopment Project
Status: Ready
```

---

## 8. プロジェクト立ち上げ完了

以下が揃えば、初期セットアップ完了とする。

```text
GitHub Repository
✓ Templateから作成済み

Local
✓ ~/Projects 配下へClone済み
✓ origin/mainと接続済み

GitHub Project
✓ 作成済み
✓ Default repository設定済み
✓ Status設定済み

Milestone
✓ MVP作成済み

Issue
✓ 最初のIssue作成済み
✓ Project / Milestoneへ紐付け済み
```

ここから通常の開発フローへ移行する。

```text
Issue
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

詳細な開発中の運用については `CONTRIBUTING.md` を参照する。
