# GET /api/v1/user
ユーザー情報を返します

## Resrouce URL
https://moneyforward.com/api/v1/user

## Data definition

name | Description 
-----------|------------------------
lock | 連続パスワード入力失敗回数（累積）
lock_limit | パスワードロック期限（nullならロックされていない
mf_registered_at | マネーフォワード家計簿サービス利用開始日時
mf_withdrew_at | マネーフォワード家計簿サービス利用終了日時（サービス退会日時）
premium? | マネーフォワード家計簿プレミアムサービス利用状況フラグ
only_api_user? | マネーフォワード家計簿をAPI経由でのみ利用しているかを表すフラグ

## Parameters
nothing

## Example
***
> **GET** *https://moneyforward.com/api/v1/user*

    {
      "user": {
        "lock": 0,
        "lock_limit": null,
        "mf_registered_at": "2014-04-19T17:33:36+09:00",
        "mf_withdrew_at": null,
        "premium?": false,
        "only_api_user?": false
      }
    }
    