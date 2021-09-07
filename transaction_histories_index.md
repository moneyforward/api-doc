# 要求の日を含む期間の収支を、日曜始まりの週または月ごとに得る

## 要求

### 必要な権限

`transactions`

### エンドポイント

```
GET https://moneyforward.com/api/v1/derived/transaction_histories
```

### パラメーター

| 場所     | 随意性                    | 名称                                    | 内容                                                                                                                                                             |
| -------- | ------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ヘッダー | 必須                      | `Authorization` または `X-MFOAuthToken` | `` Bearer `アクセストークン`  ``; ここで `` `アクセストークン` `` は [`access_token`](token.md) の値                                                             |
| クエリー | 任意; デフォルト: `month` | `period`                                | 期間の単位; `week`: 日曜始まりの週, `month`: 月                                                                                                                  |
| クエリー | 任意; デフォルト: `0`     | `past`                                  | 情報を得る期間の長さ; 上記単位で計る; [`GET https://moneyforward.com/api/v1/derived/transaction_summaries`](transaction_summaries_index.md) の場合と意味が異なる |

### 例

```
GET https://moneyforward.com/api/v1/derived/transaction_histories?past=3&period=week
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### 例

```
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
```
