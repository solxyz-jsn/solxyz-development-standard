# AIサービス利用ガイドライン

## 目的

OpenAI社のChatGPTをはじめとして、AIサービスの普及はめざましく、気軽に利用できるようになりました。

一方で外部サービスの利用をきっかけとした情報漏洩事件も多く発生しています。

サービスの利用に関して方針を設けることで、事件を未然に防ぐことを目的としています。

> 本規約は[クラスメソッド社内のAIサービス利用のガイドライン](https://dev.classmethod.jp/articles/guideline-for-use-of-ai-services/)を参考に作成しました。

## 基本方針

- AIサービスを業務利用する場合は、原則として上長の許可を得ること
- 検証目的で、業務に直接関連しない情報（テストデータなど）を入力して試すことは問題ない
- 業務情報を利用したい場合は、この後の「業務利用する場合」のガイドラインにそうこと
- サービス利用前に、データの取り扱いの規約を必ず確認すること

## 業務利用する場合

- 業務情報を用いる場合は、利用規約を確認し、機密情報の扱いに問題がないサービス・プランを利用すること
  - ユーザーが入力した情報をサービス全体の学習に利用しない、入力データ自体をサービス側で保持しないなど
- 自社内だけで利用できるモデルを学習・作成することは問題ない
- 入力した情報を学習するサービスを業務利用する場合は、業務情報の入力は禁止とする
- 入力した情報がサービス全体での学習に利用されないサービス・プランを利用する場合でも、重大な機密や個人情報の入力は禁止とする

### 文章生成AIの利用

- 文章生成AIが生成する文章は、内容が正しくない場合を認識して利用すること
- 文章コンテンツの粗製乱造をしないこと。（ブログ記事を文章生成AIで乱造するなどの行為は禁止する）
- 文章校正等に用いることは許容するが、校正元の文章は外部公開しても問題ない内容であること

### コード生成AIの利用

- コードの情報をサービス側に転送せず利用できることが望ましい
- コードの情報をサービス側に転送する利用形態の場合、以下を遵守すること
  - 利用範囲については必ずチーム内で合意のうえで利用すること
  - 汎用的な処理における利用のみ許容するなど
  - 業務上機密性の高い処理で利用する場合は、適切にリスクアセスメントを実施すること
- 生成されたコードの責任は利用者が担保すること（自分で作成したもの同様に単体テスト等を実施して品質を確保する）

### その他のコンテンツ生成AIの利用（画像生成AIなど）

- モラルの問われるコンテンツの生成・利用は避けること（既存の著作物に類似した画像の生成など）
- 会議議事などの音声をテキスト化するようなサービスの利用は原則禁止とする
  - 社外に公開してもよいもの（外部向け講演音声など）に限って、上長の許可を得て利用する

## 具体的なサービス

### ChatGPT

[ChatGPT](https://openai.com/blog/chatgpt)をWebから利用する場合、[オプトアウトの申請](https://docs.google.com/forms/d/1t2y-arKhcjlKc1I5ohl9Gb16t6Sq-iaybVFEbLFFjaI/viewform?ts=63cec7c0&edit_requested=true)を行い、受理されたことを確認してから利用してください。
オプトアウトを行っていたとしても、[他ユーザーの会話履歴の一部（要約されたタイトル）が見える問題](https://openai.com/blog/march-20-chatgpt-outage)がありました。
原則的に業務で利用を行う場合、API経由での利用を推奨します。