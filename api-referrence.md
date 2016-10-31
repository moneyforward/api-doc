# マネーフォワードAPIリファレンス
マネーフォワードAPIの概要については[こちら](README.md)を参照ください

## 認証方式

OAuth2: Authorization Code Flow

## アクセストークンの連携方法
Authorizationヘッダ、または X-MFOAuthToken ヘッダに以下の形式でaccess_tokenをセットする  
`Authorization: Bearer YOUR_ACCESS_TOKEN` または `X-MFOAuthToken: Bearer YOUR_ACCESS_TOKEN`


## データフォーマット

リクエスト、レスポンスともにJSON形式のみ。

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

## OpenID Connect認可エンドポイント

    /oauth/authorize

## OpenID Connectトークンエンドポイント

    /oauth/v2/token

## APIへのHTTPメソッドとエンドポイント

### 金融機関のカテゴリー

|                         |リソース                                                        |
|-------------------------|---------------------------------------------------------------|
|金融機関のカテゴリー一覧の取得|[`GET /api/v1/service_categories`](service_categories_index.md)|

### 金融機関

|               |リソース                                       |必要な権限(スコープ)   |
|---------------|----------------------------------------------|--------------------|
|金融機関一覧の取得|[`GET /api/v1/services`](services_index.md)   |`read` または `write`|
|金融機関詳細の取得|[`GET /api/v1/services/:id`](services_show.md)|`read` または `write`|

### ユーザー

|               |リソース                                 |必要な権限(スコープ)    |
|---------------|----------------------------------------|---------------------|
|ユーザー情報の取得|[`GET    /api/v1/user`](user_show.md)   |`read` または `write` |
|ユーザーの退会   |[`DELETE /api/v1/user`](user_destroy.md)|`write`              |

### ユーザーが登録済みの金融機関

|                    |リソース                                                   |必要な権限(スコープ)   |
|--------------------|----------------------------------------------------------|--------------------|
|金融機関詳細の再取得    |[`POST /api/v1/accounts/:id/acquire`](accounts_acquire.md)|`write`             |
|全金融機関の再取得     |[`POST /api/v1/accounts/acquire`](accounts_acquire_all.md)|`write`             |
|登録金融機関リストの取得|[`GET /api/v1/accounts`](accounts_index.md)               |`read` または `write`|
|金融機関の登録        |[`POST /api/v1/accounts`](accounts_create.md)              |`write`             |
|登録金融機関詳細の取得  |[`GET /api/v1/accounts/:id`](accounts_show.md)            |`read` または　`write`|
|                    |`PATCH /api/v1/accounts/:id`                              |`write`              |
|登録機関の更新        |[`PUT /api/v1/accounts/:id`](accounts_update.md)           |`write`             |
|金融機関の削除        |[`DELETE /api/v1/accounts/:id`](accounts_destroy.md)       |`write`             |

### 自動取得時のエラー

|                         |リソース                                                        |
|-------------------------|---------------------------------------------------------------|
|自動取得時のエラーの一覧の取得|[`GET /api/v1/aggregation_errors`](aggregation_errors_index.md)|

### 金融機関登録の追加の質問

|             |リソース                                                               |必要な権限(スコープ)|
|-------------|----------------------------------------------------------------------|-----------------|
|追加の質問の作成|[`POST /api/v1/additional_requests`](additional_requests_create.md)   |`write`          |
|追加の質問の更新|[`PUT /api/v1/additional_requests/:id`](additional_requests_update.md)|`write`          |
|              |`PATCH /api/v1/additional_requests/:id`                               |`write`         |

### 現金、株式等の資産クラス

|                 |リソース　                                            |必要な権限(スコープ)   |
|-----------------|----------------------------------------------------|--------------------|
|資産クラス一覧の取得|[`GET /api/v1/asset_classes`](asset_classes_index.md)|`read` または `write`|

### 資産クラスごとの資産合計

|                     |リソース                                                         |必要な権限(スコープ)   |
|---------------------|----------------------------------------------------------------|--------------------|
|資産クラスごとの合計の取得|[`GET /api/v1/user_asset_classes`](user_asset_classes_index.md)|`read` または `write`|

### 資産クラスごとの資産合計の履歴

|                           |                                                                               |
|---------------------------|-------------------------------------------------------------------------------|
|資産クラスごとの合計の履歴の取得|[`GET /api/v1/user_asset_class_histories`](user_asset_class_histories_index.md)|

### 資産クラスをさらに細かく分類した資産サブクラス

|                    |                                                           |必要な権限(スコープ)   |
|--------------------|-----------------------------------------------------------|--------------------|
|資産サブクラス一覧の取得|[`GET /api/v1/asset_subclasses`](asset_subclasses_index.md)|`read` または `write`|

### 資産サブクラス、サブアカウント、通貨ごとの資産合計

|                             |リソース                                                              |必要な権限(スコープ)   |
|-----------------------------|---------------------------------------------------------------------|--------------------|
|資産サブクラスごとの合計の取得    |[`GET /api/v1/user_asset_summaries`](user_asset_summaries_index.md)  |`read` または `write`|
|資産サブクラスごとの合計詳細の取得|[`GET /api/v1/user_asset_summaries/:id`](user_asset_summaries_show.md)|`read` または `write`|

### 資産サブクラスごとの資産合計の履歴

|                        |リソース                                                                               |必要な権限(スコープ)   |
|------------------------|-------------------------------------------------------------------------------------|--------------------|
|資産サブクラスごとの合計の履歴一覧の取得|[`GET /api/v1/user_asset_summary_histories`](user_asset_summary_histories_index.md)   |`read` または `write`|
|資産合計履歴詳細の取得  |[`GET /api/v1/user_asset_summary_histories/:id`](user_asset_summary_histories_show.md)|`read` または `write`|

### 資産

|            |リソース                                             |必要な権限(スコープ)   |
|------------|----------------------------------------------------|--------------------|
|資産一覧の取得|[`GET /api/v1/user_assets`](user_assets_index.md)   |`read` または `write`|
|資産詳細の取得|[`GET /api/v1/user_assets/:id`](user_assets_show.md)|`read` または `write`|

### 資産の履歴

|                     |リソース                                                             |必要な権限(スコープ)   |
|---------------------|--------------------------------------------------------------------|--------------------|
|資産の履歴の取得       |[`GET /api/v1/user_asset_histories](user_asset_histories_index.md`)   |`read` または `write`|
|資産の履歴の詳細の取得  |[`GET /api/v1/user_asset_histories/:id](user_asset_histories_show.md`)|`read` または `write`|

### 入出金履歴

|              |リソース                                            |
|--------------|--------------------------------------------------|
|入出金履歴の取得|[`GET /api/v1/transactions`](transactions_index.md)|

### SSOトークン

|               |リソース                                          |
|---------------|-------------------------------------------------|
|SSOトークンの取得|[`POST /api/v1/sso_tokens`](sso_tokens_create.md)|

## 連絡先

ご不明点、ご要望等は以下までご連絡ください。

pfm-api@moneyforward.co.jp
