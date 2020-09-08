# 口座の一時停止を行う

指定のアグリ口座をの更新を一時停止する。

一時停止を解除するには、[特定の口座内容を書き換える](accounts_update.md)を利用する。
認証情報が一時的に削除されているため、新規登録と同じ条件で認証情報を指定し更新しなければいけない。

## 要求

### 必要な権限

`manage_accounts`

### エンドポイント

```
PUT /api/v1/accounts/:id/suspend
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |
| パス | 必須 | `id` | [口座](accounts_index.md)の `hashed_id` |

### 例

```
PUT https://moneyforward.com/api/v1/accounts/YvfkvgGE_Qigjy7fiuFbAQ/suspend
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

なし