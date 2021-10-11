# マネーフォワード API

## 概要

クラウド家計簿ソフト「マネーフォワード」の開発者向け API のドキュメントです。現在は、クローズド API として、特定のパートナー企業様へ提供をしております。

本 API は継続開発中であり、予告なく変更等が入る可能性があります。

### 提供機能

- ユーザー情報の取得
- 自動取得金融機関情報の取得
- 口座情報の取得・編集
- 入出金情報の取得・編集
- 資産情報の取得
- 取引情報の取得

### 認証・認可方式

OAuth2: Authorization Code Flow に基づく

## 要求

要求のパラメーターは、それぞれ

- パス
- クエリー
- ヘッダー
- (POST メソッド時の)本文

のうちの決められた場所に記載して下さい。本文のパラメーターは JSON 形式で受け取ります。

日付に関するパラメーターの値は ISO 8601 拡張形式に即し、`YYYY-MM-DD` で指定して下さい。

- 例 (2014 年 04 月 01 日):

  ```
  2014-04-01
  ```

名前の末尾が `[]` になっているパラメーターは、1 回の要求で繰り返し使って複数の値を指定することができます。

- 例:

  ```
  https://moneyforward.com/api/v1/accounts?service_category_ids[]=1&service_category_ids[]=2&page=1
  ```

## 応答

成功時には`200`を、エラー時には `4xx` または `5xx` (`x` は数字) をステータスコードとして返します。

## 認証・認可

API の使用には、それに先立って、ユーザーの認可を得、さらにアクセストークンを得るという手順が必要です。発行されるアクセストークンは、API へのアクセスの度に必要です。アクセストークンは、発行から一定時間が過ぎると使えなくなります。発行されたアクセストークンの有効期限が切れたときは、再びユーザーの認可を受けるという手順を踏まずに、再びアクセストークンを得ることができます。

|                                                | メソッド        | URI              |
| ---------------------------------------------- | --------------- | ---------------- |
| [ユーザーの認可を得る](authorize.md)           | GET または POST | /oauth/authorize |
| [アクセストークンを得る](token.md)             | POST            | /oauth/v2/token  |
| [アクセストークンを再び得る](token_refresh.md) | POST            | /oauth/v2/token  |

## マネーフォワード API を使って出来ること

### ユーザー情報の取得

|                                                             | メソッド        | URI                | 必要な権限(スコープ)           |
| ----------------------------------------------------------- | --------------- | ------------------ | ------------------------------ |
| [ユーザーの認証情報や電子メールを得る](userinfo.md)         | GET または POST | /oauth/userinfo    | `openid` または `openid email` |
| [ユーザーの登録状況を得る](user_show.md)                    | GET             | /api/v1/user       | なし                           |
| [ユーザーの SSO トークンを登録する](sso_tokens_create.md)   | POST            | /api/v1/sso_tokens | `manage_sso`                   |
| [ユーザーのデモグラフィック情報を閲覧する](profile_show.md) | GET             | /api/v1/profile    | `profile`                      |

### 金融機関情報の取得

|                                                                                                                         | メソッド | URI                        | 必要な権限(スコープ) |
| ----------------------------------------------------------------------------------------------------------------------- | -------- | -------------------------- | -------------------- |
| [金融機関の全ての分類を得る](service_categories_index.md)                                                               | GET      | /api/v1/service_categories | なし                 |
| [マネーフォワードで口座を登録可能な全ての金融機関を得る](services_index.md)                                             | GET      | /api/v1/services           | なし                 |
| [マネーフォワードで登録可能な特定の金融機関のログインに必要な入力項目を得る](services_show.md)                          | GET      | /api/v1/services/:id       | なし                 |
| [マネーフォワードが金融機関から情報を取得しようとする際に生じうる全てのエラーの種類を得る](aggregation_errors_index.md) | GET      | /api/v1/aggregation_errors | なし                 |

### 口座情報の取得・編集

