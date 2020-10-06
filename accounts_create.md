# 口座を登録する

## 要求 

### 必要な権限

`manage_accounts`

### エンドポイント

```
POST https://moneyforward.com/api/v1/accounts
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |
| 本文 | 必須 | `account[service_id]` | [金融機関](services_index.md)の `id` |
| 本文 | 任意; デフォルト: 取得可能な最も古い日 | `account[aggre_start_date]` | データ取得開始日; ISO 8601 拡張形式 |
| 本文 | 必須; 金融機関に応じた数だけ | `account[service_forms_answers][i][id]` | [金融機関へのログインに必要な入力項目](services_show.md)の `id` |
| 本文 | 必須; 金融機関に応じた数だけ | `account[service_forms_answers][i][value]` | 入力項目に入力されるべき値 |

### 例

```
POST https://moneyforward.com/api/v1/accounts
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"

{
  "account": {
    "service_id": 1,
    "aggre_start_date": "2014-07-01",
    "service_forms_answers": [
      {
        "id": 1,
        "value": "99999999"
      },
      {
        "id": 2,
        "value": "password_text"
      }
    ]
  }
}
```

## 応答の本文

[GET https://moneyforward.com/api/v1/accounts/:id](accounts_show.md) と同じ
