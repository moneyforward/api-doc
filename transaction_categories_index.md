# 入出金の全ての大分類(及びその中のユーザー作成の中分類)を得る

## 要求

### 必要な権限

`transactions`

### エンドポイント

```
GET https://moneyforward.com/api/v1/transactions/categories
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |

### 例

```
GET https://moneyforward.com/api/v1/transactions/categories
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

| 名称 | 内容 |
| ---- | --- |
| `large_categories[i][id]` | 大項目の `id` |
| `large_categories[i][name]` | 大項目の名称 |
| `large_categories[i][income]` | `true`: 収入, `false`: 支出 |
| `large_categories[i][middle_categories][j][id]` | 中項目の `id` |
| `large_categories[i][middle_categories][j][name]` | 中項目の名称 |

### 例

```
 {
   "large_categories" : [
     {
       "id" : 0,
       "name" : "未分類",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 0,
           "name" : "未分類"
         }
       ]
     },
     {
       "id" : 1,
       "name" : "収入",
       "income" : true,
       "middle_categories" : [
         {
           "id" : 1,
           "name" : "給与"
         },
         {
           "id" : 2,
           "name" : "一時所得"
         },
         {
           "id" : 3,
           "name" : "事業・副業"
         },
         {
           "id" : 4,
           "name" : "年金"
         },
         {
           "id" : 5,
           "name" : "その他入金"
         },
         {
           "id" : 89,
           "name" : "配当所得"
         },
         {
           "id" : 90,
           "name" : "不動産所得"
         },
         {
           "id" : 104,
           "name" : "不明な入金"
         }
       ]
     },
     {
       "id" : 3,
       "name" : "現金・カード",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 8,
           "name" : "ATM引き出し"
         },
         {
           "id" : 9,
           "name" : "カード引き落とし"
         },
         {
           "id" : 76,
           "name" : "電子マネー"
         },
         {
           "id" : 77,
           "name" : "その他現金・カード"
         },
         {
           "id" : 103,
           "name" : "使途不明金"
         }
       ]
     },
     {
       "id" : 4,
       "name" : "住宅",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 10,
           "name" : "家賃・地代"
         },
         {
           "id" : 11,
           "name" : "ローン返済"
         },
         {
           "id" : 12,
           "name" : "管理費・積立金"
         },
         {
           "id" : 13,
           "name" : "地震・火災保険"
         },
         {
           "id" : 78,
           "name" : "その他住宅"
         },
         {
           "id" : 107,
           "name" : "住宅"
         }
       ]
     },
     {
       "id" : 5,
       "name" : "水道・光熱費",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 14,
           "name" : "電気代"
         },
         {
           "id" : 15,
           "name" : "ガス・灯油代"
         },
         {
           "id" : 16,
           "name" : "水道代"
         },
         {
           "id" : 79,
           "name" : "その他水道・光熱費"
         },
         {
           "id" : 108,
           "name" : "光熱費"
         }
       ]
     },
     {
       "id" : 6,
       "name" : "通信費",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 17,
           "name" : "携帯電話"
         },
         {
           "id" : 18,
           "name" : "インターネット"
         },
         {
           "id" : 19,
           "name" : "固定電話"
         },
         {
           "id" : 22,
           "name" : "放送視聴料"
         },
         {
           "id" : 23,
           "name" : "情報サービス"
         },
         {
           "id" : 80,
           "name" : "その他通信費"
         },
         {
           "id" : 102,
           "name" : "宅配便・運送"
         }
       ]
     },
     {
       "id" : 7,
       "name" : "自動車",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 24,
           "name" : "自動車ローン"
         },
         {
           "id" : 25,
           "name" : "ガソリン"
         },
         {
           "id" : 26,
           "name" : "駐車場"
         },
         {
           "id" : 27,
           "name" : "車両"
         },
         {
           "id" : 28,
           "name" : "車検・整備"
         },
         {
           "id" : 75,
           "name" : "道路料金"
         },
         {
           "id" : 81,
           "name" : "その他自動車"
         },
         {
           "id" : 101,
           "name" : "自動車保険"
         }
       ]
     },
     {
       "id" : 8,
       "name" : "保険",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 29,
           "name" : "生命保険"
         },
         {
           "id" : 30,
           "name" : "医療保険"
         },
         {
           "id" : 31,
           "name" : "その他保険"
         }
       ]
     },
     {
       "id" : 9,
       "name" : "税・社会保障",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 32,
           "name" : "所得税・住民税"
         },
         {
           "id" : 33,
           "name" : "年金保険料"
         },
         {
           "id" : 34,
           "name" : "健康保険"
         },
         {
           "id" : 35,
           "name" : "その他税・社会保障"
         }
       ]
     },
     {
       "id" : 10,
       "name" : "日用品",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 36,
           "name" : "日用品"
         },
         {
           "id" : 37,
           "name" : "ドラッグストア"
         },
         {
           "id" : 38,
           "name" : "おこづかい"
         },
         {
           "id" : 40,
           "name" : "ペット用品"
         },
         {
           "id" : 46,
           "name" : "子育て用品"
         },
         {
           "id" : 82,
           "name" : "その他日用品"
         },
         {
           "id" : 95,
           "name" : "タバコ"
         }
       ]
     },
     {
       "id" : 11,
       "name" : "食費",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 41,
           "name" : "食料品"
         },
         {
           "id" : 42,
           "name" : "外食"
         },
         {
           "id" : 43,
           "name" : "カフェ"
         },
         {
           "id" : 83,
           "name" : "その他食費"
         },
         {
           "id" : 91,
           "name" : "朝ご飯"
         },
         {
           "id" : 92,
           "name" : "昼ご飯"
         },
         {
           "id" : 93,
           "name" : "夜ご飯"
         },
         {
           "id" : 105,
           "name" : "食費"
         }
       ]
     },
     {
       "id" : 12,
       "name" : "教養・教育",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 20,
           "name" : "書籍"
         },
         {
           "id" : 21,
           "name" : "新聞・雑誌"
         },
         {
           "id" : 45,
           "name" : "習いごと"
         },
         {
           "id" : 47,
           "name" : "学費"
         },
         {
           "id" : 48,
           "name" : "塾"
         },
         {
           "id" : 84,
           "name" : "その他教養・教育"
         }
       ]
     },
     {
       "id" : 13,
       "name" : "趣味・娯楽",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 49,
           "name" : "アウトドア"
         },
         {
           "id" : 50,
           "name" : "スポーツ"
         },
         {
           "id" : 51,
           "name" : "映画・音楽・ゲーム"
         },
         {
           "id" : 52,
           "name" : "本"
         },
         {
           "id" : 53,
           "name" : "旅行"
         },
         {
           "id" : 54,
           "name" : "秘密の趣味"
         },
         {
           "id" : 85,
           "name" : "その他趣味・娯楽"
         },
         {
           "id" : 110,
           "name" : "ゴルフ"
         }
       ]
     },
     {
       "id" : 14,
       "name" : "衣服・美容",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 55,
           "name" : "衣服"
         },
         {
           "id" : 56,
           "name" : "クリーニング"
         },
         {
           "id" : 57,
           "name" : "美容院・理髪"
         },
         {
           "id" : 58,
           "name" : "化粧品"
         },
         {
           "id" : 59,
           "name" : "アクセサリー"
         },
         {
           "id" : 86,
           "name" : "その他衣服・美容"
         }
       ]
     },
     {
       "id" : 15,
       "name" : "健康・医療",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 60,
           "name" : "フィットネス"
         },
         {
           "id" : 61,
           "name" : "ボディケア"
         },
         {
           "id" : 62,
           "name" : "医療費"
         },
         {
           "id" : 63,
           "name" : "薬"
         },
         {
           "id" : 87,
           "name" : "その他健康・医療"
         }
       ]
     },
     {
       "id" : 16,
       "name" : "特別な支出",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 66,
           "name" : "住宅・リフォーム"
         },
         {
           "id" : 67,
           "name" : "家具・家電"
         },
         {
           "id" : 88,
           "name" : "その他特別な支出"
         }
       ]
     },
     {
       "id" : 18,
       "name" : "その他",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 68,
           "name" : "雑費"
         },
         {
           "id" : 69,
           "name" : "仕送り"
         },
         {
           "id" : 70,
           "name" : "事業経費"
         },
         {
           "id" : 71,
           "name" : "事業原価"
         },
         {
           "id" : 72,
           "name" : "事業投資"
         },
         {
           "id" : 94,
           "name" : "寄付金"
         }
       ]
     },
     {
       "id" : 20,
       "name" : "交通費",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 39,
           "name" : "その他交通費"
         },
         {
           "id" : 96,
           "name" : "電車"
         },
         {
           "id" : 97,
           "name" : "バス"
         },
         {
           "id" : 98,
           "name" : "飛行機"
         },
         {
           "id" : 99,
           "name" : "タクシー"
         },
         {
           "id" : 106,
           "name" : "交通費"
         }
       ]
     },
     {
       "id" : 21,
       "name" : "交際費",
       "income" : false,
       "middle_categories" : [
         {
           "id" : 44,
           "name" : "飲み会"
         },
         {
           "id" : 64,
           "name" : "冠婚葬祭"
         },
         {
           "id" : 65,
           "name" : "プレゼント代"
         },
         {
           "id" : 100,
           "name" : "その他交際費"
         },
         {
           "id" : 109,
           "name" : "交際費"
         }
       ]
     }
   ]
 }
```
