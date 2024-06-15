# インターフェイス仕様書

## 規格と形式

REST APIインターフェイス仕様書の作成には、[`OpenAPI (旧：Swagger)`](https://www.openapis.org/)の最新バージョンを採用し、仕様に準拠したYAMLまたはJSONフォーマットにて記述します。
OpenAPIは、REST APIを記述するための標準的な仕様フォーマットであり、APIの構造と動作を明確に定義できます。

OpenAPIには、さまざまなエコシステムが存在します。これにより、コードの自動生成やテスト自動化などが可能になります。

## 内容

OpenAPIには、次の項目を明確かつ簡潔に記載することとします。

- APIの目的と機能の概要
- 認証方法とセキュリティ要件
- エンドポイントURLとHTTPメソッド
- リクエストとレスポンスのデータ構造（必須/オプションのパラメータ、データ型、制約事項など）
- APIの制限事項（レート制限、ページネーションなど）
- エラーコードとエラーメッセージ
- 使用例と注意事項

## ドキュメントの管理

OpenAPIの変更履歴は、Gitを用いたバージョン管理にて行います。
ドキュメントの更新日時と担当者は、Gitのコミットで判断し、更新内容もコミットメッセージに記載します。

## サンプルコード

Swaggerの例を次に示します。
このコードは、ユーザー一覧を取得するためのエンドポイントを定義しています。

```yaml
openapi: 3.0.0
info:
  title: サンプルAPI
  version: 1.0.0
  description: このAPIは、サンプルアプリケーションのためのものです。

paths:
  /users:
    get:
      summary: ユーザー一覧の取得
      description: 登録されているすべてのユーザーを取得します。
      responses:
        '200':
          description: 成功レスポンス
          content:
            application/json:    
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/User'
        '401':
          $ref: '#/components/responses/UnauthorizedError'

components:
  schemas:
    User:
      type: object
      properties:
        id:
          type: integer
        name:
          type: string
        email:
          type: string
          format: email
      required:
        - id
        - name
        - email

  responses:
    UnauthorizedError:
      description: 認証エラー
      content:
        application/json:
          schema:
            $ref: '#/components/schemas/Error'

    Error:
      type: object
      properties:
        code:
          type: integer
        message:
          type: string
```
