# GET /api/v1/user_asset_class_histories
ユーザーの資産合計をアセットクラス別に集計したものの履歴を返します。

## Resrouce URL
https://moneyforward.com/api/v1/user_asset_class_histories

## Data definition

name | Description 
-----------|------------------------
profit | 損益
value | 評価額
rated_profit | 為替レート勘案円換算損益
rated_value | 為替レート勘案円換算評価額
updated_at | 基準日

## Parameters
name | Description 
-----------|------------------------
account_ids <br /> *optional* | 登録金融機関ID *hashed* *Array*
asset_class_ids  <br /> *optional* | アセットクラスID *Array*
asset_subclass_ids  <br /> *optional* | アセットサブクラスID *Array*
target_dates <br /> *optional* | 履歴検索指定日。from_date,to_dateより優先 *Array*
from_date <br /> *optional* | 履歴検索開始日。デフォルトは昨日日付
to_date <br /> *optional* | 履歴検索終了日。デフォルトは昨日日付
 
## Example
***
> **GET** *https://moneyforward.com/api/v1/user_asset_class_histories?from_date=2014-06-01&to_date=2014-06-01*
    
    [
      {
        "user_asset_class_history": {
          "asset_class_id": 1,
          "profit": 0,
          "rated_profit": 0,
          "rated_value": 12583787,
          "updated_at": "2014-06-01T00:00:00+09:00",
          "value": 12583787,
          "asset_class": {
            "asset_class_name": "預金・現金",
            "asset_class_type": "DEPO",
            "disp_order": 1,
            "id": 1
          }
        }
      },
      {
        "user_asset_class_history": {
          "asset_class_id": 3,
          "profit": 0,
          "rated_profit": 0,
          "rated_value": 1,
          "updated_at": "2014-06-01T00:00:00+09:00",
          "value": 1,
          "asset_class": {
            "asset_class_name": "投資信託",
            "asset_class_type": "MF",
            "disp_order": 4,
            "id": 3
          }
        }
      },
      {
        "user_asset_class_history": {
          "asset_class_id": 4,
          "profit": 96300,
          "rated_profit": 96300,
          "rated_value": 3813782,
          "updated_at": "2014-06-01T00:00:00+09:00",
          "value": 3813782,
          "asset_class": {
            "asset_class_name": "株式(現物)",
            "asset_class_type": "EQ",
            "disp_order": 2,
            "id": 4
          }
        }
      },
      {
        "user_asset_class_history": {
          "asset_class_id": 5,
          "profit": 4488476,
          "rated_profit": 4488476,
          "rated_value": 4488476,
          "updated_at": "2014-06-01T00:00:00+09:00",
          "value": 4488476,
          "asset_class": {
            "asset_class_name": "FX",
            "asset_class_type": "FX",
            "disp_order": 6,
            "id": 5
          }
        }
      },
      {
        "user_asset_class_history": {
          "asset_class_id": 6,
          "profit": 3911674,
          "rated_profit": 3911674,
          "rated_value": 3911674,
          "updated_at": "2014-06-01T00:00:00+09:00",
          "value": 3911674,
          "asset_class": {
            "asset_class_name": "先物OP",
            "asset_class_type": "DRV",
            "disp_order": 7,
            "id": 6
          }
        }
      },
      {
        "user_asset_class_history": {
          "asset_class_id": 11,
          "profit": null,
          "rated_profit": null,
          "rated_value": -4277,
          "updated_at": "2014-06-01T00:00:00+09:00",
          "value": -4277,
          "asset_class": {
            "asset_class_name": "負債",
            "asset_class_type": "LIA",
            "disp_order": 100,
            "id": 11
          }
        }
      },
      {
        "user_asset_class_history": {
          "asset_class_id": 13,
          "profit": 4928571,
          "rated_profit": 4928571,
          "rated_value": 7643731,
          "updated_at": "2014-06-01T00:00:00+09:00",
          "value": 7643731,
          "asset_class": {
            "asset_class_name": "株式(信用)",
            "asset_class_type": "MGN",
            "disp_order": 3,
            "id": 13
          }
        }
      }
    ]