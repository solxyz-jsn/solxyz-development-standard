# Eclipse Javaフォーマッター利用手引き

## 本ドキュメントについて

本ドキュメントはEclipse（version: 2022-06 Java Standard）におけるフォーマッター設定について解説したものです。

## 設定ファイル

設定ファイルは次のとおりです。

[Eclipse Javaフォーマッター設定ファイル](./settings.xml)

## 設定ファイルの比較

[設定ファイルの比較](./diff.md)

ソルクシーズスタンダードが提供する設定ファイルは、Eclipseのデフォルトのフォーマッターとは一部設定項目が異なります。

上記のドキュメントは、異なる設定項目について差分を列挙したものです。

## 設定項目詳細

[設定項目解説](./settings_explanation.md)

GUIにおける設定と設定ファイルをエクスポートした際の設定値を照らし合わせ、サンプルコードを交えて各項目の説明を行います。

設定項目は９つの大項目からなります。

- インデント
- 波括弧の位置
- 丸括弧の位置
- 空白
- ブランク行
- 改行
- 行折り返し
- コメント
- off/onタグ

それぞれの意味について簡単にまとめます。フォーマッターをカスタムする際にご活用ください。

|大項目|意味|
|--|--|
|インデント|インデント数、およびインデントする対象を規定する|
|波括弧の位置|波括弧`{}`の位置をステートメントごとに規定する|
|丸括弧の位置|丸括弧`()`の位置をステートメントごとに規定する|
|空白|空白の挿入の有無をステートメントごとに規定する|
|ブランク行|（行区切りとしての）ブランク行の挿入の有無をステートメントごとに規定する|
|改行|改行の挿入の有無をステートメントごとに規定する|
|行折り返し|折り返しの有無をステートメントごとに規定する|
|コメント|JavaDocやコメントのフォーマットを規定する|
|off/onタグ|フォーマッターの無効化/有効化を規定する|

## ライセンス

Nablarchが提供する[Nablarchスタイルガイド](https://github.com/nablarch-development-standards/nablarch-style-guide)より、[Nablarchコードフォーマッター](https://github.com/nablarch-development-standards/nablarch-style-guide/blob/master/java/assets/nablarch-code-formatter.xml)を一部改変して作成しています。

複製元に従い、[Eclipse Javaフォーマッター設定ファイル](./settings.xmlq)は[Apache License Version 2.0](https://www.apache.org/licenses/LICENSE-2.0.txt)の下に提供されます。

改変履歴は[CHANGELOG.md](./CHANGELOG.md)をご参照ください。
