# 全ての資産を得る

## 要求

### エンドポイント

```
GET https://moneyforward.com/api/v1/user_assets
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| パス | 随意; デフォルト: 要求の日の前日 | `previous_date` | 前の営業日; ISO 8601 拡張形式 |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで `アクセストークン` は [`access_token`](token.md) の値 |
| クエリー | 随意; デフォルト: 全て; 複数個使用可 | `account_ids[]` | 口座の `hashed_id` |
| クエリー | 随意; デフォルト: 全て; 複数個使用可 | `asset_class_ids[]` | 資産の大分類の `id` |
| クエリー | 随意; デフォルト: 全て; 複数個使用可 | `asset_subclass_ids[]` | 資産の中分類の `id` |
| クエリー | 随意; デフォルト: `1` | `page` | ページ番号 |
| クエリー | 随意; デフォルト: `100` | `limit` | 1ページ当たりの最大表示件数; 最大: `500` |
 
### 例

```
GET https://moneyforward.com/api/v1/user_assets?account_ids[]=LlPqfqeeCZavwPBLmUy6xg==&asset_class_ids[]=3
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

[GET https://moneyforward.com/api/v1/user_assets/:id](user_assets_show.md) と同じ内容が `user_assets[i]` として配列に入っている。

### 例

```
{
  "limit": 100,
  "offset": 0,
  "total_count": 1,
  "user_assets": [
    {
      "user_asset": {
        "asset_class_id": 3,
        "asset_subclass_id": 12,
        "code": "",
        "cost": 0,
        "created_at": "2014-05-22T06:33:13+09:00",
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
        "hashed_sub_account_id": "fkwoFjgrCZamqJEEdUy8lo==",
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
          "service_category_id": 2,
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
        },
        "sub_account": {
          "service_category_id" : 2,
          "sub_name" : "本店",
          "sub_type" : "普通",
          "sub_number" : "0999999",
          "disp_name" : null,
          "created_at" : "2016-10-20T15:57:24+09:00"
        },
        "asset_class": {
          "asset_class_name": "投資信託",
          "asset_class_type": "MF",
          "disp_order": 4,
          "id": 3
        },
        "asset_subclass": {
          "asset_class_id": 3,
          "asset_subclass_name": "投資信託",
          "asset_subclass_type": "MUTUAL_FUND",
          "disp_order": 1,
          "id": 12,
          "liquid": 85
        }
      }
    }
  ]
}
```
