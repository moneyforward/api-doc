# GET /api/v1/services/:id
金融機関情報を登録フォーム付きで返す

## Resrouce URL
https://moneyforward.com/api/v1/services/:id

## Parameters
name | Description 
-----------|------------------------
id <br> *required*  | 金融機関のID
 
## Example
***
> **GET** *https://moneyforward.com/api/v1/services/1*

    {
      "service": {
        "category_name": "銀行",
        "category_type": "BANK",
        "code": "0005",
        "description": "<li>口座番号ではなくオンラインバンキング用のログイン情報となります。オンラインバンキングの手続きは各金融機関へお問い合わせ下さい。</li><li>登録後、「IDとパスワードをお確かめ下さい」というメッセージが表示された場合、一度本サイトにログイン出来るかのご確認をお願いします。</li>",
        "id": 1,
        "login_url": "https://entry11.bk.mufg.jp/ibg/dfw/APLIN/loginib/login?_TRANID=AA000_001",
        "service_name": "三菱東京UFJ銀行",
        "service_type": "B_MUFG",
        "yomigana": "ミツビシトウキョウユーエフジェイギンコウ",
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