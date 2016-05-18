# GET /api/v1/accounts
登録済み金融機関リストを返す。取得状況ステータスや、資産額合計も返す。

## Resrouce URL
https://moneyforward.com/api/v1/accounts

## Data definition

name | Description 
-----------|------------------------
account_uid_hidden | 金融機関登録したIDをマスキングしたID（最大３文字が非マスキング）
asset_sum | 金融機関内で保有する資産合計
disp_name | ユーザー自身が設定した登録金融機関識別名（未設定ならnull）
memo | ユーザーが設定した登録金融機関に関するメモ
msg_flag | true: messageを表示する false(default): message非表示
message | ユーザーに通知する必要があるメッセージ
status | アグリゲーションの状態を表す 0:正常（取得済み）、1:取得中、2:取得エラー、3:取得停止中

## Parameters
name | Description 
-----------|------------------------
service_category_ids <br> *optional*  | 金融機関種別のID *Array*
page <br> *optional*  | ページ番号
limit  <br> *optional*  | 1ページあたりのエレメント数

 
## Example
***
> **GET** *https://moneyforward.com/api/v1/accounts*

    {
      "limit": 100,
      "offset": 0,
      "total_count": 1,
      "accounts": [
        {
          "account": {
            "account_uid_hidden": "dem*",
            "asset_sum": 4839122.2979287775,
            "created_at": "2014-04-19T17:33:37+09:00",
            "disp_name": null,
            "aggregation_error_id": 5,
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
            "hashed_id": "LlPqfqeeCZavwPBLmUy6xg==",
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
            "aggregation_error": {
              "error_msg": "LoginErrorException",
              "error_type": "FATAL",
              "id": 5,
              "msg_title": "設定エラー"
            }
          }
        }
      ]
    }