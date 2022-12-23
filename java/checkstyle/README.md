# Checkstyle 利用手引き

Checkstyleとは、Javaソースコードの静的解析ツールです。

コーディングルールに準拠していることをチェックし、違反箇所を洗い出すことができます。

[Checkstyleリファレンス](https://checkstyle.sourceforge.io/)

## 設定項目について

ソースコードの設定項目（チェックルール）は、`module`という単位で表現されます。

また、`module`は親子関係を持ちます。たとえば、「アスタリスクを用いたimport（例：`import hoge.*`）を禁止する」というルールは`TreeWalker`（Javaの構文解析を行う）の子`module`です。

各`module`の解説は、[設定項目の説明](./settings_explanation.md)をご参照ください。

## Checkstyleの使い方

Checkstyleの導入から実行までの手順を解説します。

ソルクシーズスタンダードでは、EclipseのCheckstyleプラグインを使用します。

導入の際は[Checkstyleの使い方](./how_to_use.md)をご参照ください。

## ライセンス

Googleが提供する設定ファイル、[google_checks.xml](https://github.com/checkstyle/checkstyle/blob/master/src/main/resources/google_checks.xml)を一部改変して作成しています。

複製元に従い、[Checkstyle設定ファイル](./checkstyle.xml)は[LGPL v2.1](https://www.gnu.org/licenses/old-licenses/lgpl-2.1.ja.html)の下に提供されます。

改変履歴は[CHANGELOG.md](./CHANGELOG.md)をご参照ください。
