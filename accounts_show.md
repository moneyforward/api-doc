# 特定の口座の取得状況や資産額合計、ログインに必要な入力項目を得る

## 要求

### 必要な権限

`accounts`

### エンドポイント

```
GET https://moneyforward.com/api/v1/accounts/:id
```

### パラメーター

| 場所     | 随意性 | 名称                                    | 内容                                                                                                 |
| -------- | ------ | --------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| ヘッダー | 必須   | `Authorization` または `X-MFOAuthToken` | `` Bearer `アクセストークン`  ``; ここで `` `アクセストークン` `` は [`access_token`](token.md) の値 |
| パス     | 必須   | `id`                                    | [口座](accounts_index.md)の `hashed_id`                                                              |

### 例

```
GET https://moneyforward.com/api/v1/accounts/LlPqfqeeCZavwPBLmUy6xg==
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

| 名称                                                     | 内容                                                                                                                                                                                                                                                                                                                          |
| -------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `account[account_uid_hidden]`                            | 口座の id の一部を隠したもの (最大 3 文字が表示される)                                                                                                                                                                                                                                                                        |
| `account[disp_name]`                                     | ユーザーが設定した口座の識別名 (未設定なら `null`)                                                                                                                                                                                                                                                                            |
| `account[memo]`                                          | ユーザーが設定したメモ                                                                                                                                                                                                                                                                                                        |
| `account[message]`                                       | 金融機関からユーザーへの通知                                                                                                                                                                                                                                                                                                  |
| `account[msg_flag]`                                      | `true`: `message` を表示する, `false` (デフォルト): `message` を表示しない                                                                                                                                                                                                                                                    |
| `account[status]`                                        | 金融機関からの情報の取得状況; `0`: 正常, `1`: 取得中、`2`: 取得エラー                                                                                                                                                                                                                                                         |
| `account[aggregation_info][aggregation_status_sentence]` | 口座のステータス状態の表示文言。`error_id == null`の場合：`"正常"` 、`error_id == null && message != null` の場合：`"正常（確認事項あり）"`、`error_id != null`の場合：各[aggregation_error](https://github.com/moneyforward/api-doc/blob/master/aggregation_errors_index.md)の`"msg_title"`が設定される                      |
| `account[aggregation_info][aggregation_detail_sentence]` | 口座のステータス詳細の表示文言。`message != null` の場合：`"message"`が設定される。`message == null` の場合、デフォルトメッセージとして`"金融機関と正常に連携できています"`もしくは各[aggregation_error](https://github.com/moneyforward/api-doc/blob/master/aggregation_errors_index.md)に対応した汎用メッセージが設定される |
| `account[aggregation_info][last_aggregated_ago]`         | 現在時刻から最後に金融機関から情報取得した日を減算し、UI 表示用に加工した文言                                                                                                                                                                                                                                                 |
| `account[aggregation_info][last_succeeded_ago]`          | 現在時刻から最後に金融機関から情報取得が成功した日を減算し、UI 表示用に加工した文言                                                                                                                                                                                                                                           |
| `account[aggregation_info][is_error]`                    | `true` または `false`。直前の情報取得が失敗しているかどうかを示す。`aggregation_error_id`が設定されている場合に`true`が設定される                                                                                                                                                                                             |
| `account[aggregation_info][is_suspended]`                | `true` または `false`。ユーザーからの問い合わせなどを起因とし、口座が情報取得停止状態に設定されている場合に`true`が設定される                                                                                                                                                                                                 |
| `account[aggregation_info][is_retrieving]`               | `true` または `false`。口座が情報取得中か否かを示す。`account[status]=1`の場合は`true`、それ以外の場合は`false`が設定される                                                                                                                                                                                                   |
| `account[aggregation_info][is_aggregatable]`             | `true` または `false`。UI における更新ボタンの活性／非活性を示す。`true`の場合は活性、`false`の場合は非活性とする                                                                                                                                                                                                             |
| `account[sub_accounts][i][sub_name]`                     | 金融機関の支店名                                                                                                                                                                                                                                                                                                              |
| `account[sub_accounts][i][sub_number]`                   | 口座番号                                                                                                                                                                                                                                                                                                                      |
| `account[exclusive_service_forms]`                       | ログインに必要な全ての入力項目                                                                                                                                                                                                                                                                                                |
| `account[exclusive_service_forms][i][encrypt_flag]`      | 暗号化対象項目か否か                                                                                                                                                                                                                                                                                                          |
| `account[exclusive_service_forms][i][input_type]`        | `alphameric`: 数値, `password`: パスワード, `text`: 文字列, `checkbox`: チェックボックス, `radio`: ラジオボタン, `table`: 乱数表                                                                                                                                                                                              |
| `account[exclusive_service_forms][i][format]`            | 入力値を制約する正規表現; 空白制限なし; `input_type` が `radio` の場合は、全ての選択肢                                                                                                                                                                                                                                        |
| `account[exclusive_service_forms][i][note]`              | 補足説明                                                                                                                                                                                                                                                                                                                      |
| `account[exclusive_service_forms][i][service_form_type]` | 入力項目の識別子                                                                                                                                                                                                                                                                                                              |
| `account[exclusive_service_forms][i][unique_flag]`       | 一意性が課されるか否か                                                                                                                                                                                                                                                                                                        |
| `account[additional_requests]`                           | 全ての秘密の質問やワンタイムパスワード                                                                                                                                                                                                                                                                                        |
| `account[additional_requests][i][hashed_id]`             | 秘密の質問やワンタイムパスワードの入力リクエストリスト                                                                                                                                                                                                                                                                        |
| `account[additional_requests][i][message]`               | 金融機関からユーザーへの通知                                                                                                                                                                                                                                                                                                  |
| `account[additional_requests][i][request_data]`          | 質問                                                                                                                                                                                                                                                                                                                          |

### 例

```
{
  "account": {
    "service_id": ,
    "service_category_id": 2,
    "status": 0,
    "disp_name": null,
    "memo": null,
    "msg_flag": 0,
    "msg_time": null,
    "account_uid_hidden": "Wge*****************",
    "last_succeeded_at": "2020-06-26T08:49:54+09:00",
    "last_aggregated_at": "2020-06-26T08:49:54+09:00",
    "next_aggregate_at": "2020-06-28T02:41:42+09:00",
    "message": null,
    "created_at": "2019-12-24T17:56:21+09:00",
    "account_show_path": "/accounts/show/TJmCObOUmIOoZFilYbuI8g",
    "hashed_id": "_TFmQwJF6n_moknLRvRpUw",
    "aggregation_error_id": 0,
    "aggregation_info": {
      "aggregation_status_sentence": "正常",
      "aggregation_detail_sentence": "金融機関と正常に連携できています",
      "last_aggregated_ago": "約5時間前",
      "last_succeeded_ago": "約5時間前",
      "is_error": false,
      "is_suspended": false,
      "is_retrieving": false,
      "is_aggregatable": true
    },
    "sub_accounts": [
      {
        "sub_name": null,
        "sub_number": null
      },
      {
        "sub_name": "本店",
        "sub_number": "0999999"
      }
    ],
    "service": {
      "category_name": "銀行",
      "category_type": "BANK",
      "code": "0001",
      "description": "<li>口座番号ではなくオンラインバンキング用のログイン情報となります。オンラインバンキングの手続きは各金融機関へお問い合わせ下さい。</li><li>登録後、「合言葉の入力が必要です」というメッセージが表示された場合、本サイトへのログインに用いる答えの入力をお願いします。</li><li>登録後、「IDとパスワードをお確かめ下さい」というメッセージが表示された場合、一度本サイトにログイン出来るかのご確認をお願いします。</li>",
      "id": 7,
      "login_url": "http://www.mizuhobank.co.jp/direct/start.html",
      "service_category_id": 2,
      "service_name": "みずほ銀行",
      "service_type": "B_MIZUHO",
      "yomigana": "ミズホギンコウ"
    },
    "aggregation_error": {
      "error_msg": "SecretQuestionException",
      "error_type": "FATAL",
      "id": 7,
      "msg_title": "要合言葉"
    },
    "exclusive_service_forms": [
      {
        "disp_order": 1,
        "encrypt_flag": 1,
        "format": "",
        "id": 13,
        "input_type": "alphameric",
        "name": "お客様番号",
        "note": "",
        "service_form_type": "ID1",
        "service_id": 7,
        "unique_flag": 1
      },
      {
        "disp_order": 2,
        "encrypt_flag": 1,
        "format": "",
        "id": 14,
        "input_type": "password",
        "name": "ログインパスワード",
        "note": "",
        "service_form_type": "PW1",
        "service_id": 7,
        "unique_flag": 0
      }
    ]
  }
}
```
