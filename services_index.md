# マネーフォワードで口座を登録可能な全ての金融機関を閲覧する

## 要求

### エンドポイント

```
GET https://moneyforward.com/api/v1/services
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで `アクセストークン` は [`access_token`](token.md) の値 |
| クエリー | 任意; デフォルト: なし | `search_keyword` | このキーを元に金融機関名 (漢字もしくは読みがな) で検索する |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `service_category_ids[]` | [金融機関の分類](service_categories_index.md)の `id` |
| クエリー | 任意; デフォルト: `1` | `page` | ページ番号 |
| クエリー | 任意; デフォルト: `200` | `limit` | 1ページ当たりの最大表示件数; 最大: `2000` |

### 例

```
GET https://moneyforward.com/api/v1/services?search_keyword=ミツビシ&service_category_ids[]=1&service_category_ids[]=2&limit=20
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

[GET https://moneyforward.com/api/v1/services/:id](services_show.md) の内容を `services[i]` として配列にしたもの

### 例

```
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
```
