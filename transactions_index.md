# 全ての入出金記録を得る

## 要求

### 必要な権限

`transactions`

### エンドポイント

```
GET https://moneyforward.com/api/v1/transactions
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |
| クエリー | 任意; デフォルト: 全て | `is_target` | `1`: 計算対象, `0`: 計算対象外 |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `account_ids[]` | [口座](accounts_index.md)の `hashed_id` |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `sub_account_ids[]` | [サブアカウント](accounts_index.md)の `hashed_id` |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `large_category_ids[]` | [入出金の大分類](transaction_categories_index.md)の `id` |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `middle_category_ids[]` | [入出金の中分類](transaction_categories_index.md)の `id` |
| クエリー | 任意; デフォルト: 要求の日の1か月前の日 | `from_date` | 最古の記帳日または日時; ISO 8601 拡張形式 |
| クエリー | 任意; デフォルト: 要求の日 | `to_date` | 最新の記帳日または日時; ISO 8601 拡張形式 |
| クエリー | 任意; デフォルト: `1` | `page` | ページ番号 |
| クエリー | 任意; デフォルト: `100` | `limit` | 1ページ当たりの最大表示件数, 最大: `500` |

※取得できる最大の期間は1年間、1年以上の期間を指定した場合、to_dateを基準にfrom_dateは1年前に設定される

### 例

```
GET https://moneyforward.com/api/v1/transactions?sub_account_ids[]=3aJadZHjTJDdj-J0V2Oawg&sub_account_ids[]=dyJaw7FlOG41c1C-LKndFA==&middle_category_ids[]=32
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文
### パラメーター

