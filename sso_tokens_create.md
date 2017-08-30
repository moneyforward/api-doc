# ユーザーのSSOトークンを登録する

## 要求

### 必要な権限

`sso_tokens`

### エンドポイント

```
POST https://moneyforward.com/api/v1/sso_tokens
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |
| 本文 | 任意; デフォルト: `/` | `sso_tokens[redirect_path]` | リダイレクト先URI |

### 例

```
POST https://moneyforward.com/api/v1/sso_tokens
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"

{
  "sso_token": {
    "redirect_path": "/accounts"
  }
}
```

## 応答の本文

### 例

```
{
  "sso_token" {
    "token": "トークン文字列"
  }
}
```
