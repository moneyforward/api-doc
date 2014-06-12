# GET /api/v1/accounts/:id
登録済み金融機関情報を返す。取得状況ステータスや、資産額合計も返す。
登録フォームも返す。

## Resrouce URL
https://moneyforward.com/api/v1/accounts/:id

## Data definition

name | Description 
-----------|------------------------
account_uid_hidden | 金融機関登録したIDをマスキングしたID（最大３文字が非マスキング）
asset_sum | 金融機関内で保有する資産合計
disp_name | ユーザー自身が設定した登録金融機関識別名（未設定ならnull）
memo | ユーザーが設定した登録金融機関に関するメモ
msg_flag | true: messageを表示する false(default): message非表示
message | ユーザーに通知する必要があるメッセージ
status | アグリゲーションの状態を表す 0:正常（取得済み）、1:取得中、2:取得エラー、3:取得停止中
exclusive_service_forms | 金融機関登録に必要なフォーム情報のリスト
exclusive_service_form[encrypt_flag] | 暗号化対象項目
exclusive_service_form[format] | 入力値の制約を正規表現チェック。ブランクは正規表現によるチェックなし。input_typeが'radio' の場合は、radioボタンの選択項目リスト
exclusive_service_form[input_type] | alphameric: 数値フィールド、 password: パスワードフィールド、text: 通常文字列フィールド、checkbox: チェックボックスフィールド、radio:ラジオボタンフィールド、table,*:乱数表
exclusive_service_form[note] | 入力値に関する補足説明
exclusive_service_form[service_form_type] | 入力フォームの識別子
exclusive_service_form[unique_flag] | ユニークチェックに利用するフィールドかどうか
additional_requests | 秘密の質問やワンタイムパスワードの入力リクエストリスト


## Parameters
name | Description 
-----------|------------------------
id  <br> *required* | 登録金融機関ID *hashed*

 
## Example
***
> **GET** *https://moneyforward.com/api/v1/accounts/LlPqfqeeCZavwPBLmUy6xg==*

    {
      "account": {
        "account_uid_hidden": "134*****",
        "created_at": "2014-05-29T19:55:16+09:00",
        "disp_name": null,
        "error_id": 7,
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