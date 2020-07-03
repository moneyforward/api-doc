# 新着明細を取得する
**このAPIは専用基盤をご契約のお客様のみご利用いただけます。**

## 要求

### 必要な権限

`transactions`

### エンドポイント

```
GET https://moneyforward.com/api/v1/transactions/recent
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| --- | --- | --- | --- |
| ヘッダー | 必須 | Authorization または X-MFOAuthToken | Bearer `アクセストークン`;  |
| クエリ | 任意; デフォルト: 要求日 | created_after | 取得対象開始日時 |
| クエリー | 任意; デフォルト: 全て | `is_target` | `1`: 計算対象, `0`: 計算対象外 |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `account_ids[]` | 口座の `hashed_id` |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `sub_account_ids[]` | サブアカウントの `hashed_id` |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `large_category_ids[]` | 入出金の大分類の `id` |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `middle_category_ids[]` | 入出金の中分類の `id` |
| クエリー | 任意; デフォルト: `1` | `page` | ページ番号 |
| クエリー | 任意; デフォルト: `100` | `limit` | 1ページ当たりの最大表示件数, 最大: `500` |

### 例

```
GET https://moneyforward.com/api/v1/transactions/recent?sub_account_ids[]=3aJadZHjTJDdj-J0V2Oawg&sub_account_ids[]=dyJaw7FlOG41c1C-LKndFA==&middle_category_ids[]=32
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文
### パラメーター

[全ての入出金記録を得る](https://github.com/moneyforward/api-doc/blob/master/transactions_index.md#%E3%83%91%E3%83%A9%E3%83%A1%E3%83%BC%E3%82%BF%E3%83%BC-1)と同様

### 例

```
{
    "created_after": "2020-06-25",
    "limit": 100,
    "offset": 0,
    "total_count": ,
    "transactions": [
        {
            "transaction": {
                "is_transfer": false,
                "is_income": false,
                "content": "【デモ】大戸屋",
                "amount": -2500.0,
                "currency": "JPY",
                "jpyrate": 1.0,
                "memo": null,
                "large_category_id": 11,
                "middle_category_id": 42,
                "is_target": true,
                "created_at": "2020-07-02T22:50:43+09:00",
                "updated_at": "2020-07-02T00:00:00+09:00",
                "hashed_id": "HyM6QJQYP9Bm9gy5w44-yA",
                "hashed_account_id": "AZRnxnQzv0cViTxCw0Vh9w",
                "hashed_sub_account_id": "ogYqdcnb2ExWCuHeCK97RA",
                "hashed_partner_act_id": null,
                "hashed_user_asset_id": null,
                "account": {
                    "service_id": 46,
                    "service_category_id": 6,
                    "status": 0,
                    "disp_name": null,
                    "memo": null,
                    "msg_flag": 0,
                    "msg_time": null,
                    "account_uid_hidden": "tes*",
                    "last_succeeded_at": "2020-07-02T22:50:43+09:00",
                    "last_aggregated_at": "2020-07-02T22:50:43+09:00",
                    "next_aggregate_at": "2020-07-05T12:51:51+09:00",
                    "message": null,
                    "created_at": "2020-05-27T11:42:16+09:00"
                },
                "sub_account": {
                    "service_category_id": 6,
                    "sub_name": null,
                    "sub_type": "カード",
                    "sub_number": null,
                    "disp_name": null,
                    "created_at": null
                },
                "large_category": {
                    "id": 11,
                    "name": "食費",
                    "income": -1,
                    "disp_order": 3
                },
                "middle_category": {
                    "id": 42,
                    "name": "外食",
                    "large_category_id": 11,
                    "disp_order": 2
                }
            }
        }
    ]
  }    
```
