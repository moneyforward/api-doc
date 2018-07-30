# 全ての約定の履歴を得る

## 要求

### 必要な権限

`trades_inquiry`

### エンドポイント

```
GET https://moneyforward.com/api/v1/executions
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `account_ids[]` | [口座](accounts_index.md)の `hashed_id` |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `sub_account_ids[]` | [サブアカウント](accounts_index.md)の `hashed_id` |
| クエリー | 任意; デフォルト: 要求の日の1か月前の日 | `from_date` | 最古の記帳日または日時; ISO 8601 拡張形式; 最大期間は1ヶ月間とする |
| クエリー | 任意; デフォルト: 要求の日 | `to_date` | 最新の記帳日または日時; ISO 8601 拡張形式 |
| クエリー | 任意; デフォルト: `1` | `page` | ページ番号 |
| クエリー | 任意; デフォルト: `100` | `limit` | 1ページ当たりの最大表示件数; 最大: `500` |

### 例

```
GET https://moneyforward.com/api/v1/executions?account_ids[]=LlPqfqeeCZavwPBLmUy6xg==&sub_account_ids[]=dyJaw7FlOG41c1C-LKndFA==&from_date=2018-04-01&to_date=2018-04-31
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

| 名称 | 内容 |
| ---- | --- |
| `executions[i][execution][id]` | ユニークID |
| `executions[i][execution][source]` | 取引所名等の外部データソース |
| `executions[i][execution][source_id]` | 外部データソースのID |
| `executions[i][execution][trade_kind]` | 取引種類 |
| `executions[i][execution][symbol]` | 金融商品の名前 |
| `executions[i][execution][side]` | 売買 |
| `executions[i][execution][entried_at]` | 取引日; ISO 8601 拡張形式 |
| `executions[i][execution][price]` | 価格; 決済通貨の単位 |
| `executions[i][execution][qty]` | 数量 |
| `executions[i][execution][cost]` | 手数料; 手数料通貨の単位 |
| `executions[i][execution][base_currency]` | 主軸通貨 |
| `executions[i][execution][settlement_currency]` | 決済通貨 |
| `executions[i][execution][cost_currency]` | 手数料通貨 |
| `executions[i][execution][created_at]` | マネーフォワードが情報を取得した日時; ISO 8601 拡張形式 |

### 例

```
{
  "limit": 100,
  "offset": 0,
  "total_count": 1,
  "executions": [
    {
      "execution": {
        "id": 887832549535371264,
        "source": "BITFLYER",
        "source_id": "JFX20180402-999999-123456F",
        "trade_kind": "SPOT",
        "symbol": "BTC_JPY",
        "side": "SELL",
        "created_at": "2018-04-02T10:23:01+09:00",
        "price": 752919,
        "qty": 0.001,
        "cost": 0,
        "base_currency": "BTC",
        "settlement_currency": "JPY",
        "cost_currency": "JPY",
        "created_at": "2018-04-02T12:34:56+09:00",
        "account": {
          "account_uid_hidden": "nkw***",
          "created_at": "2014-08-11T16:20:57+09:00",
          "disp_name": null,
          "last_aggregated_at": "2014-08-11T16:20:59+09:00",
          "last_succeeded_at": "08/11 16:21",
          "memo": null,
          "message": null,
          "msg_flag": 0,
          "msg_time": null,
          "next_aggregate_at": "2014-08-12T16:11:40+09:00",
          "service_category_id": 5,
          "service_id": 3814,
          "status": 0
        },
        "sub_account": {
          "created_at": "2014-08-11T16:20:59+09:00",
          "disp_name": null,
          "service_category_id": 5,
          "sub_name": "",
          "sub_number": "",
          "sub_type": "FX"
        }
      }
    }
  ]
}
```
