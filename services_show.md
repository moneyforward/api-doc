# マネーフォワードで登録可能な特定の金融機関のログインに必要な入力項目を得る

## 要求

### エンドポイント

```
GET https://moneyforward.com/api/v1/services/:id
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで `アクセストークン` は [`access_token`](token.md) の値 |
| パス| 必須 | `id` | [金融機関](services_index.md)の `id` |

### 例

```
GET https://moneyforward.com/api/v1/services/1
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

| 名称 | 内容 |
| ---- | --- |
| `service[id]` | 金融機関の `id` |
| `service[service_type]` | 金融機関固有の記号 |
| `service[service_name]` | 金融機関の名前 |
| `service[yomigana]` | 金融機関の名前の読み仮名 |
| `service[category_name]` | 金融機関の分類 |
| `service[category_type]` | 金融機関の分類を表す固有の記号 |
| `service[description]` | 金融機関へのログインについての説明 |
| `service[login_url]` | 金融機関サイトへのログイン先 |
| `service[exclusive_service_forms]` | ログインに必要な全ての入力項目 |
| `service[exclusive_service_forms][i][id]` | 入力項目の `id` |
| `service[exclusive_service_forms][i][disp_order]` | マネーフォワードサービスで表示される時の表示順 |
| `service[exclusive_service_forms][i][encrypt_flag]` | 暗号化対象項目か否か |
| `service[exclusive_service_forms][i][input_type]` | `alphameric`: 数値, `password`: パスワード, `text`: 文字列, `checkbox`: チェックボックス, `radio`: ラジオボタン, `table`: 乱数表 |
| `service[exclusive_service_forms][i][format]` | 入力値を制約する正規表現; 空白制限なし; `input_type` が `radio` の場合は、全ての選択肢 |
| `service[exclusive_service_forms][i][name]` | 金融機関サイトへのログイン時に表示される文言 |
| `service[exclusive_service_forms][i][note]` | 入力内容の補足説明 |
| `service[exclusive_service_forms][i][service_form_type]` | 入力項目の識別子 |
| `service[exclusive_service_forms][i][unique_flag]` | 一意性が課されるか否か |

### 例

```
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
```
