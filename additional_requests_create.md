# 特定の口座のログインに必要な追加の入力項目を登録する

## 要求

### 必要な権限

`manage_accounts`

### エンドポイント

```
POST https://moneyforward.com/api/v1/additonal_requests
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |
| 本文 | 必須 | `additional_request[account_id]` | [口座](accounts_index.md)の `hashed_id` |

### 例

```
POST https://moneyforward.com/api/v1/additional_requests
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"

{
  "additional_request": {
    "account_id": "84dG3OLcZt_gLm66DESKzw=="
  }
}
```

## 応答の本文

### 例

```
[
  {
    "additional_request": {
      "hashed_id": "ZUwr8sW8oXjm5uThdVSZPw==",
      "message": "合言葉／秘密の質問 への記入が必要です。",
      "request_data": "子供の頃の一番の親友の名前は何ですか"
    }
  }
]
```
