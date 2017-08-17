# 全ての資産の履歴を得る

## 要求

### エンドポイント

```
GET https://moneyforward.com/api/v1/user_asset_histories
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで `アクセストークン` は [`access_token`](token.md) の値 |
| クエリー | 任意; デフォルト: , 複数個使用可 | `account_ids[]` | 口座の `hashed_id` |
| クエリー | 任意; デフォルト: , 複数個使用可 | `original_user_asset_ids[]` | 資産の `hashed_id` |
| クエリー | 任意; デフォルト: , 複数個使用可 | `asset_class_ids[]` | 資産の大分類の `id` |
| クエリー | 任意; デフォルト: , 複数個使用可 | `asset_subclass_ids[]` | 資産の中分類の `id` |
| クエリー | 任意; デフォルト: , 複数個使用可 | `target_dates[]` | 期準日; ISO 8601 拡張形式; `from_date`, `to_date` より優先 |
| クエリー | 任意; デフォルト: 要求の日の前日 | `from_date` | 最古基準日; ISO 8601 拡張形式 |
| クエリー | 任意; デフォルト: 要求の日の前日 | `to_date` | 最新基準日; ISO 8601 拡張形式 |
| クエリー | 任意; デフォルト: `1` | `page` | ページ番号 |
| クエリー | 任意; デフォルト: `100` | `limit` | 1ページ当たりの最大表示件数; 最大: `500` |

### 例
 
```
GET https://moneyforward.com/api/v1/user_asset_histories?account_ids[]=LlPqfqeeCZavwPBLmUy6xg==&from_date=2014-5-22&to_date=2014-05-23
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

[GET https://moneyforward.com/api/v1/user_asset_histories/:id](user_asset_histories_show.md) の内容から一部を欠いたものが `user_asset_histories[i]` として配列に入っている。

```
{
  "limit": 100,
  "offset": 0,
  "total_count": 6,
  "user_asset_histories": [
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
        "updated_at": "2014-05-23T00:00:00+09:00",
        "value": 389024.721519843,
        "hashed_id": "2bdgEA3TcaIPREBaNKdjvw==",
        "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
        "hashed_original_user_asset_id": "vpxDzM6STgFT4Br7pFTzVQ==",
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
    },
    {
      "user_asset_history": {
        "asset_class_id": 4,
        "asset_subclass_id": 14,
        "code": "",
        "cost": 0,
        "currency": "JPY",
        "current_price": 424941.7055783825,
        "entried_at": null,
        "entried_price": 300000,
        "jpyrate": 1,
        "name": "【デモ】マネフォ株式",
        "profit": 124941.70557838248,
        "qty": 1,
        "updated_at": "2014-05-23T00:00:00+09:00",
        "value": 424941.7055783825,
        "hashed_id": "izURycZ9tGe3ffo6dkfZJw==",
        "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
        "hashed_original_user_asset_id": "3H3ZDVJ7RseoDC8LBfanvA==",
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
    },
    {
      "user_asset_history": {
        "asset_class_id": 9,
        "asset_subclass_id": 39,
        "code": "",
        "cost": 0,
        "currency": "JPY",
        "current_price": 775155.8708305522,
        "entried_at": null,
        "entried_price": 500000,
        "expire_at": null,            
        "jpyrate": 1,
        "name": "【デモ】マネフォファンド(確定拠出年金専用)",
        "profit": 275155.8708305522,
        "qty": 1,
        "updated_at": "2014-05-23T00:00:00+09:00",
        "value": 775155.8708305522,
        "hashed_id": "kZjneptIgNgzC4Pc4TPPpg==",
        "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
        "hashed_original_user_asset_id": "eMPREQm-zEmfZw_aWfrCnQ==",
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
    },
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
        "updated_at": "2014-05-22T00:00:00+09:00",
        "value": 389024.721519843,
        "hashed_id": "8ewSMICPAGhG3f3asNrptA==",
        "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
        "hashed_original_user_asset_id": "vpxDzM6STgFT4Br7pFTzVQ==",
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
    },
    {
      "user_asset_history": {
        "asset_class_id": 4,
        "asset_subclass_id": 14,
        "code": "",
        "cost": 0,
        "currency": "JPY",
        "current_price": 424941.7055783825,
        "entried_at": null,
        "entried_price": 300000,
        "expire_at": null,            
        "jpyrate": 1,
        "name": "【デモ】マネフォ株式",
        "profit": 124941.70557838248,
        "qty": 1,
        "updated_at": "2014-05-22T00:00:00+09:00",
        "value": 424941.7055783825,
        "hashed_id": "PK1jeBjDozr8B0NcD3LY3w==",
        "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
        "hashed_original_user_asset_id": "3H3ZDVJ7RseoDC8LBfanvA==",
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
    },
    {
      "user_asset_history": {
        "asset_class_id": 9,
        "asset_subclass_id": 39,
        "code": "",
        "cost": 0,
        "currency": "JPY",
        "current_price": 775155.8708305522,
        "entried_at": null,
        "entried_price": 500000,
        "expire_at": null,
        "jpyrate": 1,
        "name": "【デモ】マネフォファンド(確定拠出年金専用)",
        "profit": 275155.8708305522,
        "qty": 1,
        "updated_at": "2014-05-22T00:00:00+09:00",
        "value": 775155.8708305522,
        "hashed_id": "PcvM-sx0UdCq9sDPG6N_WQ==",
        "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
        "hashed_original_user_asset_id": "eMPREQm-zEmfZw_aWfrCnQ==",
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
  ]
}
```
