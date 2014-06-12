# GET /api/v1/asset_subclasses

資産クラスマスタをさらに細かく分類したマスタを返します。

## Resrouce URL
https://moneyforward.com/api/v1/asset_subclasses

## Data definition

name | Description 
-----------|------------------------
liquid | 資産の流動性の高さを表します。0~100で、100がmaxです。

## Parameters

nothing

## Example
***
> **GET** *https://moneyforward.com/api/v1/asset_subclasses*

    [
      {
        "asset_subclass": {
          "asset_class_id": 2,
          "asset_subclass_name": "国債",
          "asset_subclass_type": "JGB",
          "id": 7,
          "liquid": 91
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 3,
          "asset_subclass_name": "投資信託",
          "asset_subclass_type": "MUTUAL_FUND",
          "id": 12,
          "liquid": 85
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 4,
          "asset_subclass_name": "国内株",
          "asset_subclass_type": "DOM_EQ",
          "id": 14,
          "liquid": 78
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 7,
          "asset_subclass_name": "建物(自宅)",
          "asset_subclass_type": "HOME",
          "id": 28,
          "liquid": 24
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 8,
          "asset_subclass_name": "積立型保険",
          "asset_subclass_type": "INSURANCE",
          "id": 32,
          "liquid": 55
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 9,
          "asset_subclass_name": "国民年金",
          "asset_subclass_type": "KOKUMIN_PNS",
          "id": 33,
          "liquid": 20
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 11,
          "asset_subclass_name": "住宅ローン",
          "asset_subclass_type": "HOUSING_LOAN",
          "id": 44,
          "liquid": 1
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 12,
          "asset_subclass_name": "ポイント・マイル",
          "asset_subclass_type": "POINT",
          "id": 48,
          "liquid": 80
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 1,
          "asset_subclass_name": "現金",
          "asset_subclass_type": "CASH",
          "id": 49,
          "liquid": 100
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 13,
          "asset_subclass_name": "保証金・証拠金(信用)",
          "asset_subclass_type": "MDEPO_MGN",
          "id": 62,
          "liquid": 79
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 6,
          "asset_subclass_name": "証拠金(先物OP)",
          "asset_subclass_type": "MDEPO_DRV",
          "id": 63,
          "liquid": 81
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 5,
          "asset_subclass_name": "証拠金(FX)",
          "asset_subclass_type": "MDEPO_FX",
          "id": 64,
          "liquid": 82
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 2,
          "asset_subclass_name": "社債",
          "asset_subclass_type": "CORP_BD",
          "id": 8,
          "liquid": 90
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 4,
          "asset_subclass_name": "米国株",
          "asset_subclass_type": "US_EQ",
          "id": 15,
          "liquid": 77
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 5,
          "asset_subclass_name": "店頭FX",
          "asset_subclass_type": "OTC_FX",
          "id": 18,
          "liquid": 34
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 6,
          "asset_subclass_name": "指数先物",
          "asset_subclass_type": "IDX_FUT",
          "id": 22,
          "liquid": 30
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 7,
          "asset_subclass_name": "建物(投資・事業用)",
          "asset_subclass_type": "BUILDING",
          "id": 29,
          "liquid": 23
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 9,
          "asset_subclass_name": "厚生年金",
          "asset_subclass_type": "KOUSEI_PNS",
          "id": 34,
          "liquid": 19
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 10,
          "asset_subclass_name": "自動車",
          "asset_subclass_type": "CAR",
          "id": 41,
          "liquid": 17
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 11,
          "asset_subclass_name": "自動車ローン",
          "asset_subclass_type": "CAR_LOAN",
          "id": 45,
          "liquid": 2
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 1,
          "asset_subclass_name": "電子マネー",
          "asset_subclass_type": "E_MONEY",
          "id": 50,
          "liquid": 97
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 3,
          "asset_subclass_name": "外国投資信託",
          "asset_subclass_type": "FOR_MF",
          "id": 52,
          "liquid": 74
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 13,
          "asset_subclass_name": "国内株(信用)",
          "asset_subclass_type": "DOM_EQ_MGN",
          "id": 57,
          "liquid": 15
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 1,
          "asset_subclass_name": "普通預金",
          "asset_subclass_type": "ORD_DEPO",
          "id": 1,
          "liquid": 99
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 2,
          "asset_subclass_name": "外債",
          "asset_subclass_type": "FOR_BD",
          "id": 9,
          "liquid": 89
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 4,
          "asset_subclass_name": "中国株",
          "asset_subclass_type": "CN_EQ",
          "id": 16,
          "liquid": 76
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 5,
          "asset_subclass_name": "くりっく365",
          "asset_subclass_type": "TFE_FX",
          "id": 19,
          "liquid": 33
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 6,
          "asset_subclass_name": "指数OP",
          "asset_subclass_type": "IDX_OPT",
          "id": 23,
          "liquid": 29
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 7,
          "asset_subclass_name": "土地(自宅)",
          "asset_subclass_type": "HOME_LAND",
          "id": 30,
          "liquid": 22
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 9,
          "asset_subclass_name": "共済年金",
          "asset_subclass_type": "KYOSAI_PNS",
          "id": 35,
          "liquid": 67
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 10,
          "asset_subclass_name": "貴金属・宝石類",
          "asset_subclass_type": "JEWELRY",
          "id": 42,
          "liquid": 10
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 11,
          "asset_subclass_name": "キャッシング・カードローン",
          "asset_subclass_type": "CASHING_LOAN",
          "id": 46,
          "liquid": 4
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 3,
          "asset_subclass_name": "中期国債ファンド",
          "asset_subclass_type": "MGF",
          "id": 53,
          "liquid": 86
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 13,
          "asset_subclass_name": "米国株(信用)",
          "asset_subclass_type": "US_EQ_MGN",
          "id": 58,
          "liquid": 14
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 1,
          "asset_subclass_name": "定期預金",
          "asset_subclass_type": "TERM_DEPO",
          "id": 2,
          "liquid": 95
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 2,
          "asset_subclass_name": "仕組み債",
          "asset_subclass_type": "STRUCT_BD",
          "id": 10,
          "liquid": 88
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 5,
          "asset_subclass_name": "大証FX",
          "asset_subclass_type": "OSE_FX",
          "id": 20,
          "liquid": 32
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 6,
          "asset_subclass_name": "CFD",
          "asset_subclass_type": "CFD",
          "id": 24,
          "liquid": 28
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 7,
          "asset_subclass_name": "土地(投資・事業用)",
          "asset_subclass_type": "INVEST_LAND",
          "id": 31,
          "liquid": 21
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 9,
          "asset_subclass_name": "企業年金",
          "asset_subclass_type": "KIGYO_PNS",
          "id": 36,
          "liquid": 18
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 10,
          "asset_subclass_name": "その他",
          "asset_subclass_type": "OTHER_ASSET",
          "id": 43,
          "liquid": 16
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 11,
          "asset_subclass_name": "その他",
          "asset_subclass_type": "OTHER_LIA",
          "id": 47,
          "liquid": 3
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 3,
          "asset_subclass_name": "MMF",
          "asset_subclass_type": "MMF",
          "id": 54,
          "liquid": 96
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 4,
          "asset_subclass_name": "外国株",
          "asset_subclass_type": "FOR_EQ",
          "id": 55,
          "liquid": 73
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 13,
          "asset_subclass_name": "中国株(信用)",
          "asset_subclass_type": "CN_EQ_MGN",
          "id": 59,
          "liquid": 13
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 1,
          "asset_subclass_name": "外貨預金",
          "asset_subclass_type": "FOR_DEPO",
          "id": 3,
          "liquid": 94
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 3,
          "asset_subclass_name": "外貨MMF",
          "asset_subclass_type": "FOR_MMF",
          "id": 4,
          "liquid": 93
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 2,
          "asset_subclass_name": "その他債券",
          "asset_subclass_type": "OTHER_BD",
          "id": 11,
          "liquid": 87
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 5,
          "asset_subclass_name": "その他FX",
          "asset_subclass_type": "OTHER_FX",
          "id": 21,
          "liquid": 31
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 6,
          "asset_subclass_name": "くりっく株365",
          "asset_subclass_type": "TFE_EQ",
          "id": 25,
          "liquid": 27
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 9,
          "asset_subclass_name": "厚生年金基金",
          "asset_subclass_type": "KOUSEI_K_PNS",
          "id": 37,
          "liquid": 68
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 4,
          "asset_subclass_name": "未公開株式",
          "asset_subclass_type": "PRIVATE_EQ",
          "id": 56,
          "liquid": 72
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 13,
          "asset_subclass_name": "外国株(信用)",
          "asset_subclass_type": "FOR_EQ_MGN",
          "id": 60,
          "liquid": 12
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 1,
          "asset_subclass_name": "預り金・MRF",
          "asset_subclass_type": "MRF",
          "id": 5,
          "liquid": 98
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 3,
          "asset_subclass_name": "その他投信",
          "asset_subclass_type": "OTHER_FUND",
          "id": 13,
          "liquid": 84
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 4,
          "asset_subclass_name": "その他株式",
          "asset_subclass_type": "OTHER_EQ",
          "id": 17,
          "liquid": 75
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 6,
          "asset_subclass_name": "商品先物",
          "asset_subclass_type": "COMM_FUT",
          "id": 26,
          "liquid": 26
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 6,
          "asset_subclass_name": "その他先物OP",
          "asset_subclass_type": "OTHER_DRV",
          "id": 27,
          "liquid": 25
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 9,
          "asset_subclass_name": "国民年金基金",
          "asset_subclass_type": "KOKUMIN_K_PNS",
          "id": 38,
          "liquid": 69
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 13,
          "asset_subclass_name": "その他株式(信用)",
          "asset_subclass_type": "OTHER_EQ_MGN",
          "id": 61,
          "liquid": 11
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 9,
          "asset_subclass_name": "確定拠出年金",
          "asset_subclass_type": "KAKUTEI_PNS",
          "id": 39,
          "liquid": 70
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 1,
          "asset_subclass_name": "保証金・証拠金",
          "asset_subclass_type": "MDEPO",
          "id": 51,
          "liquid": 83
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 1,
          "asset_subclass_name": "その他預金",
          "asset_subclass_type": "OTHER_DEPO",
          "id": 6,
          "liquid": 92
        }
      },
      {
        "asset_subclass": {
          "asset_class_id": 9,
          "asset_subclass_name": "私的年金",
          "asset_subclass_type": "PRIVATE_PNS",
          "id": 40,
          "liquid": 66
        }
      }
    ]