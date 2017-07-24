# 特定の口座の登録内容を書き換える

## 要求

### エンドポイント

```
PUT https://moneyforward.com/api/v1/accounts/:id
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで `アクセストークン` は [`access_token`](token.md) の値 |
| パス | 必須 | `id` | [口座](accounts_index.md)の `hashed_id` |
| 本文 | 随意; デフォルト: なし | `account[service_form_answers][i][id]` | [金融機関のウェブサイト上でログインに必要な入力項目](services_show.md)の `id` |
| 本文 | 随意; デフォルト: なし | `account[service_form_answers][i][value]` | 入力項目に入力されるべき値; 空だと更新しない |

### 例

```
PUT https://moneyforward.com/api/v1/accounts/e2RPphY9_-bdYZ1PBLMmjg==
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"

{
  "account": {
    "service_forms_answers": [
      {
        "id": 1,
        "value": "11111111"
      },
      {
        "id": 2,
        "value": "password_edit"
      }
    ]
  }
}
```

## 応答の本文

https://github.com/moneyforward/api-doc/blob/master/accounts_show.md と同じ
