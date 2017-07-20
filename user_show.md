# ユーザーの情報を得る

## 要求

### エンドポイント

```
GET https://moneyforward.com/api/v1/user
```

### パラメーター

なし

### 例

```
GET https://moneyforward.com/api/v1/user
```

## 応答の本文

### パラメーター

| 名称 | 内容 |
| ---- | --- |
| `user[hashed_id]` | ユーザーの `hashed_id` |
| `user[calc_st_day]` | 毎月の集計期間の開始日; `1` から月末までの間の数字 |
| `user[lock]` | パスワードを連続して入力に失敗した累積回数 |
| `user[lock_limit]` | パスワードロック期限; `null`: ロックされていない |
| `user[mf_registered_at]` | マネーフォワード家計簿サービス利用開始日時; ISO 8601 拡張形式 |
| `user[mf_withdrew_at]` | マネーフォワード家計簿サービス退会日時; ISO 8601 拡張形式 |
| `user[premium?]` | マネーフォワード家計簿プレミアムサービス利用状況 |
| `user[only_api_user?]` | マネーフォワード家計簿をAPI経由でのみ利用しているか |

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
