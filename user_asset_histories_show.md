# GET /api/v1/user_asset_histories/:id
ユーザーの個別資産履歴を返します。

## Resrouce URL
https://moneyforward.com/api/v1/user_asset_histories/:id

## Data definition

name | Description 
-----------|------------------------
code | 株式銘柄コード等。
cost | 現在未使用フィールド
entried_at | 資産取得日（特定できなければnull）
entried_price | 取得価格
expire_at	| 資産の有効期限（ポイント等）
jpy_rate | 円換算レート
name | 資産名称
profit | 損益
qty | 数量
value | 評価額
updated_at | 基準日
rated_value | 円換算評価額
rated_profit | 円換算損益
hashed_original_user_asset_id | ヒストリカル作成の元となった、user_assetのid *hashed*
previous_value_set[:value] | 前営業日評価額
previous_value_set[:profit] | 前営業日損益
previous_value_set[:rated_value] | 前営業日円換算評価額
previous_value_set[:rated_profit] | 前営業日円換算損益
previous_value_set[:updated_at] | 前営業日日付


## Parameters
name | Description 
-----------|------------------------
id <br /> *required* | 個別資産履歴ID *hashed*
previous_date <br /> *optional* | 前営業日日付 ※未指定なら前日を採用 
 
## Example
***
> **GET** *https://moneyforward.com/api/v1/user_asset_histories/vpxDzM6STgFT4Br7pFTzVQ==*

    {
      "user_asset": {
        "asset_class_id": 3,
        "asset_subclass_id": 12,
        "code": "",
        "cost": 0,
        "created_at": "2014-05-22T06:33:13+09:00",
        "currency": "JPY",
        "current_price": 389024.721519843,
        "entried_at": null,
        "entried_price": 300000,
        "expire_at": null,
        "jpyrate": 1,
        "name": "【デモ】マネフォファンド",
        "profit": 89024.72151984298,
        "qty": 1,
        "rated_profit": 89024.72151984298,
        "rated_value": 389024.721519843,
        "updated_at": "2014-05-22T06:33:13+09:00",
        "value": 389024.721519843,
        "hashed_id": "vpxDzM6STgFT4Br7pFTzVQ==",
        "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
        "previous_value_set": {
            "profit": 80934.72151984298,
            "rated_profit": 383024.721519843,
            "rated_value": 379024.721519843,
            "updated_at": "2014-06-20T00:00:00+09:00",
            "value": 379024.721519843
        },
        "account": {
          "account_uid_hidden": "dem*",
          "created_at": "2014-04-19T17:33:37+09:00",
          "disp_name": null,
          "error_id": 5,
          "last_aggregated_at": "2014-05-22T06:33:13+09:00",
          "last_succeeded_at": "05/22 06:33",
          "memo": null,
          "message": null,
          "msg_flag": 0,
          "msg_time": null,
          "next_aggregate_at": "2014-05-25T02:27:08+09:00",
          "service_category_id": 1,
          "service_id": 1,
          "status": 2,
          "service": {
            "category_name": "銀行",
            "category_type": "BANK",
            "code": "0005",
            "description": "<li>口座番号ではなくオンラインバンキング用のログイン情報となります。オンラインバンキングの手続きは各金融機関へお問い合わせ下さい。</li><li>登録後、「IDとパスワードをお確かめ下さい」というメッセージが表示された場合、一度本サイトにログイン出来るかのご確認をお願いします。</li>",
            "id": 1,
            "login_url": "https://entry11.bk.mufg.jp/ibg/dfw/APLIN/loginib/login?_TRANID=AA000_001",
            "service_name": "三菱東京UFJ銀行",
            "service_type": "B_MUFG",
            "yomigana": "ミツビシトウキョウユーエフジェイギンコウ"
          }
        },
        "asset_class": {
          "asset_class_name": "投資信託",
          "asset_class_type": "MF",
          "disp_order": 4,
          "id": 3
        },
        "asset_subclass": {
          "asset_class_id": 3,
          "asset_subclass_name": "投資信託",
          "asset_subclass_type": "MUTUAL_FUND",
          "id": 12,
          "liquid": 85
        }
      }
    }
