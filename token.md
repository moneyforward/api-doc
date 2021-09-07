# アクセストークンを得る

[認可を得た](authorize.md)ら、それに引き続いて、API へのアクセスに必要なアクセストークンを得る。

## 要求

### エンドポイント

```
POST /oauth/v2/token
```

### パラメーター

| 場所                              | 随意性 | 名称            | 内容                                                                                                     |
| --------------------------------- | ------ | --------------- | -------------------------------------------------------------------------------------------------------- |
| 本文                              | 必須   | `grant_type`    | `authorization_code`                                                                                     |
| 本文または Authorization ヘッダー | 必須   | `client_id`     | クライアントソフトウェア登録時にマネーフォワード担当者がお渡ししたクライアントソフトウェア固有の文字列   |
| 本文または Authorization ヘッダー | 必須   | `client_secret` | クライアントソフトウェア登録時にマネーフォワード担当者がお渡ししたクライアントソフトウェアの秘密の文字列 |
| 本文                              | 必須   | `redirect_uri`  | クライアントソフトウェアの登録時に指定された、クライアントソフトウェア上の URL                           |
| 本文                              | 必須   | `code`          | [認可を得た](authorize.md)時に応答の本文に含まれていた `code` の値                                       |

### 例

```
POST http://moneyforward.com/oauth/v2/token
```

## 応答の本文

### パラメーター

| 名称            | 内容                                                                                                                                                           |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `token_type`    | `bearer`                                                                                                                                                       |
| `access_token`  | アクセストークン; API エンドポイントのアクセスに必要な秘密の文字列                                                                                             |
| `expires_in`    | アクセストークンが有効な発行時からの秒数                                                                                                                       |
| `refresh_token` | アクセストークンの有効期限が切れたときに、再び[認可を受ける](authorize.md)手順を踏まずに[アクセストークンを再び得る](token_refresh.md)ために必要な秘密の文字列 |
| `scope`         | 認可された権限を空白でつないだもの                                                                                                                             |
| `id_token`      | 認可についての情報を JSON Web Signature (JWS) の Compact Serialization 形式でエンコードしたもの                                                                |

`id_token` の値のペイロード部分をデコードすることによって、さらに次のようなパラメーターを得ることが出来る。これらはクレームと呼ばれる。時間は、Unix エポックを起点として、秒単位で表されている。

| 名称        | 内容                                                                           |
| ----------- | ------------------------------------------------------------------------------ |
| `iss`       | Issuer; アクセストークンの発行元を表す文字列や URL; `https://moneyforward.com` |
| `sub`       | Subject; ユーザーに固有な文字列                                                |
| `aud`       | Audience; 要求の `client_id` の値                                              |
| `exp`       | Expiration time; `id_token` の有効期限                                         |
| `iat`       | Issued at; `id_token` を発行した時間                                           |
| `auth_time` | ユーザーを認証した時間                                                         |

### 例

```
{
  "token_type": "bearer",
  "access_token": "0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c",
  "expires_in": 1209599,
  "refresh_token": "1e7b4441334d4c15b2c18ae48267aae7e9661b4316a24913de664cc28b8bec96",
  "scope": "openid email accounts acquire_accounts manage_accounts assets transactions manage_transactions manage_sso",
  "id_token": "ZJQ0VvbHJxNXJLMW80OTdrQ2pSVXhEQmlnSUeyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImtpZCI6IldsNURLaGNVZ3M3bUtGOXEixQ.eyJpc3MiOiJodHRwczovL2iOiIzZWY1OWRjZmE4ZDAwMjQ5ZjXhMzJlMmJmMDE1O1vbmV5Zm9yd2XyZC5jb20iLCJzdWITIxNmMwNDZiYjc4NzYzZDBjOWRlZGIyOTYzY2I2ZTEwYjA0IiwiYXVkIjoiZmY5N2Q1OTdjMmE5ODM2NzQ2MTg5MmE0OTdiOGU3MTBjYjQ2MThiZTgzZmY1OGNhYmQ2MDIyNjcyZjJhODVlYiIsImV4cCI6MTUwMDg2ODQyOSwiaWX0IjoxNTAwODY4MzA5LCJhdXRoX3RpbWUiOjE1MDA4NjgzMDl9.tuzsRx_Zkop4yeSHtKL7KbCQZiBtloCTnnKEXol9X9JwY4DWCtEUyxSUSNZ5OnmUrxMv1U0xStHRnwdP3ViCEi4Lx8X7AuY4BmvlowoT020SDZXN0HowxB7I6UNs6eenGU1DL4kIt4VcAjBZDKTkoC0mWOAE1Z32_rj7rW_Krdw"
}
```

```
{
  "iss": "https://moneyforward.com",
  "sub": "3ef59dcfa8d002edb2963cb6e10b0449f1a32e2bf0159216c046bb78763d0c9d",
  "aud": "ff97d597c2a98367461892a497b8e710cb4618be83ff58cabd6022672f2a85eb",
  "exp": 1500868429,
  "iat": 1500868309,
  "auth_time": 1500868309
}
```
