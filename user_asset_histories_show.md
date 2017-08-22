# 特定の資産の履歴を得る

## 要求

### 必要な権限

`assets`

### エンドポイント

```
GET https://moneyforward.com/api/v1/user_asset_histories/:id
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| パス | 必須 | `id` | 資産の履歴の `hashed_id` |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで `アクセストークン` は [`access_token`](token.md) の値 |
| クエリー | 任意; デフォルト: 要求の日の前日 | `previous_date` | 前の営業日; ISO 8601 拡張形式 |
 
### 例

```
GET https://moneyforward.com/api/v1/user_asset_histories/vpxDzM6STgFT4Br7pFTzVQ==
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

| 名称 | 内容 |
| ---- | --- |
| `user_asset_history[code]` | 株式銘柄コード等 |
| `user_asset_history[cost]` | 現在未使用 |
| `user_asset_history[entried_at]` | 取得日; ISO 8601 拡張形式; 特定できなければ `null` |
| `user_asset_history[entried_price]` | 取得価格 |
| `user_asset_history[expire_at]` | ポイント等の場合の有効期限日; ISO 8601 拡張形式; 特定できなければ `null` |
| `user_asset_history[jpy_rate]` | 円換算レート |
| `user_asset_history[name]` | 名称 |
| `user_asset_history[profit]` | 損益 |
| `user_asset_history[qty]` | 数量 |
| `user_asset_history[value]` | 評価額またはポイント数 |
| `user_asset_history[rated_value]` | 円換算評価額 |
| `user_asset_history[rated_profit]` | 円換算損益 |
| `user_asset_history[updated_at]` | 基準日; ISO 8601 拡張形式 |
| `user_asset_history[hashed_original_user_asset_id]` | 履歴作成の元となった資産の `hashed_id` |
| `user_asset_history[previous_value_set][rated_value]` | 前の営業日の円換算評価額 |
| `user_asset_history[previous_value_set][rated_profit]` | 前の営業日の円換算損益 |
| `user_asset_history[previous_value_set][updated_at]` | 前の営業日; ISO 8601 拡張形式 |

### 例

```
{
  "user_asset_history": {
    "asset_class_id": 3,
    "asset_subclass_id": 12,
    "code": "",
    "cost": 0,
    "currency": "JPY",
    "current_price": 389024.721519843,
    "entried_at": null,
    "entried_price": 300000,
    "expire_at": null,
    "jpyrate": 1,
    "name": "【デモ】マネフォファンド",
    "profit": 89024.72151984298,
    "qty": 1,
    "rated_profit": 89024.72151984298,
    "rated_value": 389024.721519843,
    "updated_at": "2014-05-22T06:33:13+09:00",
    "value": 389024.721519843,
    "hashed_id": "vpxDzM6STgFT4Br7pFTzVQ==",
    "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
    "hashed_original_user_asset_id": "2bdgEA3TcaIPREBaNKdjvw==",
    "previous_value_set": {
        "profit": 80934.72151984298,
        "rated_profit": 383024.721519843,
        "rated_value": 379024.721519843,
        "updated_at": "2014-06-20T00:00:00+09:00",
        "value": 379024.721519843
    },
    "account": {
      "account_uid_hidden": "dem*",
      "created_at": "2014-04-19T17:33:37+09:00",
      "disp_name": null,
      "last_aggregated_at": "2014-05-22T06:33:13+09:00",
      "last_succeeded_at": "05/22 06:33",
      "memo": null,
      "message": null,
      "msg_flag": 0,
      "msg_time": null,
      "next_aggregate_at": "2014-05-25T02:27:08+09:00",
      "service_category_id": 1,
      "service_id": 1,
      "status": 2,
      "service": {
        "category_name": "銀行",
        "category_type": "BANK",
        "code": "0005",
        "description": "<li>口座番号ではなくオンラインバンキング用のログイン情報となります。オンラインバンキングの手続きは各金融機関へお問い合わせ下さい。</li><li>登録後、「IDとパスワードをお確かめ下さい」というメッセージが表示された場合、一度本サイトにログイン出来るかのご確認をお願いします。</li>",
        "id": 1,
        "login_url": "https://entry11.bk.mufg.jp/ibg/dfw/APLIN/loginib/login?_TRANID=AA000_001",
        "service_name": "三菱東京UFJ銀行",
        "service_type": "B_MUFG",
        "yomigana": "ミツビシトウキョウユーエフジェイギンコウ"
      }
    }
  }
}
```
