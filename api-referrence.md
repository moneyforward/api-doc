# マネーフォワードAPIリファレンス
マネーフォワードAPIの概要については[こちら](README.md)を参照ください

## 認証方式

OAuth2: Authorization Code Flow

## アクセストークンの連携方法
ヘッダに、次のいずれかの値を与える。`<アクセストークン>`にはアクセストークンが入る。

    Authorization: Bearer <アクセストークン>

または

    X-MFOAuthToken: Bearer <アクセストークン>

## データフォーマット

リクエスト、レスポンスともにJSON形式。

## ノーマルレスポンスのHTTPステータスコード

200 を返します。

## 共通エラーレスポンス

HTTPステータスコードは適切な4XX〜5xxのコードを返します。

レスポンスbodyの例

    {
      "error_code": 42200,
      "errors":
        [
          "名前の長さは20文字以内にしてください。",
          "日付は現在日付以降にしてください。"
        ]
    }

## エンドポイントと接続方法

### OpenID Connect認可エンドポイント

    /oauth/authorize

### OpenID Connectトークンエンドポイント

    /oauth/v2/token

### OpenID Connect個人情報エンドポイント

    /oauth/userinfo

### 金融機関のカテゴリー

|                                       |メソッド |URI                       |必要な権限(スコープ)   |
|---------------------------------------|------|--------------------------|-------------------|
|[一覧の取得](service_categories_index.md)|GET   |/api/v1/service_categories|`read` または `write`|

### 金融機関

|                             |メソッド |URI                 |必要な権限(スコープ)   |
|-----------------------------|------|--------------------|-------------------|
|[一覧の取得](services_index.md)|GET   |/api/v1/services    |`read` または `write`|
|[個別の取得](services_show.md) |GET   |/api/v1/services/:id|`read` または `write`|

### ユーザー

|                           |メソッド |URI         |必要な権限(スコープ)    |
|---------------------------|------|------------|--------------------|
|[個別の取得](user_show.md)   |GET   |/api/v1/user|`read` または `write`|
|[個別の退会](user_destroy.md)|DELETE|/api/v1/user|`write`             |

### ユーザーが登録している金融機関

|                                     |メソッド |URI                          |必要な権限(スコープ)   |
|-------------------------------------|------|-----------------------------|--------------------|
|[個別の再取得](accounts_acquire.md)　  |POST   |/api/v1/accounts/:id/acquire|`write`             |
|[一覧の再取得](accounts_acquire_all.md)|POST  |/api/v1/accounts/acquire     |`write`             |
|[一覧の取得](accounts_index.md)        |GET   |/api/v1/accounts             |`read` または `write`|
|[個別の登録](accounts_create.md)       |POST  |/api/v1/accounts             |`write`             |
|[個別の取得](accounts_show.md)         |GET   |/api/v1/accounts/:id         |`read` または　`write`|
|                                     |PATCH |/api/v1/accounts/:id         |`write`             |
|[個別の更新](accounts_update.md)       |PUT   |/api/v1/accounts/:id         |`write`             |
|[個別の削除](accounts_destroy.md)      |DELETE| /api/v1/accounts/:id        |`write`             |

### 自動取得時のエラー

|                                       |メソッド |URI                       |必要な権限(スコープ)   |
|---------------------------------------|------|--------------------------|--------------------|
|[一覧の取得](aggregation_errors_index.md)|GET   |/api/v1/aggregation_errors|`read` または `write`|

### 金融機関登録の追加の質問

|                                    |メソッド |URI                           |必要な権限(スコープ)|
|------------------------------------|------|------------------------------|-----------------|
|[作成](additional_requests_create.md)|POST |/api/v1/additional_requests    |`write`          |
|[更新](additional_requests_update.md)|PUT  |/api/v1/additional_requests/:id|`write`          |
|                                    |PATCH|/api/v1/additional_requests/:id|`write`          |

### 現金、株式等の資産クラス

|                                                                |メソッド |URI                               |必要な権限(スコープ)     |
|----------------------------------------------------------------|------|----------------------------------|--------------------|
|[クラスの一覧の取得](asset_classes_index.md)                              |GET   |/api/v1/asset_classes             |`read` または `write`|
|[各資産の合計の一覧の取得](user_asset_classes_index.md)             |GET   |/api/v1/user_asset_classes        |`read` または `write`|
|[各資産の合計の履歴の取得](user_asset_class_histories_index.md)|GET   |/api/v1/user_asset_class_histories|`read` または `write`|

### 資産クラスをさらに細かく分類した資産サブクラス、サブアカウント、通貨

|                                                                  |メソッド |URI                                   |必要な権限(スコープ)     |
|------------------------------------------------------------------|------|--------------------------------------|--------------------|
|[サブクラスの一覧の取得](asset_subclasses_index.md)                    |GET   |/api/v1/asset_subclasses              |`read` または `write`|
|[各資産の合計の一覧の取得](user_asset_summaries_index.md)             |GET   |/api/v1/user_asset_summaries           |`read` または `write`|
|[個別の資産の合計の取得](user_asset_summaries_show.md)   　           |GET   |/api/v1/user_asset_summaries/:id       |`read` または `write`|
|[各資産の合計の一覧の履歴の取得](user_asset_summary_histories_index.md)|GET   |/api/v1/user_asset_summary_histories   |`read` または `write`|
|[個別の資産の合計の履歴の取得](user_asset_summary_histories_show.md)    |GET  |/api/v1/user_asset_summary_histories/:id|`read` または `write`|

### 資産

|                                              |メソッド |URI                             |必要な権限(スコープ)   |
|----------------------------------------------|------|--------------------------------|--------------------|
|[一覧の取得](user_assets_index.md)              |GET   |/api/v1/user_assets             |`read` または `write`|
|[個別の取得](user_assets_show.md)               |GET   |/api/v1/user_assets/:id         |`read` または `write`|
|[全体の履歴の取得](user_asset_histories_index.md)|GET   |/api/v1/user_asset_histories    |`read` または `write`|
|[個別の履歴の取得](user_asset_histories_show.md) |GET   |/api/v1/user_asset_histories/:id|`read` または `write`|

### 入出金

|                                 |メソッド |URI                 |必要な権限(スコープ)   |
|---------------------------------|------|--------------------|--------------------|
|[履歴の取得](transactions_index.md)|GET   |/api/v1/transactions|`read` または `write`|

### SSOトークン

|                           |メソッド |URI               |必要な権限(スコープ)   |
|---------------------------|------|------------------|--------------------|
|[取得](sso_tokens_create.md)|POST  |/api/v1/sso_tokens|`read` または `write`|

## 連絡先

ご不明点、ご要望等は以下までご連絡ください。

pfm-api@moneyforward.co.jp
