# 特定の口座連携を解除する

## 要求

### 必要な権限

`manage_accounts`

### エンドポイント

```
DELETE https://moneyforward.com/api/v1/accounts/:id
```

### パラメーター

| 場所     | 随意性 | 名称                                    | 内容                                                                                                 |
| -------- | ------ | --------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| ヘッダー | 必須   | `Authorization` または `X-MFOAuthToken` | `` Bearer `アクセストークン`  ``; ここで `` `アクセストークン` `` は [`access_token`](token.md) の値 |
| パス     | 必須   | `id`                                    | [口座](accounts_index.md)の `hashed_id`                                                              |

### 例

```
DELETE https://moneyforward.com/api/v1/accounts/e2RPphY9_-bdYZ1PBLMmjg==
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

なし
