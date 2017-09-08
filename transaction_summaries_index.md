# 日曜始まりの週または月の収支を、資産の分類ごとに得る

## 要求

### 必要な権限

`transactions`

### エンドポイント

```
GET https://moneyforward.com/api/v1/derived/transaction_summaries
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |
| クエリー | 任意; デフォルト: `month` | `period` | 期間の単位; `week`: 日曜始まりの週, `month`: 月 |
| クエリー | 任意; デフォルト: `0` | `past` | 情報を得る期間がどれだけ過去か; 上記単位で計る; [`GET https://moneyforward.com/api/v1/derived/transaction_histories`](transaction_histories_index.md) の場合と意味が異なる |
| クエリー | 任意; デフォルト: `large` | `category_size` | 集計する分類の大きさ; `large`: 大項目, `middle`: 中項目 |

### 例

```
GET https://moneyforward.com/api/v1/derived/transaction_summaries?past=0&period=month&category_size=large
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### 例

```
{
  "transaction_summaries": {
    "from_date": "2016-10-01",
    "to_date": "2016-10-31",
    "category_size": "large_category",
    "income": {
      "amount": 2000,
      "currency": "JPY"
    },
    "expense": {
      "amount": 2980,
      "currency": "JPY"
    },
    "category_summaries": [
      {
        "large_category_id": 1,
        "name": "収入",
        "amount": 1000,
        "currency": "JPY"
      },
      {
        "large_category_id": 3,
        "name": "現金・カード",
        "amount": 1980,
        "currency": "JPY"
      }
    ]
  }
}
```

