# カード引き落とし明細一覧を取得する

## 要求

### 必要な権限

`transactions`

### エンドポイント

```
GET https://moneyforward.com/api/v1/card_future_payments
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `account_ids[]` | [口座](accounts_index.md)の `hashed_id` |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `sub_account_ids[]` | [サブアカウント](accounts_index.md)の `hashed_id` |
| クエリー | 任意; デフォルト: 要求の日の1か月前の日 | `from_date` | 最古の記帳日; ISO 8601 拡張形式 |
| クエリー | 任意; デフォルト: 要求の日 | `to_date` | 最新の記帳日; ISO 8601 拡張形式 |
| クエリー | 任意; デフォルト: `1` | `page` | ページ番号 |
| クエリー | 任意; デフォルト: `100` | `limit` | 1ページ当たりの最大表示件数, 最大: `500` |

※取得できる最大の期間は1年間、1年以上の期間を指定した場合、to_dateを基準にfrom_dateは1年前に設定される

### 例

```
GET https://moneyforward.com/api/v1/card_future_payments?account_ids[]=3aJadZHjTJDdj-J0V2Oawg&account_ids[]=dyJaw7FlOG41c1C-LKndFA==
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文
### パラメーター

| 名称 | 内容 |
| ---- | --- |
| `card_future_payments[i][content]` | 入出金内容 |
| `card_future_payments[i][date]` | 入出金日付（引落し日） |
| `card_future_payments[i][amount]` | 引落し金額 |
| `card_future_payments[i][currency]` | 通貨; デフォルト: JPY (日本円) |
| `card_future_payments[i][jpyrate]` | 日本円に対する為替レート |
| `card_future_payments[i][created_at]` | マネーフォワードが情報を取得した日時 |
| `card_future_payments[i][updated_at]` | 入出金が記帳された日時; ISO 8601 拡張形式 |
| `card_future_payments[i][hashed_id]` | 入出金記録のhashed_id |
| `card_future_payments[i][hashed_account_id]` | 入出金元口座のhashed_id |
| `card_future_payments[i][hashed_sub_account_id]` | 入出金元口座のサブアカウントのhashed_id |
| `card_future_payments[i][hashed_partner_account_id]` | 振替相手口座のhashed_id |
| `card_future_payments[i][hashed_partner_sub_account_id]` | 振替相手口座のサブアカウントのhashed_id |
| `card_future_payments[i][account][service_id]` | 金融機関のid |
| `card_future_payments[i][account][service_category_id]` | 金融機関分類のid |
| `card_future_payments[i][account][status]` | 金融機関からの情報の取得状況; 0: 正常, 1: 取得中、2: 取得エラー |
| `card_future_payments[i][account][disp_name]` | 手入力で作成した口座（財布内の所持金など）につけた名称 |
| `card_future_payments[i][account][memo]` | ユーザーが設定したメモ |
| `card_future_payments[i][account][msg_flag]` | true: message を表示する, false (デフォルト): message を表示しない |
| `card_future_payments[i][account][msg_time]` | 現在は未使用 |
| `card_future_payments[i][account][account_uid_hidden]` | 口座のidの一部を隠したもの (最大3文字が表示される) |
| `card_future_payments[i][account][last_succeeded_at]` | 該当accountのサービスが、MoneyForwardと最後にデータ連携処理が成功した日時 |
| `card_future_payments[i][account][last_aggregated_at]` | 該当accountのサービスが、MoneyForwardと最後にデータ連携を実施した日時 |
| `card_future_payments[i][account][next_aggregate_at]` | 該当accountのサービスが、MoneyForwardとデータ連携する次回の予定日 |
| `card_future_payments[i][account][message]` | 金融機関からユーザーへの通知 |
| `card_future_payments[i][account][created_at]` | accountを登録した日時 |
| `card_future_payments[i][account][service][id]` | 金融機関の id |
| `card_future_payments[i][account][service][service_category_id]` | 金融機関の分類を表すid |
| `card_future_payments[i][account][service][category_type]` | 金融機関の分類を表す固有の記号 |
| `card_future_payments[i][account][service][service_type]` | 金融機関固有の記号 |
| `card_future_payments[i][account][service][category_name]` | 金融機関の分類 |
| `card_future_payments[i][account][service][service_name]` | 金融機関の名前 |
| `card_future_payments[i][account][service][is_biz]` | 法人口座か否か |
| `card_future_payments[i][account][service][login_url]` | 金融機関サイトへのログイン先 |
| `card_future_payments[i][account][service][yomigana]` | 金融機関の名前の読み仮名 |
| `card_future_payments[i][account][service][description]` | 金融機関へのログインについての説明 |
| `card_future_payments[i][account][service][code]` | 金融機関コード |
| `card_future_payments[i][sub_account][service_category_id]` | 金融機関分類のid |
| `card_future_payments[i][sub_account][sub_name]` | 支店名 |
| `card_future_payments[i][sub_account][sub_type]` | 口座の種別（普通、定期、カードなど）など弊社側のシステムで自動で割り当てられた値 |
| `card_future_payments[i][sub_account][sub_number]` | 口座番号 |
| `card_future_payments[i][sub_account][disp_name]` | 支店名 |
| `card_future_payments[i][sub_account][created_at]` | sub_accountを登録した日時 |

### 例

```
{
    "from_date": "2019-07-07",
    "to_date": "2019-08-07",
    "limit": 100,
    "offset": 0,
    "total_count": 1,
    "card_future_payments": [
        {
            "content": "2019/07/10 お支払い分",
            "date": "2019-07-10",
            "amount": -52534.0,
            "currency": "JPY",
            "jpyrate": 1.0,
            "created_at": "2019-08-07T18:37:10+09:00",
            "updated_at": "2019-07-10T00:00:00+09:00",
            "hashed_id": "TZY3VMRuzMQq0LmgGrx98Q",
            "hashed_account_id": "bF2TsxGt8KSkahxa8Fu6yQ",
            "hashed_sub_account_id": "iwttZ8n8cDjePlS8weMNsQ",
            "hashed_partner_account_id": "0h4b4HjA8lOayenSoJJtIA",
            "hashed_partner_sub_account_id": "2N_JYmyxVPqe8OuiFyln8A",
            "account": {
                "service_id": 39,
                "service_category_id": 6,
                "status": 0,
                "disp_name": null,
                "memo": null,
                "msg_flag": 0,
                "msg_time": null,
                "account_uid_hidden": "Wge*****************",
                "last_succeeded_at": "2019-08-07T18:37:10+09:00",
                "last_aggregated_at": "2019-08-07T18:37:10+09:00",
                "next_aggregate_at": "2019-08-08T10:36:55+09:00",
                "message": null,
                "created_at": "2019-08-07T18:37:00+09:00",
                "service": {
                    "id": 39,
                    "service_category_id": 6,
                    "category_type": "CARD",
                    "service_type": "C_JCB",
                    "category_name": "カード",
                    "service_name": "JCBカード",
                    "is_biz": false,
                    "login_url": "https://my.jcb.co.jp/Login",
                    "yomigana": "ジェイシービーカード",
                    "description": "<li>登録後、「IDとパスワードをお確かめ下さい」というメッセージが表示された場合、一度金融機関サイトにログイン出来るかのご確認をお願いします。</li>",
                    "code": null
                }
            },
            "sub_account": {
                "service_category_id": 6,
                "sub_name": null,
                "sub_type": "カード",
                "sub_number": null,
                "disp_name": null,
                "created_at": null
            }
        }
    ]
}
```
