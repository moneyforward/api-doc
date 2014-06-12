# POST /api/v1/accounts
金融機関登録を行う

## Resrouce URL
https://moneyforward.com/api/v1/accounts

## Parameters
name | Description 
-----------|------------------------
account[service_id] <br> *required* | 金融機関ID
account[service_form_answers][i][:id] <br> *required* | サービスフォームID
account[service_form_answers][i][:value] <br> *required* | サービスフォームIDに対する値

## Example

### request

> **POST** https://moneyforward.com/api/v1/accounts

### request-body

    {
      "account": {
        "service_id": 1,
        "service_forms_answers": [
          {
            "id": 1,
            "value": "99999999"
          },
          {
            "id": 2,
            "value": "password_text"
          }
        ]
      }
    }

### response

    {
      "account": {
        "account_uid_hidden": "999*****",
        "created_at": "2014-05-28T20:46:04+09:00",
        "disp_name": null,
        "error_id": 0,
        "last_aggregated_at": null,
        "last_succeeded_at": "未取得",
        "memo": null,
        "message": null,
        "msg_flag": 0,
        "msg_time": null,
        "next_aggregate_at": null,
        "service_category_id": 2,
        "service_id": 1,
        "status": 1,
        "hashed_id": "e2RPphY9_-bdYZ1PBLMmjg==",
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
        },
        "exclusive_service_forms": [
          {
            "disp_order": 1,
            "encrypt_flag": 1,
            "format": "",
            "id": 1,
            "input_type": "alphameric",
            "name": "ご契約番号 ",
            "note": "(ハイフンの有無は問いません)",
            "service_form_type": "ID1",
            "service_id": 1,
            "unique_flag": 1
          },
          {
            "disp_order": 2,
            "encrypt_flag": 1,
            "format": "",
            "id": 2,
            "input_type": "password",
            "name": "IBログインパスワード",
            "note": "",
            "service_form_type": "PW1",
            "service_id": 1,
            "unique_flag": 0
          }
        ]
      }
    }