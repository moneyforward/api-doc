# 入出金項目を登録する

## 要求

### 必要な権限

`manage_transactions`

### エンドポイント

```
POST https://moneyforward.com/api/v1/transactions
```

### パラメーター

| 場所     | 随意性                         | 名称                                    | 内容                                                                                                                                                                |
| -------- | ------------------------------ | --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ヘッダー | 必須                           | `Authorization` または `X-MFOAuthToken` | `` Bearer `アクセストークン`  ``; ここで `` `アクセストークン` `` は [`access_token`](token.md) の値                                                                |
| 本文     | 必須                           | `account_id`                            | [入金元または出金先の財布口座](accounts_index.md)の `hashed_id`; 財布口座の場合には、口座とサブアカウントが 1 対 1 対応している; 自動連携している口座は指定出来ない |
| 本文     | 必須                           | `is_income`                             | `1`: 収入, `true`: 収入, `0`: 支出, `false`: 支出                                                                                                                   |
| 本文     | 必須                           | `amount`                                | 金額; 入出金に関わらず 0 または正の整数                                                                                                                             |
| 本文     | 任意; デフォルト: 要求の日     | `updated_at`                            | 入出金日; `YY/MM/DD` 形式                                                                                                                                           |
| 本文     | 任意; デフォルト: 空文字列     | `content`                               | 入出金内容を記す文字列; 最大 65,535byte                                                                                                                             |
| 本文     | 任意; デフォルト: `0` (未設定) | `large_category_id`                     | [入出金の大分類](transaction_categories_index.md)の `id`                                                                                                            |
| 本文     | 任意; デフォルト: `0` (未設定) | `middle_category_id`                    | [入出金の中分類](transaction_categories_index.md)の `id`                                                                                                            |

### 例

```
POST https://moneyforward.com/api/v1/transactions
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"

{
  "account_id": "c6f7fTZ_BfttQZ2fBg2eTQ",
  "is_income": true,
  "amount": 1234,
  "updated_at": "2017/01/31",
  "content": "labour",
  "large_category_id": 4,
  "middle_category_id": 11
}
```

## 応答の本文

[GET https://moneyforward.com/api/v1/transactions](transactions_index.md) の中の 1 件分の情報と同じ
