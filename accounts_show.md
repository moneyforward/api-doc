# 特定の口座の取得状況や資産額合計、ログインに必要な入力項目を得る

## 要求

### 必要な権限

`accounts`

### エンドポイント

```
GET https://moneyforward.com/api/v1/accounts/:id
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |
| パス | 必須 | `id` | [口座](accounts_index.md)の `hashed_id` |

### 例

```
GET https://moneyforward.com/api/v1/accounts/LlPqfqeeCZavwPBLmUy6xg==
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

| 名称 | 内容 |
| ---- | --- |
| `account[account_uid_hidden]` | 口座のidの一部を隠したもの (最大3文字が表示される) |
| `account[asset_sum]` | 資産の合計 |
| `account[disp_name]` | ユーザーが設定した口座の識別名 (未設定なら `null`) |
| `account[memo]` | ユーザーが設定したメモ |
| `account[message]` | 金融機関からユーザーへの通知 |
| `account[msg_flag]` | `true`: `message` を表示する, `false` (デフォルト): `message` を表示しない |
| `account[status]` | 金融機関からの情報の取得状況; `0`: 取得済み, `1`: 取得中、`2`: 取得エラー, `3`: 取得停止中 |
| `account[sub_accounts][i][sub_name]` | 金融機関の支店名 |
| `account[sub_accounts][i][sub_number]` | 口座番号 |
| `account[exclusive_service_forms]` | ログインに必要な全ての入力項目 |
| `account[exclusive_service_forms][i][encrypt_flag]` | 暗号化対象項目か否か |
| `account[exclusive_service_forms][i][input_type]` | `alphameric`: 数値, `password`: パスワード, `text`: 文字列, `checkbox`: チェックボックス, `radio`: ラジオボタン, `table`: 乱数表 |
| `account[exclusive_service_forms][i][format]` | 入力値を制約する正規表現; 空白制限なし; `input_type` が `radio` の場合は、全ての選択肢 |
| `account[exclusive_service_forms][i][note]` | 補足説明 |
| `account[exclusive_service_forms][i][service_form_type]` | 入力項目の識別子 |
| `account[exclusive_service_forms][i][unique_flag]` | 一意性が課されるか否か |
| `account[additional_requests]` | 全ての秘密の質問やワンタイムパスワード |
| `account[additional_requests][i][hashed_id]` | 秘密の質問やワンタイムパスワードの入力リクエストリスト |
| `account[additional_requests][i][message]` | 金融機関からユーザーへの通知 |
| `account[additional_requests][i][request_data]` | 質問 |

### 例

```
{
  "account": {
    "account_uid_hidden": "134*****",
    "created_at": "2014-05-29T19:55:16+09:00",
    "disp_name": null,
    "aggregation_error_id": 7,
    "last_aggregated_at": "2014-05-31T17:16:05+09:00",
    "last_succeeded_at": "未取得",
    "memo": null,
    "message": null,
    "msg_flag": 1,
    "msg_time": null,
    "next_aggregate_at": "2014-06-01T20:25:11+09:00",
    "service_category_id": 2,
    "service_id": 7,
    "status": 2,
    "hashed_id": "84dG3OLcZt_gLm66DESKzw==",
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
    ],
    "additional_requests": [
      {
        "hashed_id": "DMA8-glWM3Bgzmvkx0dJkQ==",
        "message": "合言葉／秘密の質問 への記入が必要です。",
        "request_data": "子供の頃の一番の親友の名前は何ですか"
      }
    ]
  }
}
```
