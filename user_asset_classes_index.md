# GET /api/v1/user_asset_classes
ユーザーの資産合計をアセットクラス別に集計して返します。

## Resrouce URL
https://moneyforward.com/api/v1/user_asset_classes

## Data definition

name | Description 
-----------|------------------------
profit | 損益
value | 評価額
rated_profit | 為替レート勘案円換算損益
rated_value | 為替レート勘案円換算評価額
updated_at | 基準日
previous_value_set[:value] | 前営業日評価額
previous_value_set[:profit] | 前営業日損益
previous_value_set[:rated_value] | 前営業日円換算評価額
previous_value_set[:rated_profit] | 前営業日円換算損益
previous_value_set[:updated_at] | 前営業日日付

## Parameters
name | Description 
-----------|------------------------
previous_date <br /> *optional* | 前営業日日付 ※未指定なら前日を採用
account_ids <br /> *optional* | 登録金融機関ID *hashed* *Array*
asset_class_ids  <br /> *optional* | アセットクラスID *Array*
asset_subclass_ids  <br /> *optional* | アセットサブクラスID *Array*

 
## Example
***
> **GET** *https://moneyforward.com/api/v1/user_asset_classes*

    [
      {
        "user_asset_class": {
          "asset_class_id": 1,
          "profit": 0,
          "rated_profit": 0,
          "rated_value": 12937088,
          "updated_at": "2013-07-22T10:54:40+09:00",
          "value": 12937088,
          "asset_class": {
            "asset_class_name": "預金・現金",
            "asset_class_type": "DEPO",
            "disp_order": 1,
            "id": 1
          },
          "previous_value_set": {
            "profit": 0,
            "rated_profit": 0,
            "rated_value": 3329192,
            "updated_at": "2014-06-20T00:00:00+09:00",
            "value": 3329192
          }
        }
      },
      {
        "user_asset_class": {
          "asset_class_id": 3,
          "profit": 0,
          "rated_profit": 0,
          "rated_value": 1,
          "updated_at": "2013-07-22T16:10:30+09:00",
          "value": 1,
          "asset_class": {
            "asset_class_name": "投資信託",
            "asset_class_type": "MF",
            "disp_order": 4,
            "id": 3
          },
          "previous_value_set": {
            "profit": 0,
            "rated_profit": 0,
            "rated_value": 3329192,
            "updated_at": "2014-06-20T00:00:00+09:00",
            "value": 3329192
          }
        }
      },
      {
        "user_asset_class": {
          "asset_class_id": 4,
          "profit": 96300,
          "rated_profit": 96300,
          "rated_value": 5528285,
          "updated_at": "2014-06-02T15:35:07+09:00",
          "value": 5528285,
          "asset_class": {
            "asset_class_name": "株式(現物)",
            "asset_class_type": "EQ",
            "disp_order": 2,
            "id": 4
          },
          "previous_value_set": {
            "profit": 90000,
            "rated_profit": 90000,
            "rated_value": 3329192,
            "updated_at": "2014-06-20T00:00:00+09:00",
            "value": 3329192
          }
        }
      },
      {
        "user_asset_class": {
          "asset_class_id": 5,
          "profit": 4946498,
          "rated_profit": 4946498,
          "rated_value": 4946498,
          "updated_at": "2014-06-02T12:59:45+09:00",
          "value": 4946498,
          "asset_class": {
            "asset_class_name": "FX",
            "asset_class_type": "FX",
            "disp_order": 6,
            "id": 5
          },
          "previous_value_set": {
            "profit": 0,
            "rated_profit": 0,
            "rated_value": 3329192,
            "updated_at": "2014-06-20T00:00:00+09:00",
            "value": 3329192
          }
        }
      },
      {
        "user_asset_class": {
          "asset_class_id": 6,
          "profit": 5227719,
          "rated_profit": 5227719,
          "rated_value": 5227719,
          "updated_at": "2014-06-02T12:59:45+09:00",
          "value": 5227719,
          "asset_class": {
            "asset_class_name": "先物OP",
            "asset_class_type": "DRV",
            "disp_order": 7,
            "id": 6
          },
          "previous_value_set": {
            "profit": 0,
            "rated_profit": 0,
            "rated_value": 3329192,
            "updated_at": "2014-06-20T00:00:00+09:00",
            "value": 3329192
          }
        }
      },
      {
        "user_asset_class": {
          "asset_class_id": 11,
          "profit": null,
          "rated_profit": null,
          "rated_value": -4277,
          "updated_at": "2014-03-27T16:02:43+09:00",
          "value": -4277,
          "asset_class": {
            "asset_class_name": "負債",
            "asset_class_type": "LIA",
            "disp_order": 100,
            "id": 11
          },
          "previous_value_set": {
            "profit": 0,
            "rated_profit": 0,
            "rated_value": 3329192,
            "updated_at": "2014-06-20T00:00:00+09:00",
            "value": 3329192
          }
        }
      },
      {
        "user_asset_class": {
          "asset_class_id": 13,
          "profit": 4271599,
          "rated_profit": 4271599,
          "rated_value": 6936389,
          "updated_at": "2014-06-02T15:35:07+09:00",
          "value": 6936389,
          "asset_class": {
            "asset_class_name": "株式(信用)",
            "asset_class_type": "MGN",
            "disp_order": 3,
            "id": 13
          },
          "previous_value_set": {
            "profit": 0,
            "rated_profit": 0,
            "rated_value": 3329192,
            "updated_at": "2014-06-20T00:00:00+09:00",
            "value": 3329192
          }
        }
      }
    ]
