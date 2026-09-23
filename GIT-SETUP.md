# 新規プロジェクトのgit手順

新しいプロジェクトフォルダを作ったら、この順番で進める。

## 1. すでにgit管理下かを確認

```bash
cd ~/Projects/プロジェクト名
git rev-parse --show-toplevel
```

- `fatal: not a git repository` → 未管理。手順2へ
- パスが返る → すでに親のリポジトリに含まれている。**init しない**

親リポジトリの中で `git init` すると入れ子のリポジトリになり、
外側からは中身が追跡されない宙ぶらりんな状態になる。

## 2. リポジトリを作る

```bash
git init
```

## 3. 最初のコミット

```bash
git add .
git commit -m "初期構成"
```

ここまででローカルの履歴が残り、「さっきの状態に戻して」が効くようになる。
GitHubに上げるかどうかに関係なく、この3ステップは最初にやる。

## 4. GitHub CLI にログイン（初回のみ）

```bash
gh auth login
```

選択肢は上から順に:

1. What account do you want to log into? → `GitHub.com`
2. What is your preferred protocol? → `HTTPS`
3. Authenticate Git with your GitHub credentials? → `Y`
4. How would you like to authenticate? → `Login with a web browser`

8桁のコード（`XXXX-XXXX`）が表示されるのでコピーして Enter。
ブラウザでGitHubにログインし、コードを貼って承認する。
`✓ Logged in as ユーザー名` が出れば完了。

マシン全体で有効なので、次のプロジェクトでは不要。

## 5. リモートを作って一気にpush

```bash
gh repo create プロジェクト名 --private --source=. --push
```

GitHub上のリポジトリ作成・リモート登録・pushまでこれ1行で終わる。

## 6. 以降の更新

```bash
git add .
git commit -m "カードパーツを追加"
git push
```

手順5で上流ブランチまで設定されるので、2回目からは `git push` だけで通る。

---

## エラー対応

| エラー | 原因 | 対応 |
|---|---|---|
| `fatal: not a git repository` | まだ init していない | 手順2 |
| `No configured push destination` | リモート未設定 | 手順5、または `git remote add origin URL` |
| `please run: gh auth login` | GitHub CLI 未ログイン | 手順4 |

## 手動でリモートを設定する場合

`gh` を使わず、GitHubのWebで空のリポジトリを作った場合:

```bash
git remote add origin https://github.com/ユーザー名/リポジトリ名.git
git branch -M main
git push -u origin main
```

初回だけ `-u` を付ける。次からは `git push` だけでよい。
