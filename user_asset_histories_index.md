# 全ての資産の履歴を得る

## 要求

### 必要な権限

`assets`

### エンドポイント

```
GET https://moneyforward.com/api/v1/user_asset_histories
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |
| クエリー | 任意; デフォルト: , 複数個使用可 | `account_ids[]` | 口座の `hashed_id` |
| クエリー | 任意; デフォルト: , 複数個使用可 | `asset_class_ids[]` | 資産の大分類の `id` |
| クエリー | 任意; デフォルト: , 複数個使用可 | `asset_subclass_ids[]` | 資産の中分類の `id` |
| クエリー | 任意; デフォルト: , 複数個使用可 | `target_dates[]` | 期準日; ISO 8601 拡張形式; `from_date`, `to_date` より優先 |
| クエリー | 任意; デフォルト: 要求の日の前日 | `from_date` | 最古基準日; ISO 8601 拡張形式 |
| クエリー | 任意; デフォルト: 要求の日の前日 | `to_date` | 最新基準日; ISO 8601 拡張形式 |
| クエリー | 任意; デフォルト: `1` | `page` | ページ番号 |
| クエリー | 任意; デフォルト: `25` | `limit` | 1ページ当たりの最大表示件数; 最大: `500` |

### 例
 
```
GET https://moneyforward.com/api/v1/user_asset_histories?account_ids[]=LlPqfqeeCZavwPBLmUy6xg==&from_date=2014-5-22&to_date=2014-05-23
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文
### パラメーター

| 名称 | 内容 |
| ---- | --- |
| `total_count`                                                                  | 全レコード数                                                                       |
| `user_asset_histories[i][user_asset_history][asset_class_id]`                  | 資産の大分類のid                                                                   |
| `user_asset_histories[i][user_asset_history][asset_subclass_id]`               | 資産の大分類中の中分類のid                                                         |
| `user_asset_histories[i][user_asset_history][code]`                            | 株式銘柄コード等                                                                   |
| `user_asset_histories[i][user_asset_history][cost]`                            | 現在未使用                                                                         |
| `user_asset_histories[i][user_asset_history][currency]`                        | 通貨; デフォルト: `JPY` (日本円)                                                   |
| `user_asset_histories[i][user_asset_history][current_price]`                   | データが取得された時点での、10000口当たりの単価                                    |
| `user_asset_histories[i][user_asset_history][entried_at]`                      | 取得日; ISO 8601 拡張形式; 特定できなければ `null`                                   |
| `user_asset_histories[i][user_asset_history][entried_price]`                   | 取得価格                                                                           |
| `user_asset_histories[i][user_asset_history][expire_at]`                       | ポイント等の場合の有効期限日; ISO 8601 拡張形式; 特定できなければ `null`             |
| `user_asset_histories[i][user_asset_history][jpyrate]`                         | 円換算レート                                                                       |
| `user_asset_histories[i][user_asset_history][name]`                            | 名称                                                                               |
| `user_asset_histories[i][user_asset_history][profit]`                          | 損益                                                                               |
| `user_asset_histories[i][user_asset_history][qty]`                             | 数量                                                                               |
| `user_asset_histories[i][user_asset_history][updated_at]`                      | 基準日; ISO 8601 拡張形式                                                          |
| `user_asset_histories[i][user_asset_history][value]`                           | 評価額またはポイント数                                                             |
| `user_asset_histories[i][user_asset_history][hashed_id]`                       | ユニーク`id`                                                                         |
| `user_asset_histories[i][user_asset_history][hashed_account_id]`               | 入出金元の口座の `hashed_id`                                                         |
| `user_asset_histories[i][user_asset_history][hashed_original_user_asset_id]`   | 履歴作成の元となった資産の `hashed_id`                                               |
| `user_asset_histories[i][user_asset_history][account][account_uid_hidden]`     | 口座のidの一部を隠したもの (最大3文字が表示される)                                 |
| `user_asset_histories[i][user_asset_history][account][created_at]`             | 口座が登録された日付                                                              |
| `user_asset_histories[i][user_asset_history][account][disp_name]`              | ユーザーが設定した口座の識別名 (未設定なら `null`)                                   |
| `user_asset_histories[i][user_asset_history][account][last_aggregated_at]`     | 該当accountのサービスが、MoneyForwardと最後にデータ連携を実施した日時              |
| `user_asset_histories[i][user_asset_history][account][last_succeeded_at]`      | 該当accountのサービスが、MoneyForwardと最後にデータ連携処理が成功した日時          |
| `user_asset_histories[i][user_asset_history][account][memo]`                   | ユーザーが設定したメモ                                                             |
| `user_asset_histories[i][user_asset_history][account][message]`                | 金融機関からユーザーへの通知                                                       |
| `user_asset_histories[i][user_asset_history][account][msg_flag]`               | `true`: message を表示する, `false` (デフォルト): message を表示しない                 |
| `user_asset_histories[i][user_asset_history][account][next_aggregate_at]`      | 該当accountのさびーすが、MoneyForwardとデータ連携する次回の予定日                  |
| `user_asset_histories[i][user_asset_history][account][service_category_id]`    | 金融機関分類のid                                                                   |
| `user_asset_histories[i][user_asset_history][account][service_id]`             | 金融機関の`id`                                                                      |
| `user_asset_histories[i][user_asset_history][account][status]`                 | 金融機関からの情報の取得状況; 0: 取得済み, 1: 取得中、2: 取得エラー, 3: 取得停止中 |
| `user_asset_histories[i][user_asset_history][account][service][category_name]` | 金融機関の分類                                                                     |
| `user_asset_histories[i][user_asset_history][account][service][category_type]` | 金融機関の分類を表す固有の記号                                                     |
| `user_asset_histories[i][user_asset_history][account][service][code]`          | 金融機関コード                                                                     |
| `user_asset_histories[i][user_asset_history][account][service][description]`   | 金融機関へのログインについての説明                                                 |
| `user_asset_histories[i][user_asset_history][account][service][id]`            | 金融機関の`id`                                                                      |
| `user_asset_histories[i][user_asset_history][account][service][login_url]`     | 金融機関サイトへのログイン先                                                       |
| `user_asset_histories[i][user_asset_history][account][service][service_name]`  | 金融機関の名前                                                                     |
| `user_asset_histories[i][user_asset_history][account][service][service_type]`  | 金融機関固有の記号                                                                 |
| `user_asset_histories[i][user_asset_history][account][service][yomigana]`      | 金融機関の名前の読み仮名                                                           |

### 例

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
