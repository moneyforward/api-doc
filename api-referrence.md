# マネーフォワードAPIリファレンス
マネーフォワードAPIの概要については[こちら](README.md)を参照ください

## 認証方式

OAuth2: Authorization Code Flow

## データフォーマット

リクエスト、レスポンスともにJSON形式。

ノーマルレスポンスはHTTPステータスコード200を返します。

エラー時は適切なHTTPステータスコード4XX〜5xxを返します。

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

### 認可

| 　         |メソッド        |URI 　  　 　 　 　 　|必要なパラメーター                               |
|-----------|-------------|----------------|---------------------------------------------|
|認可       |GET または POST|/oauth/authorize|scope, response_type, client_id, redirect_uri|
|トークン     |POST         |/oauth/v2/token |grant_type, code, redirect_uri, client_id     |

### 認可情報

| 　         |メソッド        |URI 　  　 　 　 　 　|必要な権限(スコープ)|
|-----------|-------------|----------------|----------------|
|個別の取得                 |GET または POST|/oauth/userinfo |`openid`           |
|電子メールアドレス付き個別の取得|GET または POST|/oauth/userinfo |`openid email`        |

認可情報を得る場合は、ヘッダに、以下のいずれかの値を与える。`<アクセストークン>`にはアクセストークンが入る。

    Authorization: Bearer <アクセストークン>

または

    X-MFOAuthToken: Bearer <アクセストークン>

### 金融機関のカテゴリー

|                                       |メソッド|URI    　 　 　 　 　　 　 　 　 　|必要な権限(スコープ)|
|---------------------------------------|------|--------------------------|----------------|
|[一覧の取得](service_categories_index.md)|GET 　 |/api/v1/service_categories|なし             |

### 金融機関

|                             |メソッド |URI                 |必要な権限(スコープ)|
|-----------------------------|------|--------------------|------------------|
|[一覧の取得](services_index.md)|GET 　 |/api/v1/services 　  |なし               |
|[個別の取得](services_show.md) |GET 　 |/api/v1/services/:id|なし               |

### 自動取得時のエラー

|                                       |メソッド |URI                     |必要な権限(スコープ)|
|---------------------------------------|------|--------------------------|----------------|
|[一覧の取得](aggregation_errors_index.md)|GET 　 |/api/v1/aggregation_errors|なし             |

### ユーザー

|                           |メソッド|URI        |必要な権限(スコープ)   |
|---------------------------|------|------------|-------------------|
|[個別の取得](user_show.md) 　 |GET 　 |/api/v1/user|なし                |

### ユーザーが登録している金融機関

|                                     |メソッド|URI                          |必要な権限(スコープ) |
|-------------------------------------|------|-----------------------------|------------------|
|[一覧の取得](accounts_index.md)        |GET   |/api/v1/accounts             |`accounts`        |
|[一覧の再取得](accounts_acquire_all.md)|POST  |/api/v1/accounts/acquire     |`acquire_accounts`|
|[個別の登録](accounts_create.md)       |POST  |/api/v1/accounts             |`manage_accounts` |
|[個別の取得](accounts_show.md)         |GET   |/api/v1/accounts/:id 　 　　　 　 |`accounts`        |
|[個別の再取得](accounts_acquire.md)　  |POST 　 |/api/v1/accounts/:id/acquire|`acquire_accounts` |
|[個別の更新](accounts_update.md)       |PATCH または PUT|/api/v1/accounts/:id         |`manage_accounts` |
|[個別の削除](accounts_destroy.md)      |DELETE| /api/v1/accounts/:id        |`manage_accounts` |

### 金融機関登録の追加の質問

|                                    |メソッド|URI                            |必要な権限(スコープ)|
|------------------------------------|------|-------------------------------|------------------|
|[作成](additional_requests_create.md)|POST  |/api/v1/additional_requests    |`manage_accounts` |
|[更新](additional_requests_update.md)|PATCH または PUT|/api/v1/additional_requests/:id|`manage_accounts` |

### 現金、株式等の資産クラス

| 　 　 　 　 　 　 　 　             　                         　 　|メソッド|URI　 　 　                          |必要な権限(スコープ)|
|----------------------------------------------------------|------|----------------------------------|-----------------|
|[クラスの一覧の取得](asset_classes_index.md) 　 　 　 　 　 　 　 　  |GET 　 |/api/v1/asset_classes 　 　 　 　 　 　 |なし             |
|[各資産の合計の一覧の取得](user_asset_classes_index.md)        |GET   |/api/v1/user_asset_classes        |`assets`         |
|[各資産の合計の履歴の取得](user_asset_class_histories_index.md)|GET   |/api/v1/user_asset_class_histories|`assets`         |

### 資産クラスをさらに細かく分類した資産サブクラス、サブアカウント、通貨

|                                                                  |メソッド|URI                                   |必要な権限(スコープ)|
|------------------------------------------------------------------|------|--------------------------------------|------------------|
|[サブクラスの一覧の取得](asset_subclasses_index.md) 　 　 　 　 　 　 　  　  |GET 　 |/api/v1/asset_subclasses 　 　 　 　 　 　  |なし|
|[各資産の合計の一覧の取得](user_asset_summaries_index.md) 　 　 　 　 　 　 |GET 　 |/api/v1/user_asset_summaries 　 　 　 　 　 |`assets`|
|[個別の資産の合計の取得](user_asset_summaries_show.md) 　 　           |GET   |/api/v1/user_asset_summaries/:id       |`assets`|
|[各資産の合計の一覧の履歴の取得](user_asset_summary_histories_index.md)|GET   |/api/v1/user_asset_summary_histories   |`assets`|
|[個別の資産の合計の履歴の取得](user_asset_summary_histories_show.md)   |GET  |/api/v1/user_asset_summary_histories/:id|`assets`|

### 資産

|                                              |メソッド|URI                            |必要な権限(スコープ)|
|----------------------------------------------|------|--------------------------------|----------------|
|[一覧の取得](user_assets_index.md)              |GET   |/api/v1/user_assets             |`assets`        |
|[個別の取得](user_assets_show.md)               |GET   |/api/v1/user_assets/:id         |`assets`        |
|[全体の履歴の取得](user_asset_histories_index.md)|GET   |/api/v1/user_asset_histories    |`assets`        |
|[個別の履歴の取得](user_asset_histories_show.md) |GET   |/api/v1/user_asset_histories/:id|`assets`        |

### 入出金

|                                      |メソッド|URI                                  |必要な権限(スコープ)|
|--------------------------------------|-------|-------------------------------------|----------------|
|[種類の一覧の取得](categories_index.md) |GET 　  |/api/v1/transactions/categories      |`transactions`  |
|[一覧の取得](transactions_index.md)     |GET 　  |/api/v1/transactions                 |`transactions`  |
|[個別の登録](transactions_create.md)     |POST 　  |/api/v1/transactions                 |`manage_transactions`  |
|[個別の更新](transactions_update.md)     |PATCH または PUT 　  |/api/v1/transactions/:id                 |`manage_transactions`  |
|[合計の取得](transaction_summaries_index.md)     |GET 　  |/api/v1/derived/transaction_summaries|`transactions`  |
|[履歴の取得](transaction_histories_index.md)     |GET    |/api/v1/derived/transaction_histories|`transactions`  |

## 連絡先

ご不明点、ご要望等は以下までご連絡ください。

pfm-api@moneyforward.co.jp
