# マネーフォワードで口座を登録可能な全ての金融機関を得る

## 要求

### 必要な権限

なし

### エンドポイント

```
GET https://moneyforward.com/api/v1/services
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |
| クエリー | 任意; デフォルト: なし | `search_keyword` | このキーを元に金融機関名 (漢字もしくは読みがな) で検索する |
| クエリー | 任意; デフォルト: 全て; 複数個使用可 | `service_category_ids[]` | [金融機関の分類](service_categories_index.md)の `id` |
| クエリー | 任意; デフォルト: `1` | `page` | ページ番号 |
| クエリー | 任意; デフォルト: `200` | `limit` | 1ページ当たりの最大表示件数; 最大: `2000` |
| クエリー | 任意; デフォルト: なし　| `biz_flag` | 個人用口座・法人用口座に絞って検索する。`0`なら個人用口座、`1`なら法人用口座。|

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
    "total_count": 1562,
    "services": [
        {
            "service": {
                "id": 1144,
                "service_category_id": 2,
                "category_type": "BANK",
                "service_type": "B_SHINKIN_1206",
                "category_name": "銀行",
                "service_name": "アイオー信用金庫",
                "is_biz": false,
                "login_url": "https://www11.ib.shinkin-ib.jp/webbk/login/b-prelogin.do?bankcode=MTIwNg==",
                "yomigana": "アイオーシンヨウキンコ",
                "description": "<li>口座番号ではなくオンラインバンキング用のログイン情報となります。オンラインバンキングの手続きは各金融機関へお問い合わせ下さい。</li><li>登録後、「IDとパスワードをお確かめ下さい」というメッセージが表示された場合、一度金融機関サイトにログイン出来るかのご確認をお願いします。</li>",
                "code": "1206"
            }
        },
        {
            "service": {
                "id": 157,
                "service_category_id": 2,
                "category_type": "BANK",
                "service_type": "B_AICHI",
                "category_name": "銀行",
                "service_name": "愛知銀行",
                "is_biz": false,
                "login_url": "https://www.aidirect.aichibank.co.jp/ib/index.do?PT=BS&CCT0080=0542",
                "yomigana": "アイチギンコウ",
                "description": null,
                "code": "0542"
            }
        },
        {
            "service": {
                "id": 1027,
                "service_category_id": 2,
                "category_type": "BANK",
                "service_type": "B_SHINKUMI_2451",
                "category_name": "銀行",
                "service_name": "愛知県中央信用組合",
                "is_biz": false,
                "login_url": "https://www.parasol.anser.ne.jp/ib/index.do?PT=BS&CCT0080=2451",
                "yomigana": "アイチケンチュウオウシンヨウクミアイ",
                "description": "<li>口座番号ではなくオンラインバンキング用のログイン情報となります。オンラインバンキングの手続きは各金融機関へお問い合わせ下さい。</li><li>登録後、「合言葉の入力が必要です」というメッセージが表示された場合、金融機関サイトへのログインに用いる答えの入力をお願いします。</li><li>登録後、「IDとパスワードをお確かめ下さい」というメッセージが表示された場合、一度金融機関サイトにログイン出来るかのご確認をお願いします。</li>",
                "code": "2451"
            }
        }
    ]
}
```
