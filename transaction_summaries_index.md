# GET /api/v1/derived/transaction_summaries

指定された過去から現在までの期間のカテゴリ毎の収支を取得します。期間は週または月の倍数で指定します。

## Resource URL

https://moneyforward.com/api/v1/derived/transaction_summaries

## Parameters

Name | Description
----- | -----
period <br> *optional* | 期間を指定する単位。`week` または `month` 。デフォルト: `month`。
past <br> *optional* | 上記単位で計った期間の長さ。 デフォルト: `0`。

## Example

今月のカテゴリ毎の収支データを取得

> **GET** *https://moneyforward.com/api/v1/derived/transaction_summaries?past=0&period=month*

    {
      "transaction_summaries" : {
        "from_date" : "2016-10-01",
        "to_date" : "2016-10-31",
        "income" : {
          "amount" : 2000,
          "currency" : "JPY"
        },
        "expense" : {
          "amount" : 2980,
          "currency" : "JPY"
        },
        "category_summaries" : [
          {
            "large_category_id" : 1,
            "name" : "収入",
            "amount" : 1000,
            "currency" : "JPY"
          },
          {
            "large_category_id" : 3,
            "name" : "現金・カード",
            "amount" : 1980,
            "currency" : "JPY"
          }
        ]
      }
    }
