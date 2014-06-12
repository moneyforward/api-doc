# GET /api/v1/user_asset_summaries
ユーザーの保有する個別資産合計リストを返します。
user_asset_summaryは(個別資産をサブアカウント、アセットサブクラス、通過毎に集計したものです）

## Resrouce URL
https://moneyforward.com/api/v1/user_asset_summaries

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
account_ids <br /> *optional* | 登録金融機関ID *hashed* *Array*
asset_class_ids  <br /> *optional* | アセットクラスID *Array*
asset_subclass_ids  <br /> *optional* | アセットサブクラスID *Array*
page  <br /> *optional* | ページ番号
limit <br /> *optional* | 1ページあたりのエレメント数.デフォルト100、最大500

 
## Example
***
> **GET** *https://moneyforward.com/api/v1/user_asset_summaries?account_ids[]=LlPqfqeeCZavwPBLmUy6xg==&asset_subclass_ids[]=39*

    {
      "limit": 100,
      "offset": 0,
      "total_count": 1,
      "user_asset_summaries": [
        {
          "user_asset_summary": {
            "asset_class_id": 9,
            "asset_subclass_id": 39,
            "created_at": "2014-05-22T06:33:13+09:00",
            "currency": "JPY",
            "jpyrate": 1,
            "profit": 3000,
            "rated_value": 775155.8708305522,
            "rated_profit": 3000,
            "updated_at": "2014-05-22T06:33:13+09:00",
            "value": 775155.8708305522,
            "hashed_id": "EZOB3wR14WhMJDWb49ydFg==",
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
              "asset_class_name": "年金",
              "asset_class_type": "PNS",
              "disp_order": 10,
              "id": 9
            },
            "asset_subclass": {
              "asset_class_id": 9,
              "asset_subclass_name": "確定拠出年金",
              "asset_subclass_type": "KAKUTEI_PNS",
              "id": 39,
              "liquid": 70
            }
          }
        }
      ]
    }