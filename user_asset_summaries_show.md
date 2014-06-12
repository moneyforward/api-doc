# GET /api/v1/user_asset_summaries/:id
ユーザーの個別資産合計を返します。

## Resrouce URL
https://moneyforward.com/api/v1/user_asset_summaries/:id

## Data definition

name | Description 
-----------|------------------------
profit | 損益
value | 評価額
rated_value | 為替レートを勘案した円換算評価額
rated_profit | 為替レートを勘案した円換算損益

## Parameters
name | Description 
-----------|------------------------
id <br /> *required* | 個別資産合計ID *hashed*
 
## Example
***
> **GET** *https://moneyforward.com/api/v1/user_asset_summaries/BR5-TCLSc2eZ-gf5Wxa4lA==*

    {
      "user_asset_summary": {
        "asset_class_id": 3,
        "asset_subclass_id": 12,
        "created_at": "2014-05-22T06:33:13+09:00",
        "currency": "JPY",
        "jpyrate": 1,
        "rated_value": 389024.721519843,
        "updated_at": "2014-05-22T06:33:13+09:00",
        "value": 389024.721519843,
        "hashed_id": "BR5-TCLSc2eZ-gf5Wxa4lA==",
        "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
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