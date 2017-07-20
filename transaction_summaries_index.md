# リクエスト日を含み、日曜始まりの週または月を単位とする期間の、入出金の大分類毎の収支を得る

## 要求

### エンドポイント

```
GET https://moneyforward.com/api/v1/derived/transaction_summaries
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| クエリー | 随意; デフォルト: `month` | `period` | 期間を指定する単位; `week`: 日曜始まりの週, `month`: 月 |
| クエリー | 随意; デフォルト: `0` | `past` | 上記単位で計った期間の長さ |

### 例

```
GET https://moneyforward.com/api/v1/derived/transaction_summaries?past=0&period=month
```

## 応答の本文

### 例

```
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
```

