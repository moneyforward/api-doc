# 全ての口座の取得状況や資産額合計を得る

## 要求

### 必要な権限

`accounts`

### エンドポイント

```
GET https://moneyforward.com/api/v1/accounts
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `service_category_ids[]` | [金融機関の種別](service_categories_index.md)の `id` |
| クエリー | 任意; デフォルト: `1` | `page` | ページ番号 |
| クエリー | 任意; デフォルト: `100` | `limit` | 1ページ当たりの最大表示件数; 最大: `10000` |

### 例

```
GET https://moneyforward.com/api/v1/accounts?service_category_ids[]=1&service_category_ids[]=2&page=1
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

| 名称 | 内容 |
| ---- | --- |
| `accounts[i][account][account_uid_hidden]` | 口座のidの一部を隠したもの (最大3文字が表示される) |
| `accounts[i][account][asset_sum]` | 資産の合計 |
| `accounts[i][account][disp_name]` | ユーザーが設定した口座の識別名 (未設定なら `null`) |
| `accounts[i][account][memo]` | ユーザーが設定したメモ |
| `accounts[i][account][message]` | 金融機関からユーザーへの通知 |
| `accounts[i][account][msg_flag]` | `true`: `message` を表示する, `false` (デフォルト): `message` を表示しない |
| `accounts[i][account][status]` | 金融機関からの情報の取得状況; `0`: 取得済み, `1`: 取得中、`2`: 取得エラー, `3`: 取得停止中 |
| `accounts[i][account][sub_accounts][j][sub_name]` | 金融機関の支店名 |
| `accounts[i][account][sub_accounts][j][sub_number]` | 口座番号 |
 
### 例

```
 {
   "limit": 100,
   "offset": 0,
   "total_count": 1,
   "accounts": [
     {
       "account": {
         "account_uid_hidden": "dem*",
         "asset_sum": 4839122.2979287775,
         "asset_sum_debt": -839122.2979287775,
         "account_show_path": "/accounts/show/JmaKaQJ1wfqKUE68hX9cHw",
         "created_at": "2014-04-19T17:33:37+09:00",
         "disp_name": null,
         "aggregation_error_id": 5,
         "last_aggregated_at": "2014-05-22T06:33:13+09:00",
         "last_succeeded_at": "2014-05-22T06:33:13+09:00",
         "memo": null,
         "message": null,
         "msg_flag": 0,
         "msg_time": null,
         "next_aggregate_at": "2014-05-25T02:27:08+09:00",
         "service_category_id": 1,
         "service_id": 1,
         "status": 2,
         "hashed_id": "LlPqfqeeCZavwPBLmUy6xg==",
         "sub_accounts" : [
           {
             "sub_name" : null,
             "sub_number" : null
           },
           {
             "sub_name" : "本店",
             "sub_number" : "0999999",
           }
         ],
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
         "aggregation_error": {
           "error_msg": "LoginErrorException",
           "error_type": "FATAL",
           "id": 5,
           "msg_title": "設定エラー"
         }
       }
     }
   ]
 }
```
