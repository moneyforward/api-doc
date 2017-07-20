# ユーザーのSSOトークンを取得する

## 要求

### エンドポイント

```
POST https://moneyforward.com/api/v1/sso_tokens
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| 本文 | 随意; デフォルト: `/` | `sso_tokens[redirect_path]` | リダイレクト先URI |

### 例

```
POST https://moneyforward.com/api/v1/sso_tokens

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
