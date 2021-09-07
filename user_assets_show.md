# 特定の資産を得る

## 要求

### 必要な権限

`assets`

### エンドポイント

```
GET https://moneyforward.com/api/v1/user_assets/:id
```

### パラメーター

| 場所     | 随意性                           | 名称                                    | 内容                                                                                                 |
| -------- | -------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| パス     | 必須                             | `id`                                    | 資産の `hashed_id`                                                                                   |
| ヘッダー | 必須                             | `Authorization` または `X-MFOAuthToken` | `` Bearer `アクセストークン`  ``; ここで `` `アクセストークン` `` は [`access_token`](token.md) の値 |
| クエリー | 任意; デフォルト: 要求の日の前日 | `previous_date`                         | 前の営業日; ISO 8601 拡張形式                                                                        |

### 例

```
GET https://moneyforward.com/api/v1/user_assets/vpxDzM6STgFT4Br7pFTzVQ==
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

| 名称                                           | 内容                                                                                                                          |
| ---------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `user_asset[asset_class_id]`                   | [資産の大分類](https://github.com/moneyforward/api-doc/blob/master/asset_classes_index.md)の ID                               |
| `user_asset[asset_subclass_id]`                | [資産の中分類](https://github.com/moneyforward/api-doc/blob/master/asset_subclasses_index.md)の ID                            |
| `user_asset[code]`                             | 株式銘柄コード等                                                                                                              |
| `user_asset[cost]`                             | 現在未使用                                                                                                                    |
| `user_asset[currency]`                         | 通貨                                                                                                                          |
| `user_asset[current_price]`                    | 基準価格(1 口または 1 万口当たりの値段)                                                                                       |
| `user_asset[entried_at]`                       | 資産取得日; ISO 8601 拡張形式; 特定できなければ `null`                                                                        |
| `user_asset[entried_price]`                    | 取得価格                                                                                                                      |
| `user_asset[expire_at]`                        | ポイント等の場合の有効期限日; ISO 8601 拡張形式; 特定できなければ `null`                                                      |
| `user_asset[jpy_rate]`                         | 円換算レート                                                                                                                  |
| `user_asset[name]`                             | 名称                                                                                                                          |
| `user_asset[profit]`                           | 損益                                                                                                                          |
| `user_asset[qty]`                              | 数量                                                                                                                          |
| `user_asset[value]`                            | 評価額またはポイント数                                                                                                        |
| `user_asset[rated_value]`                      | 円換算評価額                                                                                                                  |
| `user_asset[rated_profit]`                     | 円換算損益                                                                                                                    |
| `user_asset[created_at]`                       | レコード作成日; ISO 8601 拡張形式                                                                                             |
| `user_asset[updated_at]`                       | レコード更新日; ISO 8601 拡張形式                                                                                             |
| `user_asset[hashed_id]`                        | 資産の hash_id                                                                                                                |
| `user_asset[hashed_account_id]`                | 口座の hash_id                                                                                                                |
| `user_asset[hashed_sub_account_id]`            | サブアカウントの hash_id                                                                                                      |
| `user_asset[previous_value_set][value]`        | 前の営業日の評価額                                                                                                            |
| `user_asset[previous_value_set][profit]`       | 前の営業日の損益                                                                                                              |
| `user_asset[previous_value_set][rated_value]`  | 前の営業日の円換算評価額                                                                                                      |
| `user_asset[previous_value_set][rated_profit]` | 前の営業日の円換算損益                                                                                                        |
| `user_asset[previous_value_set][updated_at]`   | 前の営業日; ISO 8601 拡張形式                                                                                                 |
| `user_asset[account][account_uid_hidden]`      | 口座の id の一部を隠したもの (最大 3 文字が表示される)                                                                        |
| `user_asset[account][created_at]`              | account を登録した日時                                                                                                        |
| `user_asset[account][disp_name]`               | ユーザーが設定した口座の識別名 (未設定なら null)                                                                              |
| `user_asset[account][last_aggregated_at]`      | 該当 account のサービスが、MoneyForward と最後にデータ連携を実施した日時                                                      |
| `user_asset[account][last_succeeded_at]`       | 該当 account のサービスが、MoneyForward と最後にデータ連携処理が成功した日時                                                  |
| `user_asset[account][memo]`                    | ユーザーが設定したメモ                                                                                                        |
| `user_asset[account][message]`                 | 金融機関からユーザーへの通知                                                                                                  |
| `user_asset[account][msg_flag]`                | `true`: message を表示する, false (デフォルト): message を表示しない                                                          |
| `user_asset[account][msg_time]`                | 現在は未使用                                                                                                                  |
| `user_asset[account][next_aggregate_at]`       | 該当 account のサービスが、MoneyForward とデータ連携する次回の予定日                                                          |
| `user_asset[account][service_category_id]`     | 金融機関分類の id                                                                                                             |
| `user_asset[account][service_id]`              | 金融機関の`id`                                                                                                                |
| `user_asset[account][status]`                  | 金融機関からの情報の取得状況; 0: 正常, 1: 取得中、2: 取得エラー                                                               |
| `user_asset[account][service]{..}`             | [金融機関情報詳細](https://github.com/moneyforward/api-doc/blob/master/services_show.md)                                      |
| `user_asset[sub_account][created_at]`          | sub_account を登録した日時                                                                                                    |
| `user_asset[sub_account][disp_name]`           | 手入力で作成した口座（財布内の所持金など）につけた名称                                                                        |
| `user_asset[sub_account][service_category_id]` | 金融機関分類の id                                                                                                             |
| `user_asset[sub_account][sub_name]`            | 支店名                                                                                                                        |
| `user_asset[sub_account][sub_number]`          | 口座番号                                                                                                                      |
| `user_asset[sub_account][sub_type]`            | 口座の種別（普通、定期、カードなど）など弊社側のシステムで自動で割り当てられた値                                              |
| `user_asset[asset_class]{..}`                  | [資産の大分類](https://github.com/moneyforward/api-doc/blob/master/asset_classes_index.md)の asset_class[i]と同様の内容を返す |
| `user_asset[asset_subclass]{..}`               | [資産の中分類](https://github.com/moneyforward/api-doc/blob/master/asset_subclasses_index.md)[i]と同様の内容を返す            |

### 例

```
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
      "id": 12,
      "liquid": 85
    }
  }
}
```
