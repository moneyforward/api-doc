# ユーザーの登録状況を得る

## 要求

### 必要な権限

なし

### エンドポイント

```
GET https://moneyforward.com/api/v1/user
```

### パラメーター

| 場所     | 随意性 | 名称                                    | 内容                                                                                                 |
| -------- | ------ | --------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| ヘッダー | 必須   | `Authorization` または `X-MFOAuthToken` | `` Bearer `アクセストークン`  ``; ここで `` `アクセストークン` `` は [`access_token`](token.md) の値 |

### 例

```
GET https://moneyforward.com/api/v1/user
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

| 名称                     | 内容                                                                                                 |
| ------------------------ | ---------------------------------------------------------------------------------------------------- |
| `user[hashed_id]`        | ユーザーの `hashed_id`                                                                               |
| `user[calc_st_day]`      | 毎月の集計期間の開始日; `1` から `31` までの間の整数                                                 |
| `user[lock]`             | パスワードを連続して入力に失敗した累積回数; `0` 以上の整数                                           |
| `user[lock_limit]`       | パスワードロック期限; ISO 8601 拡張形式、もしくは `null`: ロックされていない                         |
| `user[mf_registered_at]` | マネーフォワード家計簿サービス利用開始日時; ISO 8601 拡張形式                                        |
| `user[mf_withdrew_at]`   | マネーフォワード家計簿サービス退会日時; ISO 8601 拡張形式、もしくは `null`: 退会していない           |
| `user[premium?]`         | マネーフォワード家計簿プレミアムサービス利用状況; `true`: 利用している, `false`: 利用していない      |
| `user[only_api_user?]`   | マネーフォワード家計簿を API 経由でのみ利用しているか; `true`: そうしている, `false`: そうしていない |

### 例

```
{
  "user": {
    "calc_st_day": 25,
    "lock": 0,
    "lock_limit": null,
    "mf_registered_at": "2014-04-19T17:33:36+09:00",
    "mf_withdrew_at": null,
    "hashed_id": "v2lhShEuROMSG9PfhvvFMA==",
    "premium?": false,
    "only_api_user?": false
  }
}
```
