# GET /api/v1/transactions
ユーザーの入出金履歴を返す  
from_date, to_date パラメーターを付けない場合は、
一ヶ月前以降のデータを返します

## Resrouce URL
https://moneyforward.com/api/v1/transactions

## Data definition

name | Description 
-----------|------------------------
amouont | 金額(出金はマイナス)
content | 明細
currency | 通貨
is_income | 収入: true, 支出: false
is_transfer | 振替: true
jpyrate | 為替レート
large_category_id | 大項目ID
middle_category_id | 中項目ID
created_at | マネーフォワードへのデータ登録日
updated_at | 記帳日
hashed_account_id | 入出金元の金融機関ID
hashed_sub_account_id | 入出金元の補助金融機関ID

## Parameters

name | Description 
-----------|------------------------
account_ids <br /> *optional* | 登録金融機関ID *hashed* *Array*
sub_account_ids <br /> *optional* | 登録補助金融機関ID *hashed* *Array*
large_category_ids <br /> *optional* | 大項目ID *Array*
middle_category_idsd <br /> *optional* | 中項目ID *Array*
from_date <br /> *optional* | 履歴検索開始日。デフォルトは１ヶ月前
to_date <br /> *optional* | 履歴検索終了日。デフォルトはnull
page  <br /> *optional* | ページ番号
limit <br /> *optional* | 1ページあたりのエレメント数.デフォルト100、最大500

 
## Example
***
> **GET** *https://moneyforward.com/api/v1/transactions?sub_account_ids[]=dyJaw7FlOG41c1C-LKndFA==&middle_category_ids[]=32*

    {
      "limit": 100,
      "offset": 0,
      "total_count": 1,
      "transactions": [
        {
          "transaction": {
            "amount": -1,
            "content": "地方税",
            "created_at": "2014-08-11T16:20:59+09:00",
            "currency": "JPY",
            "is_income": false,
            "is_transfer": false,
            "jpyrate": 1,
            "large_category_id": 9,
            "memo": null,
            "middle_category_id": 32,
            "updated_at": "2014-07-20T00:00:00+09:00",
            "hashed_id": "dYDn1yKM37qFejzmwbf2KA==",
            "hashed_account_id": "E8NWqTw4e3TnXffLl50f-Q==",
            "hashed_sub_account_id": "dyJaw7FlOG41c1C-LKndFA==",
            "account": {
              "account_uid_hidden": "nkw***",
              "created_at": "2014-08-11T16:20:57+09:00",
              "disp_name": null,
              "last_aggregated_at": "2014-08-11T16:20:59+09:00",
              "last_succeeded_at": "08/11 16:21",
              "memo": null,
              "message": null,
              "msg_flag": 0,
              "msg_time": null,
              "next_aggregate_at": "2014-08-12T16:11:40+09:00",
              "service_category_id": 2,
              "service_id": 2,
              "status": 0
            },
            "sub_account": {
              "created_at": "2014-08-11T16:20:59+09:00",
              "disp_name": null,
              "service_category_id": 2,
              "sub_name": "",
              "sub_number": "",
              "sub_type": "代表口座 - 円普通"
            },
            "large_category": {
              "disp_order": 18,
              "id": 9,
              "income": -1,
              "name": "税・社会保障"
            },
            "middle_category": {
              "disp_order": 1,
              "id": 32,
              "large_category_id": 9,
              "name": "所得税・住民税"
            }
          }
        }
      ]
    }
