# Multi-Device Development

メインPCとサブPCなど、複数の端末で同じプロジェクトを開発するときの標準手順。

GitHubを同期地点として使用し、プロジェクトフォルダそのものをiCloud DriveやGoogle Driveなどで同期しない。

---

## 基本方針

```text
メインPC
   ↓ Push
 GitHub
   ↑ Pull
サブPC
```

コード・設計書・Git履歴はGitHubで共有する。

以下はGitHubでは共有しない。

* `node_modules`
* `.env`
* SQLiteの実データ
* その他 `.gitignore` 対象ファイル

---

## 1. 新しいPCで最初に行うこと

開発用ディレクトリを用意する。

```bash
mkdir -p ~/Projects
cd ~/Projects
```

GitHubから対象RepositoryをCloneする。

```bash
git clone <Repository URL>
```

例：

```bash
git clone https://github.com/USERNAME/reading-ideas-app.git
```

Repositoryへ移動する。

```bash
cd reading-ideas-app
```

状態を確認する。

```bash
git status
```

以下の状態ならGitの準備は完了。

```text
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

---

## 2. Node.jsプロジェクトの場合

`node_modules` はGitHubでは管理しないため、各PCで依存パッケージをインストールする。

```bash
npm install
```

以下はGitで管理する。

```text
package.json
package-lock.json
```

これにより、複数PCで同じ依存関係を再現する。

---

## 3. 環境変数

`.env` はGitHubへPushしない。

そのため、環境変数を使用する場合は各PCに `.env` を作成する。

必要な環境変数の項目だけを共有する場合は、

```text
.env.example
```

をRepositoryに置く。

`.env.example` にはパスワードや秘密情報を書かない。

---

## 4. PCを切り替える前

別のPCへ移る前に、現在の変更状態を確認する。

```bash
git status
```

変更がある場合はCommitする。

```bash
git add .
git commit -m "feat: describe change"
```

GitHubへPushする。

```bash
git push
```

基本原則：

```text
PCを離れる前にPush
```

作業途中でも、別PCで続きを行う場合は作業ブランチをPushしておく。

---

## 5. 別のPCで作業を始める

対象Repositoryへ移動する。

```bash
cd ~/Projects/<repository-name>
```

まず現在の状態を確認する。

```bash
git status
```

---

## 6. mainから新しい作業を始める場合

`main` に切り替える。

```bash
git switch main
```

GitHubの最新状態を取得する。

```bash
git pull
```

その後、Issue用の新しいブランチを作る。

```bash
git switch -c <type>/<issue-number>-<description>
```

例：

```bash
git switch -c feature/4-csv-import
```

基本原則：

```text
作業を始める前にPull
```

---

## 7. 別PCで作業中ブランチの続きを行う場合

まずリモート情報を取得する。

```bash
git fetch
```

対象ブランチへ切り替える。

```bash
git switch <branch-name>
```

例：

```bash
git switch docs/2-database-design
```

最新の変更を取得する。

```bash
git pull
```

その後、作業を再開する。

---

## 8. 作業終了時

変更内容を確認する。

```bash
git status
```

Commitする。

```bash
git add .
git commit -m "<type>: <summary>"
```

Pushする。

```bash
git push
```

別PCで続きを行う場合も、Pushまで行ってから端末を切り替える。

---

## 9. Pull RequestをMergeした後

どちらかのPCでPRをMergeした場合、他のPCでは次回作業前に `main` を更新する。

```bash
git switch main
git pull
```

Merge済みのローカルブランチが残っていれば削除する。

```bash
git branch -d <branch-name>
```

---

## 10. SQLiteの扱い

SQLiteの実データはGitHubでは同期しない。

例：

```text
data/app.db
data/app.db-wal
data/app.db-shm
```

これらは `.gitignore` の対象とする。

開発中は各PCで別々のテストDBを持ってよい。

```text
メインPC
└── 開発用DB A

サブPC
└── 開発用DB B
```

本番運用開始後は、実運用DBを複数PCで直接同期しない。

原則：

```text
アプリコード
→ GitHub

実運用データ
→ 1か所を正本とする

バックアップ
→ 別ストレージへ保存する
```

---

## 11. やってはいけないこと

### プロジェクトフォルダをクラウド同期しながらGit管理する

以下のような場所に開発Repositoryを置かない。

```text
iCloud Drive
Google Drive
Dropbox
```

Gitとファイル同期サービスが同時にファイルを変更すると、不要な競合やDB破損の原因になる可能性がある。

開発Repositoryはローカルの、

```text
~/Projects
```

などに置く。

---

### Pushしていない状態で別PCから同じブランチを編集する

例えば、

```text
メインPC
作業Aを未Push

サブPC
同じブランチで作業B
```

という状態を避ける。

必ず、

```text
Commit
↓
Push
↓
PCを切り替える
↓
Pull
```

の順番を守る。

---

## 12. 基本チェック

### PCを離れる前

```bash
git status
git add .
git commit -m "..."
git push
```

### PCで作業を始める前

```bash
git status
git switch main
git pull
```

作業中ブランチを継続する場合：

```bash
git fetch
git switch <branch-name>
git pull
```

---

## 覚えておくルール

```text
離れる前にPush
始める前にPull
```

複数PCで開発するときは、GitHub上のRepository・Issue・Branchを作業状態の基準とする。
