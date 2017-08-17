# マネーフォワードAPIリファレンス

マネーフォワードAPIの概要については[こちら](README.md)を参照ください。不明な点やご要望は  `pfm-api@moneyforward.co.jp` までご連絡ください。

## 要求

要求の各パラメーターは、

* パス
* クエリー
* ヘッダー
* (POSTメソッド時の)本文

のうちで決められた場所に記載して下さい。本文パラメーターはJSON形式で受け取ります。

日時、日付のパラメーターの値には ISO-8601 拡張形式を推奨します。

* 例 (2014年04月01日00時00分01秒):

    ```
    2014-04-01T00:00:01+09:00
    ```

* 例 (2014年04月01日):

    ```
    2014-04-01
    ```

他の `2017/04/01` などの形式も現状では使用可能ですが、将来の動作は保証致しません。

名前の末尾が `[]` になっているパラメーターは、1回の要求で繰り返し使い、複数の値を与えることができます。

* 例: 

    ```
    https://moneyforward.com/api/v1/user_asset_summaries?account_ids[]=LlPqfqeeCZavwPBLmUy6xg==&account_ids[]=dyJaw7FlOG41c1C-LKndFA&asset_subclass_ids[]=39&page=2
    ```

## 応答

成功時には`200`を、エラー時には `4xx` 乃至 `5xx` (`x` は数字) をステータスコードとして返します。

応答の本文はJSON形式で返します。

エラーが生じたときには、本文に次のような形式で返します。

* 例:

    ```
    {
      "error_code": 42200,
      "errors":
        [
          "名前の長さは20文字以内にしてください。",
          "日付は現在日付以降にしてください。"
        ]
    }
    ```

## 認証・認可

API の使用時には、始めに認可を得、アクセストークンを得るという手順が必要です。APIへのアクセスにはアクセストークンが必要です。アクセストークンは発行から一定時間が過ぎると使えなくなります。一度アクセストークンの発行を浮け、その有効期限が切れたときは、再び認可を受ける手順を踏まずにアクセストークンを再び得ることができます。

|                                              |メソッド       |URI             |
|----------------------------------------------|---------------|----------------|
|[認可を得る](authorize.md)                    |GET または POST|/oauth/authorize|
|[アクセストークンを得る](token.md)            |POST           |/oauth/v2/token |
|[アクセストークンを再び得る](token_refresh.md)|POST           |/oauth/v2/token |

## マネーフォワード API を使って出来ること

### ユーザ情報の閲覧

