# GET /api/v1/service_categories

金融機関のカテゴリマスターを返します。

## Resrouce URL
https://moneyforward.com/api/v1/service_categories

## Parameters

nothing

## Example
*** 
> **GET** *https://moneyforward.com/api/v1/service_categories*

    [
      {
        "service_category": {
          "category_name": "デモを体験する",
          "category_type": "DEMO",
          "id": 1
        }
      },
      {
        "service_category": {
          "category_name": "銀行",
          "category_type": "BANK",
          "id": 2
        }
      },
      {
        "service_category": {
          "category_name": "証券",
          "category_type": "SEC",
          "id": 3
        }
      },
      {
        "service_category": {
          "category_name": "投信",
          "category_type": "MFUND",
          "id": 4
        }
      },
      {
        "service_category": {
          "category_name": "FX・貴金属",
          "category_type": "DRV",
          "id": 5
        }
      },
      {
        "service_category": {
          "category_name": "カード",
          "category_type": "CARD",
          "id": 6
        }
      },
      {
        "service_category": {
          "category_name": "年金",
          "category_type": "PNS",
          "id": 7
        }
      },
      {
        "service_category": {
          "category_name": "電子マネー",
          "category_type": "EMONEY",
          "id": 8
        }
      },
      {
        "service_category": {
          "category_name": "ポイント",
          "category_type": "POINT",
          "id": 9
        }
      },
      {
        "service_category": {
          "category_name": "携帯",
          "category_type": "MOBI",
          "id": 10
        }
      },
      {
        "service_category": {
          "category_name": "サービス連携",
          "category_type": "CONN",
          "id": 11
        }
      },
      {
        "service_category": {
          "category_name": "通販",
          "category_type": "ECOM",
          "id": 12
        }
      },
      {
        "service_category": {
          "category_name": "その他保有資産",
          "category_type": "MANUAL",
          "id": 14
        }
      },
      {
        "service_category": {
          "category_name": "ビジネス",
          "category_type": "BIZ",
          "id": 15
        }
      },
      {
        "service_category": {
          "category_name": "スーパー",
          "category_type": "SUPER",
          "id": 16
        }
      },
      {
        "service_category": {
          "category_name": "アプリ",
          "category_type": "APP",
          "id": 99
        }
      }
    ]
