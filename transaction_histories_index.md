# GET /api/v1/derived/transaction_histories

指定された過去から現在までの期間の収支履歴を取得します。期間は週または月の倍数で指定します。

## Resource URL

https://moneyforward.com/api/v1/derived/transaction_histories

## Parameters

Name | Description
----- | -----
period <br> *optional* | 期間を指定する単位。`week` または `month` 。デフォルト: `month`。
past <br> *optional* | 上記単位で計った期間の長さ。 デフォルト: `0`。

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
