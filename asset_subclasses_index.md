# 資産の全ての中分類を得る

## 要求

### 必要な権限

なし

### エンドポイント

```
GET https://moneyforward.com/api/v1/asset_subclasses
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |

### 例

```
GET https://moneyforward.com/api/v1/asset_subclasses
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### パラメーター

| 名称 | 内容 |
| ---- | --- |
| `i[asset_subclass][liquid]` | 資産の流動性; 0から100までの数値 |

### 例

```
[
  {
    "asset_subclass": {
      "asset_class_id": 2,
      "asset_subclass_name": "国債",
      "asset_subclass_type": "JGB",
      "disp_order": 1,
      "id": 7,
      "liquid": 91
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 3,
      "asset_subclass_name": "投資信託",
      "asset_subclass_type": "MUTUAL_FUND",
      "disp_order": 1,
      "id": 12,
      "liquid": 85
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 4,
      "asset_subclass_name": "国内株",
      "asset_subclass_type": "DOM_EQ",
      "disp_order": 1,
      "id": 14,
      "liquid": 78
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 7,
      "asset_subclass_name": "建物(自宅)",
      "asset_subclass_type": "HOME",
      "disp_order": 1,
      "id": 28,
      "liquid": 24
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 8,
      "asset_subclass_name": "積立型保険",
      "asset_subclass_type": "INSURANCE",
      "disp_order": 1,
      "id": 32,
      "liquid": 55
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 9,
      "asset_subclass_name": "国民年金",
      "asset_subclass_type": "KOKUMIN_PNS",
      "disp_order": 1,
      "id": 33,
      "liquid": 20
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 11,
      "asset_subclass_name": "住宅ローン",
      "asset_subclass_type": "HOUSING_LOAN",
      "disp_order": 1,
      "id": 44,
      "liquid": 1
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 12,
      "asset_subclass_name": "ポイント・マイル",
      "asset_subclass_type": "POINT",
      "disp_order": 1,
      "id": 48,
      "liquid": 80
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 1,
      "asset_subclass_name": "現金",
      "asset_subclass_type": "CASH",
      "disp_order": 1,
      "id": 49,
      "liquid": 100
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 13,
      "asset_subclass_name": "保証金・証拠金(信用)",
      "asset_subclass_type": "MDEPO_MGN",
      "disp_order": 1,
      "id": 62,
      "liquid": 79
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 6,
      "asset_subclass_name": "証拠金(先物OP)",
      "asset_subclass_type": "MDEPO_DRV",
      "disp_order": 1,
      "id": 63,
      "liquid": 81
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 5,
      "asset_subclass_name": "証拠金(FX)",
      "asset_subclass_type": "MDEPO_FX",
      "disp_order": 1,
      "id": 64,
      "liquid": 82
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 2,
      "asset_subclass_name": "社債",
      "asset_subclass_type": "CORP_BD",
      "disp_order": 2,
      "id": 8,
      "liquid": 90
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 4,
      "asset_subclass_name": "米国株",
      "asset_subclass_type": "US_EQ",
      "disp_order": 2,
      "id": 15,
      "liquid": 77
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 5,
      "asset_subclass_name": "店頭FX",
      "asset_subclass_type": "OTC_FX",
      "disp_order": 2,
      "id": 18,
      "liquid": 34
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 6,
      "asset_subclass_name": "指数先物",
      "asset_subclass_type": "IDX_FUT",
      "disp_order": 2,
      "id": 22,
      "liquid": 30
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 7,
      "asset_subclass_name": "建物(投資・事業用)",
      "asset_subclass_type": "BUILDING",
      "disp_order": 2,
      "id": 29,
      "liquid": 23
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 9,
      "asset_subclass_name": "厚生年金",
      "asset_subclass_type": "KOUSEI_PNS",
      "disp_order": 2,
      "id": 34,
      "liquid": 19
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 10,
      "asset_subclass_name": "自動車",
      "asset_subclass_type": "CAR",
      "disp_order": 2,
      "id": 41,
      "liquid": 17
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 11,
      "asset_subclass_name": "自動車ローン",
      "asset_subclass_type": "CAR_LOAN",
      "disp_order": 2,
      "id": 45,
      "liquid": 2
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 1,
      "asset_subclass_name": "電子マネー",
      "asset_subclass_type": "E_MONEY",
      "disp_order": 2,
      "id": 50,
      "liquid": 97
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 3,
      "asset_subclass_name": "外国投資信託",
      "asset_subclass_type": "FOR_MF",
      "disp_order": 2,
      "id": 52,
      "liquid": 74
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 13,
      "asset_subclass_name": "国内株(信用)",
      "asset_subclass_type": "DOM_EQ_MGN",
      "disp_order": 2,
      "id": 57,
      "liquid": 15
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 1,
      "asset_subclass_name": "普通預金",
      "asset_subclass_type": "ORD_DEPO",
      "disp_order": 3,
      "id": 1,
      "liquid": 99
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 2,
      "asset_subclass_name": "外債",
      "asset_subclass_type": "FOR_BD",
      "disp_order": 3,
      "id": 9,
      "liquid": 89
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 4,
      "asset_subclass_name": "中国株",
      "asset_subclass_type": "CN_EQ",
      "disp_order": 3,
      "id": 16,
      "liquid": 76
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 5,
      "asset_subclass_name": "くりっく365",
      "asset_subclass_type": "TFE_FX",
      "disp_order": 3,
      "id": 19,
      "liquid": 33
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 6,
      "asset_subclass_name": "指数OP",
      "asset_subclass_type": "IDX_OPT",
      "disp_order": 3,
      "id": 23,
      "liquid": 29
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 7,
      "asset_subclass_name": "土地(自宅)",
      "asset_subclass_type": "HOME_LAND",
      "disp_order": 3,
      "id": 30,
      "liquid": 22
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 9,
      "asset_subclass_name": "共済年金",
      "asset_subclass_type": "KYOSAI_PNS",
      "disp_order": 3,
      "id": 35,
      "liquid": 67
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 10,
      "asset_subclass_name": "貴金属・宝石類",
      "asset_subclass_type": "JEWELRY",
      "disp_order": 3,
      "id": 42,
      "liquid": 10
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 11,
      "asset_subclass_name": "キャッシング・カードローン",
      "asset_subclass_type": "CASHING_LOAN",
      "disp_order": 3,
      "id": 46,
      "liquid": 4
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 3,
      "asset_subclass_name": "中期国債ファンド",
      "asset_subclass_type": "MGF",
      "disp_order": 3,
      "id": 53,
      "liquid": 86
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 13,
      "asset_subclass_name": "米国株(信用)",
      "asset_subclass_type": "US_EQ_MGN",
      "disp_order": 3,
      "id": 58,
      "liquid": 14
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 1,
      "asset_subclass_name": "定期預金",
      "asset_subclass_type": "TERM_DEPO",
      "disp_order": 4,
      "id": 2,
      "liquid": 95
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 2,
      "asset_subclass_name": "仕組み債",
      "asset_subclass_type": "STRUCT_BD",
      "disp_order": 4,
      "id": 10,
      "liquid": 88
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 5,
      "asset_subclass_name": "大証FX",
      "asset_subclass_type": "OSE_FX",
      "disp_order": 4,
      "id": 20,
      "liquid": 32
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 6,
      "asset_subclass_name": "CFD",
      "asset_subclass_type": "CFD",
      "disp_order": 4,
      "id": 24,
      "liquid": 28
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 7,
      "asset_subclass_name": "土地(投資・事業用)",
      "asset_subclass_type": "INVEST_LAND",
      "disp_order": 4,
      "id": 31,
      "liquid": 21
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 9,
      "asset_subclass_name": "企業年金",
      "asset_subclass_type": "KIGYO_PNS",
      "disp_order": 4,
      "id": 36,
      "liquid": 18
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 10,
      "asset_subclass_name": "その他",
      "asset_subclass_type": "OTHER_ASSET",
      "disp_order": 4,
      "id": 43,
      "liquid": 16
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 11,
      "asset_subclass_name": "その他",
      "asset_subclass_type": "OTHER_LIA",
      "disp_order": 4,
      "id": 47,
      "liquid": 3
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 3,
      "asset_subclass_name": "MMF",
      "asset_subclass_type": "MMF",
      "disp_order": 4,
      "id": 54,
      "liquid": 96
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 4,
      "asset_subclass_name": "外国株",
      "asset_subclass_type": "FOR_EQ",
      "disp_order": 4,
      "id": 55,
      "liquid": 73
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 13,
      "asset_subclass_name": "中国株(信用)",
      "asset_subclass_type": "CN_EQ_MGN",
      "disp_order": 4,
      "id": 59,
      "liquid": 13
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 1,
      "asset_subclass_name": "外貨預金",
      "asset_subclass_type": "FOR_DEPO",
      "disp_order": 5,
      "id": 3,
      "liquid": 94
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 3,
      "asset_subclass_name": "外貨MMF",
      "asset_subclass_type": "FOR_MMF",
      "disp_order": 5,
      "id": 4,
      "liquid": 93
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 2,
      "asset_subclass_name": "その他債券",
      "asset_subclass_type": "OTHER_BD",
      "disp_order": 5,
      "id": 11,
      "liquid": 87
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 5,
      "asset_subclass_name": "その他FX",
      "asset_subclass_type": "OTHER_FX",
      "disp_order": 5,
      "id": 21,
      "liquid": 31
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 6,
      "asset_subclass_name": "くりっく株365",
      "asset_subclass_type": "TFE_EQ",
      "disp_order": 5,
      "id": 25,
      "liquid": 27
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 9,
      "asset_subclass_name": "厚生年金基金",
      "asset_subclass_type": "KOUSEI_K_PNS",
      "disp_order": 5,
      "id": 37,
      "liquid": 68
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 4,
      "asset_subclass_name": "未公開株式",
      "asset_subclass_type": "PRIVATE_EQ",
      "disp_order": 5,
      "id": 56,
      "liquid": 72
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 13,
      "asset_subclass_name": "外国株(信用)",
      "asset_subclass_type": "FOR_EQ_MGN",
      "disp_order": 5,
      "id": 60,
      "liquid": 12
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 1,
      "asset_subclass_name": "預り金・MRF",
      "asset_subclass_type": "MRF",
      "disp_order": 6,
      "id": 5,
      "liquid": 98
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 3,
      "asset_subclass_name": "その他投信",
      "asset_subclass_type": "OTHER_FUND",
      "disp_order": 6,
      "id": 13,
      "liquid": 84
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 4,
      "asset_subclass_name": "その他株式",
      "asset_subclass_type": "OTHER_EQ",
      "disp_order": 6,
      "id": 17,
      "liquid": 75
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 6,
      "asset_subclass_name": "商品先物",
      "asset_subclass_type": "COMM_FUT",
      "disp_order": 6,
      "id": 26,
      "liquid": 26
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 6,
      "asset_subclass_name": "その他先物OP",
      "asset_subclass_type": "OTHER_DRV",
      "disp_order": 6,
      "id": 27,
      "liquid": 25
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 9,
      "asset_subclass_name": "国民年金基金",
      "asset_subclass_type": "KOKUMIN_K_PNS",
      "disp_order": 6,
      "id": 38,
      "liquid": 69
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 13,
      "asset_subclass_name": "その他株式(信用)",
      "asset_subclass_type": "OTHER_EQ_MGN",
      "disp_order": 6,
      "id": 61,
      "liquid": 11
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 9,
      "asset_subclass_name": "確定拠出年金",
      "asset_subclass_type": "KAKUTEI_PNS",
      "disp_order": 7,
      "id": 39,
      "liquid": 70
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 1,
      "asset_subclass_name": "保証金・証拠金",
      "asset_subclass_type": "MDEPO",
      "disp_order": 7,
      "id": 51,
      "liquid": 83
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 1,
      "asset_subclass_name": "その他預金",
      "asset_subclass_type": "OTHER_DEPO",
      "disp_order": 8,
      "id": 6,
      "liquid": 92
    }
  },
  {
    "asset_subclass": {
      "asset_class_id": 9,
      "asset_subclass_name": "私的年金",
      "asset_subclass_type": "PRIVATE_PNS",
      "disp_order": 8,
      "id": 40,
      "liquid": 66
    }
  }
]
```

