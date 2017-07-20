# ユーザーの認可情報を得る

## 要求

### エンドポイント

```
GET https://moneyforward.com/oauth/userinfo
```

または

```
POST https://moneyforward.com/oauth/userinfo
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ``` |


電子メールアドレス付き認可情報の取得|GET または POST|/oauth/userinfo |`openid email`        |

### 例

```
GET https://moneyforward.com/oauth/userinfo
```

## 応答の本文

### パラメーター
