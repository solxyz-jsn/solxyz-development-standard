# Giteaを中心とした現代の開発フロー: CI/CDと静的解析の統合ガイド

## はじめに

このガイドは、Giteaを中心とした開発フローを実現するためのガイドです。

Giteaを中心とした開発フローを実現するためには、Giteaと連携するツールをいくつか導入する必要があります。このガイドでは、Giteaと連携するツールの導入方法を解説します。

ガイドで用いるツールは、すべて商用利用可能なOSSのツールです。

クローズドな環境で開発する際に利用することを想定しています。

ただし、セットアップ時は各ソフトウェアをインストールを行うため、インターネットに接続できる環境が必要です。

### Giteaとは

Giteaは、Gitをベースとしたオープンソースのソースコード管理システムです。GitHubやGitLabと同様の機能を提供しますが、それらと比べ、シンプルで軽量なのが特徴です。

また、OSSであるため、自分のサーバー上にインストールすることができます。

Giteaの詳細については、[Giteaの公式サイト](https://gitea.io/)を参照してください。

### SonarQubeとは

SonarQubeは、オープンソースの静的解析ツールです。SonarQubeを用いることで、ソースコードの品質を自動的に評価することができます。

同様のサービスは、各クラウドベンダーをはじめとしてさまざまなものが提供されていますが、SonarQubeはオープンソースであるため、自分のサーバー上にインストールすることができます。

SonarQubeの詳細については、[SonarQubeの公式サイト](https://www.sonarqube.org/)を参照してください。

## このガイドで学べること

このガイドでは、次のことを学ぶことができます。

- Giteaを中心とした開発フローの構築方法
- SonarQubeを用いた静的解析の導入方法
- GiteaとSonarQubeを連携する方法
- Gitea Actionsを用いたCI/CDの導入方法

## このガイドでの動作確認環境

このガイドは、次の環境で動作確認を行っています。

- Ubuntu 22.04 LTS
- MicroK8s v1.22.2
- AWS EC2 t2.large（2vCPU, 8GB RAM）

## 備考

Gitの基本的な使い方については、ソルクシーズアカデミーを参照してください。

## 目次

### [OSセットアップ](./os-setup.md)

### Gitea

#### [Giteaのセットアップ](./gitea/gitea-setup.md)

#### [GitHubフローの導入](./gitea/github-flow.md)

#### [GiteaによるGitHubフローの実現](./gitea/github-flow-with-gitea.md)

### SonarQube

#### [SonarQubeのセットアップ](./sonarqube/SonarQubeセットアップ手順.md)

#### [SonarQube使い方](./sonarqube/SonarQube運用方法.md)

#### SonarQubeとIDEの連携

##### [IntelliJ IDEA](./sonarqube/IntelliJ_IDEAでSonarLintを使用する.md)

##### [Visual Studio Code](./sonarqube/Visual_Studio_CodeでSonarLintを使用する.md)

##### [Eclipse](./sonarqube/EclipseでSonarLintを使用する.md)

### 補足

#### [CI/CDとは何か](./what-is-ci-cd.md)

#### [CI/CDの使い方](./how-to-use-ci-cd.md)
