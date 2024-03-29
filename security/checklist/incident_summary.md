# 国内セキュリティー事故

昨今の日本国内の事例を紹介します。

- [FJcloud-V、ニフクラ不正アクセス（富士通）](https://pfs.nifcloud.com/cs/catalog/cloud_news/catalog_202205161000_1.htm)
- [宅ふぁいる便個人情報流出（オージス総研）](https://www.ogis-ri.co.jp/news/1272165_6734.html)
- [ニトリアプリ個人情報流出（ニトリ）](https://www.nitorihd.co.jp/news/items/2cdbc59fa4c3ffe4da790cc1cfe85200.pdf)
- [SMBCソースコード流出（SMBC）](https://xtech.nikkei.com/atcl/nxt/news/18/09551/)

## FJcloud-V、ニフクラ不正アクセス（富士通）

FJcloud-V、ニフクラで採用しているロードバランサーに脆弱性が存在し、不正アクセスされた事件です。

本事象において、メーカーより脆弱性の報告が出されていましたが、富士通はファームウェアのアップデートができておらず、不正アクセスを許す形となりました。

### 教訓

脆弱性報告を定期実行し、検知、対応できる仕組みを取り入れ、脆弱性を防ぎましょう。

セキュリティー要件書の7.4.1を満たすことができる組織にしましょう。

## 宅ふぁいる便個人情報流出

宅ふぁいる便に保存された情報が外部に流出する事故が起きました。

宅ふぁいる便のサービスを提供するオージス総研は、情報流出の詳細については公表しませんでしたが、パスワードを暗号化せずに保存していたという事故は各メディアで大きく掲載されてました。

### 教訓

パスワードは不可逆な暗号を施し、流出したとしても生のパスワードが分からない様に施しましょう。

セキュリティー要件書の1.3.6を満たすことができる実装にしましょう。

## ニトリアプリ個人情報流出

ニトリアプリにリスト型攻撃が行われ、個人情報が流出しました。不正ログインされたアカウント数は132,000アカウントと多大な被害が出ました。

### 教訓

二要素認証を取り入れましょう。特に新規ログイン時は、セキュリティ強度を上げられる仕組みを導入しましょう。

セキュリティー要件書の1.1.3を満たすことができる実装にしましょう。

## SMBCソースコード流出（SMBC）

SMBCで運用されているシステムのソースコードの一部がGitHub上に公開されました。

SMBCのサービスに被害はありませんでしたが、PCの情報を持ち出し、私用のGitHubにソースコードを公開する事件は業界に衝撃を与えました。

### 教訓

リポジトリやIAMが適切な公開範囲になっているかを確認しましょう。

リポジトリがPublicな設定になっている場合、第三者から閲覧することが可能です。

無料で利用可能なGitホスティングサービスでは、人数制限がありますが、プライベート（非公開）の設定をすることができます。

また、Microsoft社が提供するGitHubでは、無料でも無制限のユーザーで編集可能です。

オンプレで独自に運用する場合でも、第三者に閲覧できないような設定をしましょう。

また、社外に情報を持ち出して公開しないように教育を行いましょう。

ついうっかり秘密鍵をプッシュしてしまう場合があります。

このような場合は、即刻秘密鍵を変更するようにしましょう。

## 最後に

脆弱性が存在すると信頼の損失、賠償などさまざまなダメージを受けることになります。

昨今ではマルウェアに感染し、DDoSに加担することやマイニングのbotが埋め込まれるなど、上記以外の攻撃も多く存在します。

昨今の反社会的勢力はこれらのマルウェアを活用し、収入を得ています。

脆弱性をもつWebアプリケーションを公開する、また脆弱性報告を受けながらも対策を打たずに公開し続けることは、反社会的な勢力へ加担することにつながります。
