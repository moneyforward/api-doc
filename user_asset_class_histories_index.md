# 全ての大分類ごとの資産の合計の履歴を得る

## 要求

### 必要な権限

`assets`

### エンドポイント

```
GET https://moneyforward.com/api/v1/user_asset_class_histories
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで `アクセストークン` は [`access_token`](token.md) の値 |
| クエリー | 任意; 複数個使用可 | `account_ids[]` | [口座](accounts_index.md)の `hashed_id` |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `asset_class_ids[]` | [資産の大分類](asset_classes_index.md)の `id` |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `asset_subclass_ids[]` | [資産の中分類](asset_subclasses_index.md)の `id` |
| クエリー | 任意; デフォルト: なし; 複数個使用可 | `target_dates[]` | 基準日; `from_date`, `to_date` より優先 |
| クエリー | 任意; デフォルト: 要求の日の前日 | `from_date` | 最古の基準日; ISO 8601 拡張形式 |
| クエリー | 任意; デフォルト: 要求の日の前日 | `to_date` | 最新の基準日; ISO 8601 拡張形式 |

### 例

```
GET https://moneyforward.com/api/v1/user_asset_class_histories?from_date=2014-06-01&to_date=2014-06-01
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

### 応答の本文

### パラメーター

[GET https://moneyforward.com/api/v1/user_asset_classes](user_asset_classes_index.md) の内容から一部を欠き、 `user_asset_class` キーを `user_asset_class_history` キーに置き換えたものが配列に入っている。
 
### 例

```
[
  {
    "user_asset_class_history": {
      "asset_class_id": 1,
      "profit": 0,
      "rated_profit": 0,
      "rated_value": 12583787,
      "updated_at": "2014-06-01T00:00:00+09:00",
      "value": 12583787,
      "asset_class": {
        "asset_class_name": "預金・現金",
        "asset_class_type": "DEPO",
        "disp_order": 1,
        "id": 1
      }
    }
  },
  {
    "user_asset_class_history": {
      "asset_class_id": 3,
      "profit": 0,
      "rated_profit": 0,
      "rated_value": 1,
      "updated_at": "2014-06-01T00:00:00+09:00",
      "value": 1,
      "asset_class": {
        "asset_class_name": "投資信託",
        "asset_class_type": "MF",
        "disp_order": 4,
        "id": 3
      }
    }
  },
  {
    "user_asset_class_history": {
      "asset_class_id": 4,
      "profit": 96300,
      "rated_profit": 96300,
      "rated_value": 3813782,
      "updated_at": "2014-06-01T00:00:00+09:00",
      "value": 3813782,
      "asset_class": {
        "asset_class_name": "株式(現物)",
        "asset_class_type": "EQ",
        "disp_order": 2,
        "id": 4
      }
    }
  },
  {
    "user_asset_class_history": {
      "asset_class_id": 5,
      "profit": 4488476,
      "rated_profit": 4488476,
      "rated_value": 4488476,
      "updated_at": "2014-06-01T00:00:00+09:00",
      "value": 4488476,
      "asset_class": {
        "asset_class_name": "FX",
        "asset_class_type": "FX",
        "disp_order": 6,
        "id": 5
      }
    }
  },
  {
    "user_asset_class_history": {
      "asset_class_id": 6,
      "profit": 3911674,
      "rated_profit": 3911674,
      "rated_value": 3911674,
      "updated_at": "2014-06-01T00:00:00+09:00",
      "value": 3911674,
      "asset_class": {
        "asset_class_name": "先物OP",
        "asset_class_type": "DRV",
        "disp_order": 7,
        "id": 6
      }
    }
  },
  {
    "user_asset_class_history": {
      "asset_class_id": 11,
      "profit": null,
      "rated_profit": null,
      "rated_value": -4277,
      "updated_at": "2014-06-01T00:00:00+09:00",
      "value": -4277,
      "asset_class": {
        "asset_class_name": "負債",
        "asset_class_type": "LIA",
        "disp_order": 100,
        "id": 11
      }
    }
  },
  {
    "user_asset_class_history": {
      "asset_class_id": 13,
      "profit": 4928571,
      "rated_profit": 4928571,
      "rated_value": 7643731,
      "updated_at": "2014-06-01T00:00:00+09:00",
      "value": 7643731,
      "asset_class": {
        "asset_class_name": "株式(信用)",
        "asset_class_type": "MGN",
        "disp_order": 3,
        "id": 13
      }
    }
  }
]
```
