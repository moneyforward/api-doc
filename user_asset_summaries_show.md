# 中分類や通貨の特定の組み合わせの資産の合計を得る

## 要求

### エンドポイント

```
GET https://moneyforward.com/api/v1/user_asset_summaries/:id
```

### パラメーター

場所 | 随意性 | 名称 | 内容
---- | ---- | ---- | ---
パス | 必須 | `id` | 資産合計項目の `hashed_id`
ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで `アクセストークン` は [`access_token`](token.md) の値
クエリー | 任意; デフォルト: 要求の日の前日 | `previous_date` | 前の営業日; ISO 8601 拡張形式
 
### 例

```
GET https://moneyforward.com/api/v1/user_asset_summaries/BR5-TCLSc2eZ-gf5Wxa4lA==
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

名称 | 内容
---- | ---
`user_asset_summary[value]` | 評価額
`user_asset_summary[profit]` | 損益
`user_asset_summary[rated_value]` | 円換算評価額
`user_asset_summary[rated_profit]` | 円換算損益
`user_asset_summary[previous_value_set][value]` | 前の営業日の評価額
`user_asset_summary[previous_value_set][profit]` | 前の営業日の損益
`user_asset_summary[previous_value_set][rated_value]` | 前の営業日の円換算評価額
`user_asset_summary[previous_value_set][rated_profit]` | 前の営業日の円換算損益
`user_asset_summary[previous_value_set][updated_at]` | 前の営業日; ISO 8601 拡張形式

### 例

```
 {
   "user_asset_summary": {
     "asset_class_id": 3,
     "asset_subclass_id": 12,
     "created_at": "2014-05-22T06:33:13+09:00",
     "currency": "JPY",
     "jpyrate": 1,
     "rated_value": 389024.721519843,
     "updated_at": "2014-05-22T06:33:13+09:00",
     "value": 389024.721519843,
     "hashed_id": "BR5-TCLSc2eZ-gf5Wxa4lA==",
     "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
     "previous_value_set": {
       "profit": 32100,
       "rated_profit": 32100,
       "rated_value": 1849530,
       "updated_at": "2014-06-20T00:00:00+09:00",
       "value": 1849530
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
       "id": 12,
       "liquid": 85
     }
   }
 }
```