| 名称 | 内容 |
| ---- | --- |
| `total_count`                                                      | 全レコード数                                                                       |
| `transactions[i][transaction][amount]`                             | 金額; 正: 入金, 負: 出金                                                           |
| `transactions[i][transaction][content]`                            | ユーザーが書き込める入出金の内容を表す文字列                                       |
| `transactions[i][transaction][created_at]`                         | マネーフォワードが情報を取得した日時; ISO 8601 拡張形式                            |
| `transactions[i][transaction][currency]`                           | 通貨; デフォルト: `JPY` (日本円)                                                     |
| `transactions[i][transaction][is_target]`                          | `true`: 計算対象, `false`: 計算対象外                                                  |
| `transactions[i][transaction][is_income]`                          | `true`: 収入, `false`: 支出                                                            |
| `transactions[i][transaction][is_transfer]`                        | `true`: 振替, `false`: 振替でない                                                      |
| `transactions[i][transaction][jpyrate]`                            | 日本円に対する為替レート                                                           |
| `transactions[i][transaction][large_category_id]`                  | 大項目の`id`                                                                        |
| `transactions[i][transaction][memo]`                               | ユーザー入力のメモ                                                                 |
| `transactions[i][transaction][middle_category_id]`                 | 中項目の`id`                                                                        |
| `transactions[i][transaction][updated_at]`                         | 入出金が記帳された日時; ISO 8601 拡張形式                                          |
| `transactions[i][transaction][hashed_id]`                          | 入出金記録の`hashed_id`                                                             |
| `transactions[i][transaction][hashed_partner_act_id]`              | 振替を構成する反対側の入出金記録の`hashed_id`                                       |
| `transactions[i][transaction][hashed_account_id]`                  | 入出金元の口座の`hashed_id`                                                         |
| `transactions[i][transaction][hashed_sub_account_id]`              | 入出金元のサブアカウントの`hashed_id`                                               |
| `transactions[i][transaction][account][account_uid_hidden]`        | 口座のidの一部を隠したもの (最大3文字が表示される)                                 |
| `transactions[i][transaction][account][created_at]`                | accountを登録した日時                                                                                   |
| `transactions[i][transaction][account][disp_name]`                 | ユーザーが設定した口座の識別名 (未設定なら null)                                   |
| `transactions[i][transaction][account][last_aggregated_at]`        | 該当accountのサービスが、MoneyForwardと最後にデータ連携を実施した日時              |
| `transactions[i][transaction][account][last_succeeded_at]`         | 該当accountのサービスが、MoneyForwardと最後にデータ連携処理が成功した日時          |
| `transactions[i][transaction][account][memo]`                      | ユーザーが設定したメモ                                                             |
| `transactions[i][transaction][account][message]`                   | 金融機関からユーザーへの通知                                                       |
| `transactions[i][transaction][account][msg_flag]`                  | `true`: message を表示する, false (デフォルト): message を表示しない                 |
| `transactions[i][transaction][account][msg_time]`                  | 現在は未使用
| `transactions[i][transaction][account][next_aggregate_at]`         | 該当accountのサービスが、MoneyForwardとデータ連携する次回の予定日                  |
| `transactions[i][transaction][account][service_category_id]`       | 金融機関分類のid                                                                   |
| `transactions[i][transaction][account][service_id]`                | 金融機関の`id`                                                                      |
| `transactions[i][transaction][account][status]`                    | 金融機関からの情報の取得状況; 0: 正常, 1: 取得中、2: 取得エラー |
| `transactions[i][transaction][sub_account][created_at]`            | sub_accountを登録した日時                                                          |
| `transactions[i][transaction][sub_account][disp_name]`             | 手入力で作成した口座（財布内の所持金など）につけた名称                                   |
| `transactions[i][transaction][sub_account][service_category_id]`   | 金融機関分類のid                                                                   |
| `transactions[i][transaction][sub_account][sub_name]`              | 支店名                                                                             |
| `transactions[i][transaction][sub_account][sub_number]`            | 口座番号                                                                           |
| `transactions[i][transaction][sub_account][sub_type]`              | 口座の種別（普通、定期、カードなど）など弊社側のシステムで自動で割り当てられた値             |
| `transactions[i][transaction][large_category][disp_order]`         | マネーフォワードサービスで表示される時の表示順                                     |
| `transactions[i][transaction][large_category][id]`                 | 大項目の`id`                                                                        |
| `transactions[i][transaction][large_category][income]`             | `true`: 収入, `false`: 支出 ※（サンプルデータには、-1が格納されているため、要確認）    |
| `transactions[i][transaction][large_category][name]`               | 大項目の名称                                                                       |
| `transactions[i][transaction][middle_category][disp_order]`        | マネーフォワードサービスで表示される時の表示順                                     |
| `transactions[i][transaction][middle_category][id]`                | 中項目の`id`                                                                        |
| `transactions[i][transaction][middle_category][large_category_id]` | 紐付く大項目の`id`                                                                  |
| `transactions[i][transaction][middle_category][name]`              | 中項目の名称                                                                       |


### 例

```
{
  "limit": 100,
  "offset": 0,
  "total_count": 1,
  "transactions": [
    {
      "transaction": {
        "amount": -1,
        "content": "地方税",
        "created_at": "2014-08-11T16:20:59+09:00",
        "currency": "JPY",
        "is_target": true,
        "is_income": false,
        "is_transfer": false,
        "jpyrate": 1,
        "large_category_id": 9,
        "memo": null,
        "middle_category_id": 32,
        "updated_at": "2014-07-20T00:00:00+09:00",
        "hashed_id": "dYDn1yKM37qFejzmwbf2KA==",
        "hashed_partner_act_id": "PaWHbkj4F6W-agLF69LsHQ",
        "hashed_account_id": "E8NWqTw4e3TnXffLl50f-Q==",
        "hashed_sub_account_id": "dyJaw7FlOG41c1C-LKndFA==",
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
          "service_category_id": 2,
          "service_id": 2,
          "status": 0
        },
        "sub_account": {
          "created_at": "2014-08-11T16:20:59+09:00",
          "disp_name": null,
          "service_category_id": 2,
          "sub_name": "",
          "sub_number": "",
          "sub_type": "代表口座 - 円普通"
        },
        "large_category": {
          "disp_order": 18,
          "id": 9,
          "income": -1,
          "name": "税・社会保障"
        },
        "middle_category": {
          "disp_order": 1,
          "id": 32,
          "large_category_id": 9,
          "name": "所得税・住民税"
        }
      }
    }
  ]
}
```