|                                                                                             | メソッド         | URI                             | 必要な権限(スコープ)                |
| ------------------------------------------------------------------------------------------- | ---------------- | ------------------------------- | ----------------------------------- |
| [口座を登録する](accounts_create.md)                                                        | POST             | /api/v1/accounts                | `manage_accounts`                   |
| [特定の口座連携を解除する](accounts_destroy.md)                                             | DELETE           | /api/v1/accounts/:id            | `manage_accounts`                   |
| [特定の口座の登録内容を書き換える](accounts_update.md)                                      | PATCH または PUT | /api/v1/accounts/:id            | `manage_accounts`                   |
| [特定の口座のログインに必要な追加の入力項目を登録する](additional_requests_create.md)       | POST             | /api/v1/additional_requests     | `manage_accounts`                   |
| [特定の口座のログインに必要な追加の入力項目の答えを編集する](additional_requests_update.md) | PATCH または PUT | /api/v1/additional_requests/:id | `manage_accounts`                   |
| [特定の口座の情報をマネーフォワードに金融機関から再取得させる](accounts_acquire.md)         | POST             | /api/v1/accounts/:id/acquire    | `acquire_accounts`                  |
| [全ての口座の取得状況や資産額合計を得る](accounts_index.md)                                 | GET              | /api/v1/accounts                | `accounts` または `manual_accounts` |
| [特定の口座の取得状況や資産額合計、ログインに必要な入力項目を得る](accounts_show.md)        | GET              | /api/v1/accounts/:id            | `accounts`                          |

### 入出金情報の取得・編集

|                                                                                                 | メソッド         | URI                                   | 必要な権限(スコープ)  |
| ----------------------------------------------------------------------------------------------- | ---------------- | ------------------------------------- | --------------------- |
| [入出金の全ての大分類(及びその中のユーザー作成の中分類)を得る](transaction_categories_index.md) | GET              | /api/v1/transactions/categories       | `transactions`        |
| [入出金項目を登録する](transactions_create.md)                                                  | POST             | /api/v1/transactions                  | `manage_transactions` |
| [特定の入出金項目の情報を書き換える](transactions_update.md)                                    | PATCH または PUT | /api/v1/transactions/:id              | `manage_transactions` |
| [全ての入出金記録を得る](transactions_index.md)                                                 | GET              | /api/v1/transactions                  | `transactions`        |
| [要求の日を含む期間の収支を、日曜始まりの週または月ごとに得る](transaction_histories_index.md)  | GET              | /api/v1/derived/transaction_histories | `transactions`        |
| [日曜始まりの週または月の収支を、資産の分類ごとに得る](transaction_summaries_index.md)          | GET              | /api/v1/derived/transaction_summaries | `transactions`        |
| [カード引き落とし明細一覧を取得する](card_future_payments.md)                                   | GET              | /api/v1/card_future_payments          | `transactions`        |

### 資産情報の取得

|                                                                                 | メソッド | URI                                | 必要な権限(スコープ) |
| ------------------------------------------------------------------------------- | -------- | ---------------------------------- | -------------------- |
| [資産の全ての大分類(及びその中の中分類)を得る](asset_classes_index.md)          | GET      | /api/v1/asset_classes              | なし                 |
| [資産の全ての中分類を得る](asset_subclasses_index.md)                           | GET      | /api/v1/asset_subclasses           | なし                 |
| [全ての資産を得る](user_assets_index.md)                                        | GET      | /api/v1/user_assets                | `assets`             |
| [特定の資産を得る](user_assets_show.md)                                         | GET      | /api/v1/user_assets/:id            | `assets`             |
| [全ての資産の履歴を得る](user_asset_histories_index.md)                         | GET      | /api/v1/user_asset_histories       | `assets`             |
| [全ての大分類ごとの資産の合計を得る](user_asset_classes_index.md)               | GET      | /api/v1/user_asset_classes         | `assets`             |
| [全ての大分類ごとの資産の合計の履歴を得る](user_asset_class_histories_index.md) | GET      | /api/v1/user_asset_class_histories | `assets`             |

### 取引情報の取得

|                                               | メソッド | URI                | 必要な権限(スコープ)                                |
| --------------------------------------------- | -------- | ------------------ | --------------------------------------------------- |
| [全ての約定の履歴を得る](executions_index.md) | GET      | /api/v1/executions | `trades_inquiry` または `crypto_ccy_trades_inquiry` |
