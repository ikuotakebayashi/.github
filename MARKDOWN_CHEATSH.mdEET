Markdown Cheat Sheet

GitHub、README、Issue、Pull Request、設計ドキュメントなどで使用するMarkdownの基本記法。

⸻

見出し

# 見出し1
## 見出し2
### 見出し3
#### 見出し4

表示：

見出し1

見出し2

見出し3

通常は、

* # → ページタイトル
* ## → 大項目
* ### → 小項目

くらいで十分。

⸻

太字

**重要な文字**

表示：

重要な文字

⸻

斜体

*強調したい文字*

表示：

強調したい文字

⸻

太字 + 斜体

***強く強調する***

表示：

強く強調する

⸻

打ち消し線

~~削除された内容~~

表示：

削除された内容

⸻

箇条書き

- Item A
- Item B
- Item C

または、

* Item A
* Item B

基本的には - を使用する。

⸻

ネストした箇条書き

- Source
  - Book
  - Article
  - Web
- Note
- Idea

表示：

* Source
    * Book
    * Article
    * Web
* Note
* Idea

⸻

番号付きリスト

1. 要件定義
2. DB設計
3. API設計
4. 実装

表示：

1. 要件定義
2. DB設計
3. API設計
4. 実装

⸻

チェックリスト

Issueで特によく使用する。

- [ ] 未完了
- [x] 完了

表示：

* [ ]	未完了
* [x]	完了

例：

## やること
- [ ] DB設計
- [ ] API設計
- [x] 要件定義

⸻

インラインコード

文章内のファイル名・変数・コマンドなどに使用する。

`requirements.md`

表示：

requirements.md

例：

`git status` を実行する。
`docs/requirements.md` を更新する。

⸻

コードブロック

バッククォート3つで囲む。

```javascript
const message = "Hello";
console.log(message);
```

言語名を書くとシンタックスハイライトされる。

よく使うもの：

```javascript
```
```html
```
```css
```
```sql
```
```bash
```
```json
```
```yaml
```
```text
```

⸻

ターミナルコマンド

```bash
git status
git add .
git commit -m "feat: add feature"
---
## 引用
```markdown
> 情報を保存するのではなく、
> 思考を育てる。

表示：

情報を保存するのではなく、
思考を育てる。

⸻

リンク

[表示する文字](https://example.com)

例：

[GitHub](https://github.com)

⸻

Repository内のファイルへのリンク

[要件定義](./docs/requirements.md)

上の階層：

[README](../README.md)

⸻

画像

![代替テキスト](画像URL)

Repository内：

![画面イメージ](./docs/images/screenshot.png)

⸻

区切り線

---

表示：

⸻

セクションを大きく分けるときに使用する。

⸻

テーブル

| Status | 意味 |
| --- | --- |
| Backlog | 将来対応 |
| Ready | 着手可能 |
| In Progress | 作業中 |
| Review | 確認中 |
| Done | 完了 |

表示：

Status	意味
Backlog	将来対応
Ready	着手可能
In Progress	作業中
Review	確認中
Done	完了

⸻

テーブルの位置揃え

| 左 | 中央 | 右 |
| :--- | :---: | ---: |
| A | B | C |
:---   左揃え
:---:  中央
---:   右揃え

⸻

Issue / Pull Requestを参照する

同じRepository内：

#12

GitHubが自動的にリンクへ変換する。

例：

Issue #12 で再検討する。

⸻

Issueとの関連を示す

Related to #12

単純に関連Issueを示したい場合に使用する。

⸻

Pull RequestでIssueを自動Closeする

PR本文に、

Closes #12

を書く。

PRが main にMergeされると、Issue #12もCloseされる。

他にも、

Fixes #12
Resolves #12

などが使える。

⸻

ユーザーをメンションする

@username

例：

@ikuotakebayashi

GitHub上ではユーザーへのリンク・通知になる。

⸻

コード内で特殊文字をそのまま表示する

Markdown記号を通常文字として表示したい場合は \ を使う。

\# 見出しではない
\* 強調ではない

⸻

改行

通常は空行を入れて段落を分ける。

1つ目の段落。
2つ目の段落。

明示的に改行したい場合は行末に半角スペースを2つ入れる方法もある。

⸻

<details> で折りたたむ

長い補足情報などに便利。

<details>
<summary>詳細を見る</summary>
ここに詳細を書く。
</details>

表示イメージ：

<details>
<summary>詳細を見る</summary>

ここに詳細を書く。

</details>

⸻

GitHub Alert

GitHubでは重要度に応じたAlertを使用できる。

> [!NOTE]
> 補足情報
> [!TIP]
> ヒント
> [!IMPORTANT]
> 重要事項
> [!WARNING]
> 注意事項
> [!CAUTION]
> 特に注意が必要な内容

⸻

よく使うドキュメント構成

Issue

## 目的
このIssueで実現すること。
## やること
- [ ] Task A
- [ ] Task B
- [ ] Task C
## 完了条件
- [ ] 条件A
- [ ] 条件B

⸻

Pull Request

## 概要
変更内容の概要。
## 変更内容
- 変更A
- 変更B
## 確認内容
- [ ] 意図した変更になっている
- [ ] エラーが発生していない
- [ ] 不要なファイルが含まれていない
## 関連Issue
Closes #12

⸻

設計ドキュメント

# タイトル
## 1. 概要
## 2. 目的
## 3. 要件
### 3.1 機能A
### 3.2 機能B
## 4. データ
## 5. 制約
## 6. 今後の検討事項

⸻

よく使う記法まとめ

やりたいこと	Markdown
見出し	## Title
太字	**Text**
斜体	*Text*
打ち消し	~~Text~~
箇条書き	- Item
番号	1. Item
チェック	- [ ] Task
完了	- [x] Task
インラインコード	`code`
引用	> Text
リンク	[Text](URL)
画像	![Alt](URL)
Issue参照	#12
Issue Close	Closes #12
メンション	@username
区切り線	---

⸻

基本方針

Markdownは見た目を細かく作り込むためではなく、

構造
↓
意味
↓
読みやすさ

を簡潔に表現するために使用する。

GitHubでは特に、

見出し
箇条書き
チェックリスト
コード
リンク
Issue参照

を中心に使えば十分。
