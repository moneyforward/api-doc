# GET /api/v1/user_asset_summary_histories
ユーザーの個別資産合計の履歴リストを返す。
from_date, to_date パラメーターを付けない場合は、
昨日の資産履歴リストを返します。

## Resrouce URL
https://moneyforward.com/api/v1/user_asset_summary_histories

## Data definition

name | Description 
-----------|------------------------
profit | 損益
value | 評価額
rated_value | 為替レートを勘案した円換算評価額
rated_profit | 為替レートを勘案した円換算損益
updated_at | 基準日

## Parameters
name | Description 
-----------|------------------------
account_ids <br /> *optional* | 登録金融機関ID *hashed* *Array*
original_user_asset_summary_ids <br /> *optional* | 個別資産合計ID *hashed* *Array*
asset_class_ids  <br /> *optional* | アセットクラスID *Array*
asset_subclass_ids  <br /> *optional* | アセットサブクラスID *Array*
target_dates <br /> *optional* | 履歴検索指定日。from_date,to_dateより優先 *Array*
from_date <br /> *optional* | 履歴検索開始日。デフォルトは昨日日付
to_date <br /> *optional* | 履歴検索終了日。デフォルトは昨日日付
page  <br /> *optional* | ページ番号
limit <br /> *optional* | 1ページあたりのエレメント数.デフォルト100、最大500

 
## Example
***
> **GET** *https://moneyforward.com/api/v1/user_asset_summary_histories?account_ids[]=LlPqfqeeCZavwPBLmUy6xg==&from_date=2014-5-22&to_date=2014-05-23*

    {
      "limit": 100,
      "offset": 0,
      "total_count": 10,
      "user_asset_summary_histories": [
        {
          "user_asset_summary_history": {
            "asset_class_id": 3,
            "asset_subclass_id": 12,
            "currency": "JPY",
            "jpyrate": 1, 
            "profit": 3000,
            "rated_value": 389024.721519843,
            "rated_profit":3000,
            "updated_at": "2014-05-23T00:00:00+09:00",
            "value": 389024.721519843,
            "hashed_id": "jPuCXXZP3h6TBx3DskME-A==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_summary_id": "BR5-TCLSc2eZ-gf5Wxa4lA==",
            "account": {
              "account_uid_hidden": "dem*",
              "created_at": "2014-04-19T17:33:37+09:00",
              "disp_name": null,
              "error_id": 5,
              "last_aggregated_at": "2014-05-22T06:33:13+09:00",
              "last_succeeded_at": "05/22 06:33",
              "memo": null,
              "message": null,
              "msg_flag": 0,
              "msg_time": null,
              "next_aggregate_at": "2014-05-25T02:27:08+09:00",
              "service_category_id": 1,
              "service_id": 1,
              "status": 2,
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
              }
            },
            "asset_class": {
              "asset_class_name": "投資信託",
              "asset_class_type": "MF",
              "disp_order": 4,
              "id": 3
            },
            "asset_subclass": {
              "asset_class_id": 3,
              "asset_subclass_name": "投資信託",
              "asset_subclass_type": "MUTUAL_FUND",
              "id": 12,
              "liquid": 85
            }
          }
        },
        {
          "user_asset_summary_history": {
            "asset_class_id": 4,
            "asset_subclass_id": 14,
            "currency": "JPY",
            "jpyrate": 1, 
            "profit": 3000,
            "rated_value": 424941.7055783825,
            "rated_profit":3000,
            "updated_at": "2014-05-23T00:00:00+09:00",
            "value": 424941.7055783825,
            "hashed_id": "6mns89dM_TwYmxFdGxCflQ==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_summary_id": "cUZSL8p8QGWvMz5ERNPCgw==",
            "account": {
              "account_uid_hidden": "dem*",
              "created_at": "2014-04-19T17:33:37+09:00",
              "disp_name": null,
              "error_id": 5,
              "last_aggregated_at": "2014-05-22T06:33:13+09:00",
              "last_succeeded_at": "05/22 06:33",
              "memo": null,
              "message": null,
              "msg_flag": 0,
              "msg_time": null,
              "next_aggregate_at": "2014-05-25T02:27:08+09:00",
              "service_category_id": 1,
              "service_id": 1,
              "status": 2,
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
              }
            },
            "asset_class": {
              "asset_class_name": "株式(現物)",
              "asset_class_type": "EQ",
              "disp_order": 2,
              "id": 4
            },
            "asset_subclass": {
              "asset_class_id": 4,
              "asset_subclass_name": "国内株",
              "asset_subclass_type": "DOM_EQ",
              "id": 14,
              "liquid": 78
            }
          }
        },
        {
          "user_asset_summary_history": {
            "asset_class_id": 1,
            "asset_subclass_id": 1,
            "currency": "JPY",
            "jpyrate": 1, 
            "profit": 3000,
            "rated_value": 2750000,
            "rated_profit":3000,
            "updated_at": "2014-05-23T00:00:00+09:00",
            "value": 2750000,
            "hashed_id": "PujM2JxzEiJB2qX0Jv57DQ==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_summary_id": "jrJMif2YYMXj3v76qeVNQg==",
            "account": {
              "account_uid_hidden": "dem*",
              "created_at": "2014-04-19T17:33:37+09:00",
              "disp_name": null,
              "error_id": 5,
              "last_aggregated_at": "2014-05-22T06:33:13+09:00",
              "last_succeeded_at": "05/22 06:33",
              "memo": null,
              "message": null,
              "msg_flag": 0,
              "msg_time": null,
              "next_aggregate_at": "2014-05-25T02:27:08+09:00",
              "service_category_id": 1,
              "service_id": 1,
              "status": 2,
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
              }
            },
            "asset_class": {
              "asset_class_name": "預金・現金",
              "asset_class_type": "DEPO",
              "disp_order": 1,
              "id": 1
            },
            "asset_subclass": {
              "asset_class_id": 1,
              "asset_subclass_name": "普通預金",
              "asset_subclass_type": "ORD_DEPO",
              "id": 1,
              "liquid": 99
            }
          }
        },
        {
          "user_asset_summary_history": {
            "asset_class_id": 1,
            "asset_subclass_id": 2,
            "currency": "JPY",
            "jpyrate": 1, 
            "profit": 3000,
            "rated_value": 500000,
            "rated_profit":3000,
            "updated_at": "2014-05-23T00:00:00+09:00",
            "value": 500000,
            "hashed_id": "107xqRKYURJQd4ZiL6jPLQ==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_summary_id": "CA-qbk9HiB3ztzE5iKYWUg==",
            "account": {
              "account_uid_hidden": "dem*",
              "created_at": "2014-04-19T17:33:37+09:00",
              "disp_name": null,
              "error_id": 5,
              "last_aggregated_at": "2014-05-22T06:33:13+09:00",
              "last_succeeded_at": "05/22 06:33",
              "memo": null,
              "message": null,
              "msg_flag": 0,
              "msg_time": null,
              "next_aggregate_at": "2014-05-25T02:27:08+09:00",
              "service_category_id": 1,
              "service_id": 1,
              "status": 2,
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
              }
            },
            "asset_class": {
              "asset_class_name": "預金・現金",
              "asset_class_type": "DEPO",
              "disp_order": 1,
              "id": 1
            },
            "asset_subclass": {
              "asset_class_id": 1,
              "asset_subclass_name": "定期預金",
              "asset_subclass_type": "TERM_DEPO",
              "id": 2,
              "liquid": 95
            }
          }
        },
        {
          "user_asset_summary_history": {
            "asset_class_id": 9,
            "asset_subclass_id": 39,
            "currency": "JPY",
            "jpyrate": 1, 
            "profit": 3000,
            "rated_value": 775155.8708305522,
            "rated_profit":3000,
            "updated_at": "2014-05-23T00:00:00+09:00",
            "value": 775155.8708305522,
            "hashed_id": "Hul4UIcbHSzb0WZ7pMianQ==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_summary_id": "EZOB3wR14WhMJDWb49ydFg==",
            "account": {
              "account_uid_hidden": "dem*",
              "created_at": "2014-04-19T17:33:37+09:00",
              "disp_name": null,
              "error_id": 5,
              "last_aggregated_at": "2014-05-22T06:33:13+09:00",
              "last_succeeded_at": "05/22 06:33",
              "memo": null,
              "message": null,
              "msg_flag": 0,
              "msg_time": null,
              "next_aggregate_at": "2014-05-25T02:27:08+09:00",
              "service_category_id": 1,
              "service_id": 1,
              "status": 2,
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
              }
            },
            "asset_class": {
              "asset_class_name": "年金",
              "asset_class_type": "PNS",
              "disp_order": 10,
              "id": 9
            },
            "asset_subclass": {
              "asset_class_id": 9,
              "asset_subclass_name": "確定拠出年金",
              "asset_subclass_type": "KAKUTEI_PNS",
              "id": 39,
              "liquid": 70
            }
          }
        },
        {
          "user_asset_summary_history": {
            "asset_class_id": 3,
            "asset_subclass_id": 12,
            "currency": "JPY",
            "jpyrate": 1, 
            "profit": 3000,
            "rated_value": 389024.721519843,
            "rated_profit":3000,
            "updated_at": "2014-05-22T00:00:00+09:00",
            "value": 389024.721519843,
            "hashed_id": "14uycjMdaxOyK-g5XGr47Q==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_summary_id": "BR5-TCLSc2eZ-gf5Wxa4lA==",
            "account": {
              "account_uid_hidden": "dem*",
              "created_at": "2014-04-19T17:33:37+09:00",
              "disp_name": null,
              "error_id": 5,
              "last_aggregated_at": "2014-05-22T06:33:13+09:00",
              "last_succeeded_at": "05/22 06:33",
              "memo": null,
              "message": null,
              "msg_flag": 0,
              "msg_time": null,
              "next_aggregate_at": "2014-05-25T02:27:08+09:00",
              "service_category_id": 1,
              "service_id": 1,
              "status": 2,
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
              }
            },
            "asset_class": {
              "asset_class_name": "投資信託",
              "asset_class_type": "MF",
              "disp_order": 4,
              "id": 3
            },
            "asset_subclass": {
              "asset_class_id": 3,
              "asset_subclass_name": "投資信託",
              "asset_subclass_type": "MUTUAL_FUND",
              "id": 12,
              "liquid": 85
            }
          }
        },
        {
          "user_asset_summary_history": {
            "asset_class_id": 4,
            "asset_subclass_id": 14,
            "currency": "JPY",
            "jpyrate": 1, 
            "profit": 3000,
            "rated_value": 424941.7055783825,
            "rated_profit":3000,
            "updated_at": "2014-05-22T00:00:00+09:00",
            "value": 424941.7055783825,
            "hashed_id": "NBpXN97jxivR6H-7JsMPNQ==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_summary_id": "cUZSL8p8QGWvMz5ERNPCgw==",
            "account": {
              "account_uid_hidden": "dem*",
              "created_at": "2014-04-19T17:33:37+09:00",
              "disp_name": null,
              "error_id": 5,
              "last_aggregated_at": "2014-05-22T06:33:13+09:00",
              "last_succeeded_at": "05/22 06:33",
              "memo": null,
              "message": null,
              "msg_flag": 0,
              "msg_time": null,
              "next_aggregate_at": "2014-05-25T02:27:08+09:00",
              "service_category_id": 1,
              "service_id": 1,
              "status": 2,
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
              }
            },
            "asset_class": {
              "asset_class_name": "株式(現物)",
              "asset_class_type": "EQ",
              "disp_order": 2,
              "id": 4
            },
            "asset_subclass": {
              "asset_class_id": 4,
              "asset_subclass_name": "国内株",
              "asset_subclass_type": "DOM_EQ",
              "id": 14,
              "liquid": 78
            }
          }
        },
        {
          "user_asset_summary_history": {
            "asset_class_id": 1,
            "asset_subclass_id": 1,
            "currency": "JPY",
            "jpyrate": 1, 
            "profit": 3000,
            "rated_value": 2750000,
            "rated_profit":3000,
            "updated_at": "2014-05-22T00:00:00+09:00",
            "value": 2750000,
            "hashed_id": "j5ewE9N1jvbSahUb5e8JXA==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_summary_id": "jrJMif2YYMXj3v76qeVNQg==",
            "account": {
              "account_uid_hidden": "dem*",
              "created_at": "2014-04-19T17:33:37+09:00",
              "disp_name": null,
              "error_id": 5,
              "last_aggregated_at": "2014-05-22T06:33:13+09:00",
              "last_succeeded_at": "05/22 06:33",
              "memo": null,
              "message": null,
              "msg_flag": 0,
              "msg_time": null,
              "next_aggregate_at": "2014-05-25T02:27:08+09:00",
              "service_category_id": 1,
              "service_id": 1,
              "status": 2,
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
              }
            },
            "asset_class": {
              "asset_class_name": "預金・現金",
              "asset_class_type": "DEPO",
              "disp_order": 1,
              "id": 1
            },
            "asset_subclass": {
              "asset_class_id": 1,
              "asset_subclass_name": "普通預金",
              "asset_subclass_type": "ORD_DEPO",
              "id": 1,
              "liquid": 99
            }
          }
        },
        {
          "user_asset_summary_history": {
            "asset_class_id": 1,
            "asset_subclass_id": 2,
            "currency": "JPY",
            "jpyrate": 1,
            "profit": 3000,
            "rated_value": 500000,
            "rated_profit":3000,
            "updated_at": "2014-05-22T00:00:00+09:00",
            "value": 500000,
            "hashed_id": "DwazD9I3Q2zfMJBTTU7gvQ==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_summary_id": "CA-qbk9HiB3ztzE5iKYWUg==",
            "account": {
              "account_uid_hidden": "dem*",
              "created_at": "2014-04-19T17:33:37+09:00",
              "disp_name": null,
              "error_id": 5,
              "last_aggregated_at": "2014-05-22T06:33:13+09:00",
              "last_succeeded_at": "05/22 06:33",
              "memo": null,
              "message": null,
              "msg_flag": 0,
              "msg_time": null,
              "next_aggregate_at": "2014-05-25T02:27:08+09:00",
              "service_category_id": 1,
              "service_id": 1,
              "status": 2,
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
              }
            },
            "asset_class": {
              "asset_class_name": "預金・現金",
              "asset_class_type": "DEPO",
              "disp_order": 1,
              "id": 1
            },
            "asset_subclass": {
              "asset_class_id": 1,
              "asset_subclass_name": "定期預金",
              "asset_subclass_type": "TERM_DEPO",
              "id": 2,
              "liquid": 95
            }
          }
        },
        {
          "user_asset_summary_history": {
            "asset_class_id": 9,
            "asset_subclass_id": 39,
            "currency": "JPY",
            "jpyrate": 1, 
            "profit": 3000,
            "rated_value": 775155.8708305522,
            "rated_profit":3000,
            "updated_at": "2014-05-22T00:00:00+09:00",
            "value": 775155.8708305522,
            "hashed_id": "yIvaVQQeLt9PazrYGdkD3w==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_summary_id": "EZOB3wR14WhMJDWb49ydFg==",
            "account": {
              "account_uid_hidden": "dem*",
              "created_at": "2014-04-19T17:33:37+09:00",
              "disp_name": null,
              "error_id": 5,
              "last_aggregated_at": "2014-05-22T06:33:13+09:00",
              "last_succeeded_at": "05/22 06:33",
              "memo": null,
              "message": null,
              "msg_flag": 0,
              "msg_time": null,
              "next_aggregate_at": "2014-05-25T02:27:08+09:00",
              "service_category_id": 1,
              "service_id": 1,
              "status": 2,
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
              }
            },
            "asset_class": {
              "asset_class_name": "年金",
              "asset_class_type": "PNS",
              "disp_order": 10,
              "id": 9
            },
            "asset_subclass": {
              "asset_class_id": 9,
              "asset_subclass_name": "確定拠出年金",
              "asset_subclass_type": "KAKUTEI_PNS",
              "id": 39,
              "liquid": 70
            }
          }
        }
      ]
    }