|                                                   |メソッド       |URI                |必要な権限(スコープ)          |
|---------------------------------------------------|---------------|-------------------|------------------------------|
|[ユーザーの認可情報を閲覧する](userinfo.md)            |GET または POST|/oauth/userinfo   |`openid` または `openid email`|
|[ユーザーの情報を閲覧する](user_show.md)               |GET            |/api/v1/user      |なし                          |
|[ユーザーのSSOトークンを閲覧する](sso_tokens_create.md)|POST           |/api/v1/sso_tokens|`sso_tokens`                  |
[//]: # |ユーザーの情報を削除する|DELETE|/api/v1/user||

### 金融機関情報の閲覧

|                                                                                                                       |メソッド|URI                       |必要な権限(スコープ)|
|-----------------------------------------------------------------------------------------------------------------------|--------|--------------------------|--------------------|
|[金融機関の全ての分類を閲覧する](service_categories_index.md)                                                              |GET     |/api/v1/service_categories|なし                |
|[マネーフォワードで口座を登録可能な全ての金融機関を閲覧する](services_index.md)                                            |GET     |/api/v1/services          |なし                |
|[マネーフォワードで登録可能な特定の金融機関のログインに必要な入力項目を閲覧する](services_show.md)                         |GET     |/api/v1/services/:id      |なし                |
|[マネーフォワードが金融機関から情報を取得しようとする際に生じうる全てのエラーの種類を閲覧する](aggregation_errors_index.md)|GET     |/api/v1/aggregation_errors|なし                |

### 口座情報の閲覧・編集

|                                                                                                   |メソッド        |URI                            |必要な権限(スコープ)|
|---------------------------------------------------------------------------------------------------|----------------|-------------------------------|--------------------|
|[口座を登録する](accounts_create.md)                                                       |POST            |/api/v1/accounts               |`manage_accounts`   |
|[特定の口座連携を削除する](accounts_destroy.md)                                            |DELETE          |/api/v1/accounts/:id          |`manage_accounts`   |
|[特定の口座の登録内容を編集する](accounts_update.md)                                       |PATCH または PUT|/api/v1/accounts/:id           |`manage_accounts`   |
|[特定の口座のログインに必要な追加の入力項目を登録する](additional_requests_create.md)      |POST            |/api/v1/additional_requests    |`manage_accounts`   |
|[特定の口座のログインに必要な追加の入力項目の答えを編集する](additional_requests_update.md)|PATCH または PUT|/api/v1/additional_requests/:id|`manage_accounts`   |
|[全ての口座の情報をマネーフォワードに金融機関から再取得させる](accounts_acquire_all.md)    |POST            |/api/v1/accounts/acquire       |`acquire_accounts`  |
|[特定の口座の情報をマネーフォワードに金融機関から再取得させる](accounts_acquire.md)        |POST            |/api/v1/accounts/:id/acquire   |`acquire_accounts`  |
|[全ての口座の取得状況や資産額合計を閲覧する](accounts_index.md)                            |GET             |/api/v1/accounts               |`accounts`          |
|[特定の口座の取得状況や資産額合計、ログインに必要な入力項目を閲覧する](accounts_show.md)   |GET             |/api/v1/accounts/:id           |`accounts`          |

### 入出金情報の閲覧・編集

|                                                                                                                        |メソッド        |URI                                  |必要な権限(スコープ) |
|------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------------------|---------------------|
|[入出金の全ての大分類(及びその中のユーザー作成の中分類)を閲覧する](transaction_categories_index.md)                         |GET             |/api/v1/transactions/categories      |`transactions`       |
|[入出金項目を登録する](transactions_create.md)                                                                              |POST            |/api/v1/transactions                 |`manage_transactions`|
|[特定の入出金項目の情報を編集する](transactions_update.md)                                                                  |PATCH または PUT|/api/v1/transactions/:id             |`manage_transactions`|
|[全ての入出金記録を閲覧する](transactions_index.md)                                                                         |GET             |/api/v1/transactions                 |`transactions`       |
|[要求の日を含む期間の、日曜始まりの週または月ごとの全ての入出金を閲覧する](transaction_histories_index.md)                  |GET             |/api/v1/derived/transaction_histories|`transactions`       |
|[要求の日を含み、日曜始まりの週または月を単位とする期間の、入出金の大分類毎の収支を閲覧する](transaction_summaries_index.md)|GET             |/api/v1/derived/transaction_summaries|`transactions`       |

### 資産情報の閲覧

|                                                                                     |メソッド|URI                               |必要な権限(スコープ)|
|-------------------------------------------------------------------------------------|--------|----------------------------------|--------------------|
|[資産の全ての大分類(及びその中の中分類)を閲覧する](asset_classes_index.md)               |GET     |/api/v1/asset_classes             |なし                |
|[資産の全ての中分類を閲覧する](asset_subclasses_index.md)                                |GET     |/api/v1/asset_subclasses          |なし                |
|[全ての資産を閲覧する](user_assets_index.md)                                             |GET     |/api/v1/user_assets               |`assets`            |
|[特定の資産を閲覧する](user_assets_show.md)                                              |GET     |/api/v1/user_assets/:id           |`assets`            |
|[全ての資産の履歴を閲覧する](user_asset_histories_index.md)                              |GET     |/api/v1/user_asset_histories      |`assets`            |
|[特定の資産の履歴を閲覧する](user_asset_histories_show.md)                               |GET     |/api/v1/user_asset_histories/:id  |`assets`            |
|[全ての大分類ごとの資産の合計を閲覧する](user_asset_classes_index.md)                    |GET     |/api/v1/user_asset_classes        |`assets`            |
|[全ての大分類ごとの資産の合計の履歴を閲覧する](user_asset_class_histories_index.md)      |GET     |/api/v1/user_asset_class_histories|`assets`            |
|[中分類や通貨の全ての組み合わせごとの資産の合計を閲覧する](user_asset_summaries_index.md)|GET     |/api/v1/user_asset_summaries      |`assets`            |
|[中分類や通貨の特定の組み合わせの資産の合計を閲覧する](user_asset_summaries_show.md)     |GET     |/api/v1/user_asset_summaries/:id  |`assets`            |
