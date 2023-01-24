# Solxyz Standard コントリビューションガイドへようこそ <!-- omit in toc -->

Solxyz Standardの品質向上のためにお時間を割いてくださり、ありがとうございます。

このガイドでは、コントリビューションワークフロー（issueの提議、Pull Requestの作成、レビュー、PRのマージなど）を説明します。

- [はじめに](#はじめに)
- [GitHubアカウントの作成](#githubアカウントの作成)
  - [二要素認証（オプション）](#二要素認証オプション)
- [Issues](#issues)
  - [新規issueの提出](#新規issueの提出)
  - [issueの解決](#issueの解決)
- [変更の提出](#変更の提出)
  - [変更の準備](#変更の準備)
  - [ファイルの編集](#ファイルの編集)
  - [編集のコミット](#編集のコミット)
  - [Pull Requestの提出](#pull-requestの提出)
- [GitHubマニュアル](#githubマニュアル)

## はじめに

Solxyz Standardの目的、意義などは[ソルクシーズスタンダード策定の目的](introduction.md)を参照してください。

Solxyz Standardは基本的に[マークダウン](https://ja.wikipedia.org/wiki/Markdown)によって記述されています。

マークダウンの記述方法はWeb上に多くのリファレンスが提供されていますので、ここでは割愛します。

## GitHubアカウントの作成

品質向上に貢献いただくにはGitHubアカウントが必要になります。

次の手順にそってアカウントを作成してください。

1. [GitHub](https://github.com/)にアクセスする
2. 右上の`Sign up`を押下する
3. emailアドレスを要求されるので、入力し、`Continue`を押下する
4. passwordが要求されるので、入力し、`Continue`を押下する
5. ユーザー名を要求されるので、入力し、`Continue`を押下する
6. メール購読の有無を問われるので、`y`または`n`を入力し、`Continue`を押下する
7. 画像認証を求められるので、回答する
8. `Create account`を押下する
9. 登録したメールアドレスに認証コードが届くので、入力を行う
10. `Welcome to GitHub`画面が表示されたら、`Skip personalization`を押下する
11. ダッシュボードが表示されたら作成完了

### 二要素認証（オプション）

二要素認証については[Configuring two-factor authentication](https://docs.github.com/ja/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication)を参照ください。

## Issues

Solxyz Standardの記事の誤りや、疑問点を指摘する際にはIssuesを活用します。

### 新規issueの提出

issueを新規提出する前に、すでに同様のissueが提出されていないか確認してください。

もし既存のものがなければ、[テンプレート](https://github.com/solxyz-jsn/solxyz-development-standard/issues/new/choose)から適切なものを選択して、新しいissueを提出してください。

issueの作成方法については[公式ドキュメント - Issueの作成](https://docs.github.com/ja/issues/tracking-your-work-with-issues/creating-an-issue)を参照してください。

### issueの解決

解決できる既存のissueがある場合には修正を提案することができます。

後述する手順にそってPull Requestを作成してください。

## 変更の提出

### 変更の準備

1. Visual Studio Codeのインストール

    マークダウンファイルを編集するために[Visual Studio Code](https://azure.microsoft.com/ja-jp/products/visual-studio-code/)をインストールします。

2. Dev Containers拡張機能のインストール

   1. Visual Studio Codeを起動

   2. `Ctrl（Command） + Shift + X`を押して拡張機能を開く

   3. 上部検索窓に`Dev Containers`と入力してEnterを押下

   4. 次のように`Dev Containers`が表示されるので、「インストール」をクリック

      ![image.png](/img/dev_container_extention.png)

   5. 完了したら、Visual Studio Codeを再起動する

3. Rancher Desktopのインストール

    Solxyz Standardでは文章校正などのライブラリをコンテナで提供しています。

    コンテナを動作させるために[Rancher Desktop](https://rancherdesktop.io/)をインストールします。

    Docker Desktopが導入されている場合は不要です。

    > Docker Desktopは商用利用が有料となるため注意が必要

4. リポジトリのフォーク

   Solxyz Standardのリポジトリを自分のGitHubアカウントにフォークします

5. リポジトリのクローン

    フォークしたリポジトリをローカルの環境にクローンします

### ファイルの編集

1. Rancher Desktopを起動

2. Visual Studio Codeでクローンしたフォルダを開く

3. `Ctrl（Command） + Shift + P`を押してコマンドパレットを開く

4. 「Reopen in Container」と入力して「Dev Container: Reopen in Container」を選択

    しばらく待つとコンテナが作成され、そのコンテナ上で執筆を開始できます。

    ![image.png](/img/vscode.png)

### 編集のコミット

編集が終わったらファイルをコミットします。

コミットする前にエラーや警告が表示されていないことを確認してください。

### Pull Requestの提出

変更が完了したら、Pull Request（以下「PR」）を作成します。

1. フォークしたリポジトリにアクセスし、Pull requestsタブから、「New pull request」ボタンを押下すると、テンプレートが表示されます。テンプレートにしたがって必要事項を入力し、PRを作成します。

2. PRを提出すると、Solxyz Standardチームのメンバーが提案をレビューします。質問をしたり、追加情報を要求する場合があります。

3. Solxyz Standardチームの要求に対して、PRを更新して変更を適用したら、要求のコメントに変更内容を返信します。

4. チームが変更を承認すると、PRはSolxyz Standardにマージされます。

## GitHubマニュアル

GitHubでの基本的なコントリビュート方法は次に記載があります。必要に応じて参照してください。

- [Git のセットアップ](https://docs.github.com/ja/get-started/quickstart/set-up-git)
- [GitHub フロー](https://docs.github.com/ja/get-started/quickstart/github-flow)
- [pull request を使った共同作業](https://docs.github.com/ja/pull-requests/collaborating-with-pull-requests)
