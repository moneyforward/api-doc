# GET /api/v1/user_asset_histories
ユーザーの保有する資産の履歴リストを返す。
from_date, to_date パラメーターを付けない場合は、
昨日の資産履歴リストを返します。

## Resrouce URL
https://moneyforward.com/api/v1/user_asset_histories

## Data definition

name | Description 
-----------|------------------------
code | 株式銘柄コード等。
cost | 現在未使用フィールド
entried_at | 資産取得日（特定できなければnull）
entried_price | 取得価格
expire_at |	資産の有効期限（ポイント等）※特定できなければnull
jpy_rate | 円換算レート
name | 資産名称
profit | 損益
qty | 数量
value | 評価額またはポイント数
updated_at | 基準日
hashed_original_user_asset_id | ヒストリカル作成の元となった、user_assetのid *hashed*

## Parameters

name | Description 
-----------|------------------------
account_ids <br /> *optional* | 登録金融機関ID *hashed* *Array*
original_user_asset_ids <br /> *optional* | 保有資産ID *hashed* *Array*
asset_class_ids  <br /> *optional* | アセットクラスID *Array*
asset_subclass_ids  <br /> *optional* | アセットサブクラスID *Array*
target_dates <br /> *optional* | 履歴検索指定日。from_date,to_dateより優先 *Array*
from_date <br /> *optional* | 履歴検索開始日。デフォルトは昨日日付
to_date <br /> *optional* | 履歴検索終了日。デフォルトは昨日日付
page  <br /> *optional* | ページ番号
limit <br /> *optional* | 1ページあたりのエレメント数.デフォルト100、最大500

 
## Example
***
> **GET** *https://moneyforward.com/api/v1/user_asset_histories?account_ids[]=LlPqfqeeCZavwPBLmUy6xg==&from_date=2014-5-22&to_date=2014-05-23*

    {
      "limit": 100,
      "offset": 0,
      "total_count": 6,
      "user_asset_histories": [
        {
          "user_asset_history": {
            "asset_class_id": 3,
            "asset_subclass_id": 12,
            "code": "",
            "cost": 0,
            "currency": "JPY",
            "current_price": 389024.721519843,
            "entried_at": null,
            "entried_price": 300000,
            "expire_at": null,
            "jpyrate": 1,
            "name": "【デモ】マネフォファンド",
            "profit": 89024.72151984298,
            "qty": 1,
            "updated_at": "2014-05-23T00:00:00+09:00",
            "value": 389024.721519843,
            "hashed_id": "2bdgEA3TcaIPREBaNKdjvw==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_id": "vpxDzM6STgFT4Br7pFTzVQ==",
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
            }
          }
        },
        {
          "user_asset_history": {
            "asset_class_id": 4,
            "asset_subclass_id": 14,
            "code": "",
            "cost": 0,
            "currency": "JPY",
            "current_price": 424941.7055783825,
            "entried_at": null,
            "entried_price": 300000,
            "jpyrate": 1,
            "name": "【デモ】マネフォ株式",
            "profit": 124941.70557838248,
            "qty": 1,
            "updated_at": "2014-05-23T00:00:00+09:00",
            "value": 424941.7055783825,
            "hashed_id": "izURycZ9tGe3ffo6dkfZJw==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_id": "3H3ZDVJ7RseoDC8LBfanvA==",
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
            }
          }
        },
        {
          "user_asset_history": {
            "asset_class_id": 9,
            "asset_subclass_id": 39,
            "code": "",
            "cost": 0,
            "currency": "JPY",
            "current_price": 775155.8708305522,
            "entried_at": null,
            "entried_price": 500000,
            "expire_at": null,            
            "jpyrate": 1,
            "name": "【デモ】マネフォファンド(確定拠出年金専用)",
            "profit": 275155.8708305522,
            "qty": 1,
            "updated_at": "2014-05-23T00:00:00+09:00",
            "value": 775155.8708305522,
            "hashed_id": "kZjneptIgNgzC4Pc4TPPpg==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_id": "eMPREQm-zEmfZw_aWfrCnQ==",
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
            }
          }
        },
        {
          "user_asset_history": {
            "asset_class_id": 3,
            "asset_subclass_id": 12,
            "code": "",
            "cost": 0,
            "currency": "JPY",
            "current_price": 389024.721519843,
            "entried_at": null,
            "entried_price": 300000,
            "expire_at": null,
            "jpyrate": 1,
            "name": "【デモ】マネフォファンド",
            "profit": 89024.72151984298,
            "qty": 1,
            "updated_at": "2014-05-22T00:00:00+09:00",
            "value": 389024.721519843,
            "hashed_id": "8ewSMICPAGhG3f3asNrptA==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_id": "vpxDzM6STgFT4Br7pFTzVQ==",
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
            }
          }
        },
        {
          "user_asset_history": {
            "asset_class_id": 4,
            "asset_subclass_id": 14,
            "code": "",
            "cost": 0,
            "currency": "JPY",
            "current_price": 424941.7055783825,
            "entried_at": null,
            "entried_price": 300000,
            "expire_at": null,            
            "jpyrate": 1,
            "name": "【デモ】マネフォ株式",
            "profit": 124941.70557838248,
            "qty": 1,
            "updated_at": "2014-05-22T00:00:00+09:00",
            "value": 424941.7055783825,
            "hashed_id": "PK1jeBjDozr8B0NcD3LY3w==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_id": "3H3ZDVJ7RseoDC8LBfanvA==",
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
            }
          }
        },
        {
          "user_asset_history": {
            "asset_class_id": 9,
            "asset_subclass_id": 39,
            "code": "",
            "cost": 0,
            "currency": "JPY",
            "current_price": 775155.8708305522,
            "entried_at": null,
            "entried_price": 500000,
            "expire_at": null,
            "jpyrate": 1,
            "name": "【デモ】マネフォファンド(確定拠出年金専用)",
            "profit": 275155.8708305522,
            "qty": 1,
            "updated_at": "2014-05-22T00:00:00+09:00",
            "value": 775155.8708305522,
            "hashed_id": "PcvM-sx0UdCq9sDPG6N_WQ==",
            "hashed_account_id": "LlPqfqeeCZavwPBLmUy6xg==",
            "hashed_original_user_asset_id": "eMPREQm-zEmfZw_aWfrCnQ==",
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
            }
          }
        }
      ]
    }
