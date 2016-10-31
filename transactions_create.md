# POST /api/v1/transactions

入出金履歴の登録を行います。

## Resource URL

https://moneyforward.com/api/v1/transactions

## Parameters

Name | Description
-----------|------------------------
updated_at <br> *required* | 入出金日
amount <br> *required* | 金額
is_income <br> *required* | 収入: true, 支出: false
large_category_id <br> *optional* | 大項目カテゴリ
middle_category_id <br> *optional* | 中項目カテゴリ

## Example

***
> **POST** https://moneyforward.com/api/v1/transactions

    {
      "transaction" : {
        "amount" : 25000,
        "content" : null,
        "currency" : "JPY",
        "is_income" : true,
        "is_transfer" : false,
        "jpyrate" : 1.0,
        "large_category_id" : 15,
        "middle_category_id" : 62,
        "created_at" : "2016-10-28T16:20:55+09:00",
        "updated_at" : "2016-10-28T00:00:00+09:00"
      }
    }
