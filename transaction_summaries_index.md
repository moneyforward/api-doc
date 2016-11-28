# GET /api/v1/derived/transaction_summaries

**ある特定期間** でのカテゴリ毎の収支を取得します。
週 or 月単位で取得できます。

## Resource URL

https://moneyforward.com/api/v1/derived/transaction_summaries

## Parameters

Name | Description
----- | -----
past <br> *optional* | 遡りたい過去 <br> ※ デフォルト: `0`
period <br> *optional* | `week` or `month` <br> ※ デフォルト: `month`

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
