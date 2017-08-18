# 中分類や通貨の全ての組み合わせごとの資産の合計を閲覧する

## 要求

### エンドポイント

```
GET https://moneyforward.com/api/v1/user_asset_summaries
```

### パラメーター

場所 | 随意性 | 名称 | 内容
---- | ---- | ---- | ---
ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで `アクセストークン` は [`access_token`](token.md) の値
クエリー | 任意; デフォルト: 要求の日の前日 | `previous_date` | 前の営業日
クエリー | 任意; デフォルト: 全て; 複数個使用可 | `account_ids[]` | 口座の `hashed_id`
クエリー | 任意; デフォルト: 全て; 複数個使用可 | `asset_class_ids[]` | 資産の大分類の `id`
クエリー | 任意; デフォルト: 全て; 複数個使用可 | `asset_subclass_ids[]` | 資産の中分類の `id`
クエリー | 任意; デフォルト: `1` | `page` | ページ番号
クエリー | 任意; デフォルト: `100` | `limit` | 1ページ当たりの最大表示件数; 最大: `500`

 
### 例

```
GET https://moneyforward.com/api/v1/user_asset_summaries?account_ids[]=LlPqfqeeCZavwPBLmUy6xg==&asset_subclass_ids[]=39
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

[GET https://moneyforward.com/api/v1/user_assets/:id](user_assets_show.md) と同じ内容が `user_asset_summaries[i]` として配列に入っている。

### 例

```
{
  "limit": 100,
  "offset": 0,
  "total_count": 1,
  "user_asset_summaries": [
    {
      "user_asset_summary": {
        "asset_class_id": 9,
        "asset_subclass_id": 39,
        "created_at": "2014-05-22T06:33:13+09:00",
        "currency": "JPY",
        "jpyrate": 1,
        "profit": 3000,
        "rated_value": 775155.8708305522,
        "rated_profit": 3000,
        "updated_at": "2014-05-22T06:33:13+09:00",
        "value": 775155.8708305522,
        "hashed_id": "EZOB3wR14WhMJDWb49ydFg==",
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
          "asset_class_name": "年金",
          "asset_class_type": "PNS",
          "disp_order": 10,
          "id": 9
        },
        "asset_subclass": {
          "asset_class_id": 9,
          "asset_subclass_name": "確定拠出年金",
          "asset_subclass_type": "KAKUTEI_PNS",
          "id": 39,
          "liquid": 70
        }
      }
    }
  ]
}
```
