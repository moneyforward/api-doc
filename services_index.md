# GET /api/v1/services

マネーフォワードで登録可能な金融機関を返します。デフォルトでは２００件の金融機関を返します。
キーワードを指定することにより、金融機関名（漢字もしくは読みがな）にて検索可能です。

## Resrouce URL
https://moneyforward.com/api/v1/services

## Data definition

name | Description 
-----------|------------------------
code | 銀行コード等

## Parameters
name | Description 
-----------|------------------------
search_keyword <br /> *optional* | 金融機関検索のサーチキー。このキーを元に金融機関名（漢字もしくは読みがな）で検索します
service_category_ids <br> *optional*  | 金融機関のサービスカテゴリーID *Array*
page <br> *optional*  | ページ番号
limit <br> *optional*  | 1ページ辺りのエレメント数。最大2000。デフォルト200。

## Example
***
> **GET** *https://moneyforward.com/api/v1/services?search_keyword=ミツビシ&service_category_ids[]=2&service_category_ids[]=3&page=1&limit=3*

    {
      "limit": 3,
      "offset": 0,
      "total_count": 4,
      "services": [
        {
          "service": {
            "category_name": "銀行",
            "category_type": "BANK",
            "code": "2820",
            "description": "<li>口座番号ではなくオンラインバンキング用のログイン情報となります。オンラインバンキングの手続きは各金融機関へお問い合わせ下さい。</li><li>登録後、「合言葉の入力が必要です」というメッセージが表示された場合、本サイトへのログインに用いる答えの入力をお願いします。</li><li>登録後、「IDとパスワードをお確かめ下さい」というメッセージが表示された場合、一度本サイトにログイン出来るかのご確認をお願いします。</li>",
            "id": 1045,
            "login_url": "https://www2.paweb.anser.or.jp/BS?CCT0080=2820",
            "service_category_id": 2,
            "service_name": "長崎三菱信用組合",
            "service_type": "B_SHINKUMI_2820",
            "yomigana": "ナガサキミツビシシンヨウクミアイ"
          }
        },
        {
          "service": {
            "category_name": "銀行",
            "category_type": "BANK",
            "code": "0005",
            "description": "<li>口座番号ではなくオンラインバンキング用のログイン情報となります。オンラインバンキングの手続きは各金融機関へお問い合わせ下さい。</li><li>登録後、「IDとパスワードをお確かめ下さい」というメッセージが表示された場合、一度本サイトにログイン出来るかのご確認をお願いします。</li>",
            "id": 1,
            "login_url": "https://entry11.bk.mufg.jp/ibg/dfw/APLIN/loginib/login?_TRANID=AA000_001",
            "service_category_id": 2,
            "service_name": "三菱東京UFJ銀行",
            "service_type": "B_MUFG",
            "yomigana": "ミツビシトウキョウユーエフジェイギンコウ"
          }
        },
        {
          "service": {
            "category_name": "銀行",
            "category_type": "BANK",
            "code": "0288",
            "description": "<li>口座番号ではなくオンラインバンキング用のログイン情報となります。オンラインバンキングの手続きは各金融機関へお問い合わせ下さい。</li><li>登録後、「IDとパスワードをお確かめ下さい」というメッセージが表示された場合、一度本サイトにログイン出来るかのご確認をお願いします。</li>",
            "id": 1482,
            "login_url": "https://www.direct.tr.mufg.jp",
            "service_category_id": 2,
            "service_name": "三菱UFJ信託銀行",
            "service_type": "B_TR_MUFG",
            "yomigana": "ミツビシユーエフジェイシンタクギンコウ"
          }
        }
      ]
    }