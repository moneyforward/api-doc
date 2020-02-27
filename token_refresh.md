# アクセストークンを再び得る

一度アクセストークンの発行を受けた後、再び認可を受ける手順を踏まずにアクセストークンを再び得る。

再発行されたアクセストークンを使用すると、以前のアクセストークン `access_token` 及び `refresh_token` は無効になります(再発行されていても、使用していなければ、無効になりません)。

## 要求

### エンドポイント

```
POST /oauth/v2/token
```

### パラメーター
| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| クエリー | 必須 | `grant_type` | `refresh_token` |
| クエリー | 必須 | `refresh_token` | [アクセストークンを得た](token.md)時に応答の本文に含まれていた `refresh_token` の値 |
| クエリー | 必須 | `client_id` | クライアントソフトウェア登録時にマネーフォワード担当者がお渡ししたクライアントソフトウェア固有の文字列 |
| クエリー | 必須 | `client_secret` | クライアントソフトウェア登録時にマネーフォワード担当者がお渡ししたクライアントソフトウェアの秘密の文字列 |

### 例

```
POST https://moneyforward.com/oauth/v2/token?grant_type=refresh_token&refresh_token=1e7b4441334d4c15b2c18ae48267aae7e9661b4316a24913de664cc28b8bec96
```

## 応答の本文

### パラメーター

[アクセストークンを得る](token.md)ときと比べて、認可の詳細な情報を `id_token` の値の中にエンコードするのでなく、直接に記載している。

| 名称 | 内容 |
| ---- | --- |
| `token_type` | `bearer` |
| `access_token` | アクセストークン; APIエンドポイントのアクセスに必要な秘密の文字列 |
| `expires_in` | アクセストークンが有効な発行時からの秒数 |
| `refresh_token` | アクセストークンの有効期限が切れたときに、再び[認可を受ける](authorize.md)手順を踏まずに[アクセストークンを再び得る](refresh.md)ために必要な秘密の文字列 |
| `scope` | 認可された権限を空白でつないだもの |
| `client_id` | クライアントソフトウェア登録時にマネーフォワード担当者がお渡ししたクライアントソフトウェア固有の文字列 |
| `redirect_uri` | クライアントソフトウェアの登録時に指定された、クライアントソフトウェア上のURL |
| `client_secret` | クライアントソフトウェア登録時にマネーフォワード担当者がお渡ししたクライアントソフトウェアの秘密の文字列 |

### 例

```
{
  "token_type": "bearer",
  "access_token": "4d2cd19730a977c91ffb1f2c354fa6d28d2064213c9af39aad0afeb19b135bd8",
  "expires_in": 1209599,
  "refresh_token": "a03902af7e33048f408e3960984ae1a9a8fb909da44ad1e275d7a9d5e2454a92",
  "scope": "openid email accounts acquire_accounts manage_accounts assets transactions manage_transactions manage_sso",
  "client_id": "ff97d597c2a98367461892a497b8e710cb4618be83ff58cabd6022672f2a85eb",
  "redirect_uri": "http://localhost:1234/callback",
  "client_secret": "5d07e141ab41b2d866869ade5b315ba14dd3997d275f8968ca078f121e8b3e35"
}
```
