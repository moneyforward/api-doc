# GET /api/v1/derived/transaction_summaries

指定された期間まで遡り現在からその期間までの収支履歴を取得します。
週 or 月単位で取得できます。

## Resource URL

https://moneyforward.com/api/v1/derived/transaction_summaries

## Parameters

Name | Description
----- | -----
past <br> *optional* | 遡りたい過去 <br> ※ デフォルト: `0`
period <br> *optional* | `week` or `month` <br> ※ デフォルト: `month`

## Example

過去3週間の収支履歴を取得

> **GET** *https://moneyforward.com/api/v1/derived/transaction_histories?past=3&period=week*

    {
      "transaction_histories" : [
        {
          "from_date" : "2016-10-30",
          "income" : {
            "amount" : 2000,
            "currency" : "JPY"
          },
          "expense" : {
            "amount" : 1000,
            "currency" : "JPY"
          }
        },
        {
          "from_date" : "2016-10-23",
          "income" : {
            "amount" : 0,
            "currency" : "JPY"
          },
          "expense" : {
            "amount" : 1980,
            "currency" : "JPY"
          }
        },
        {
          "from_date" : "2016-10-16",
          "income" : {
            "amount" : 0,
            "currency" : "JPY"
          },
          "expense" : {
            "amount" : 5600,
            "currency" : "JPY"
          }
        }
      ]
    }
