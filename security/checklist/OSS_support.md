# OSSを採用する際の注意点

昨今、製品開発をする上でOSSを採用するということは珍しくありません。

OSSはソースコードが外部に公開されている性質上、攻撃されるリスクがパッケージ製品に比べ上昇します。

そのため、世界中のコントリビューターはOSSの脆弱性を修正し、日々対応しています。

OSSを採用する場合は一度作れば終了というわけではなく、脆弱性対応やサポート期間の対応でパッケージのバージョンアップデートを行う必要があります。

## OSSのサポート期間

OSSにはサポート期間が存在します。

商用契約を結ぶことで、サポート期間を延長可能なOSSも存在します。

OSSのサポート期間を確認し、採用・保守するようにしてください。

特に外部にサービスを公開するような場合、脆弱性の情報に気をつけましょう。

OS、フレームワーク、ライブラリ、ミドルウェアのサポート期限は[endoflife.date](https://endoflife.date/)で確認することができます。

## 既知の脆弱性

脆弱性報告は、[共通脆弱性識別子CVE](https://www.ipa.go.jp/security/vuln/CVE.html)にて管理されています。

JavaにてMavenやGradleを利用している場合、OWASPのプラグイン「[dependency-check](https://jeremylong.github.io/DependencyCheck/dependency-check-gradle/index.html)」を利用することでCVEに報告があがっている脆弱性がないかを確認することができます。

Node.jsでは、`npm audit`にて確認することができます。

このほかにも、プログラミング言語によりさまざまな確認方法があります。

GitHubでは、[Dependabot](https://docs.github.com/ja/code-security/dependabot/dependabot-security-updates/configuring-dependabot-security-updates)と呼ばれる利用している依存関係に脆弱性が存在した場合に通知をしてくれるBotが存在します。

さまざまなツールを活用し、脆弱性に気づくことができる環境を整えましょう。
