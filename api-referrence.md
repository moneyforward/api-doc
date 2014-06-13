# Moneyforward APIリファレンス
[概要](README.md)はこちら

# Resources

## asset_classes
*現金、株式等の資産クラスマスタ*

 Resource | Description 
:-----------|------------------------:
 [GET /api/v1/asset_classes](asset_classes_index.md) | 資産クラスマスタの取得
 
## asset_subclasses
*資産クラスをさらに細かく分類した資産サブクラスマスタ*

 Resource | Description 
:-----------|-----------------------:
 [GET /api/v1/asset_subclasses](asset_subclasses_index.md) | 資産サブクラスマスタの取得

## service_categories
*金融機関のカテゴリーマスタ*

 Resource | Description 
:-----------|-----------------------:
 [GET /api/v1/service_categories](service_categories_index.md) | 金融機関のカテゴリーマスタの取得

## aggregation_errors
*アグリゲーションのエラーマスタ*

 Resource | Description 
:-----------|-----------------------:
 [GET /api/v1/aggregation_erros](aggregation_errors_index.md) | アグリゲーションのエラーマスタの取得

## services
*銀行や証券会社、カード等、マネーフォワードで登録可能な金融機関のマスタ。*

 Resource | Description 
:-----------|------------------------:
 [GET /api/v1/services](services_index.md) | 金融機関マスタの取得
 [GET /api/v1/services/:id](services_show.md) | 金融機関詳細の取得

## accounts
*登録金融機関。ユーザーが登録済みの金融機関情報*

 Resource | Description
:-----------|------------------------:
 [GET /api/v1/accounts](accounts_index.md) | 登録金融機関リストの取得
 [GET /api/v1/accounts/:id](accounts_show.md) | 登録金融機関詳細の取得
 [POST /api/v1/accounts](accounts_create.md) | 金融機関の登録
 [PUT /api/v1/accounts/:id](accounts_update.md) | 登録機関の更新
 [DELETE /api/v1/accounts/:id](accounts_destroy.md) | 金融機関の削除

## additional_requests
*金融機関登録の追加の質問*

 Resource | Description
:-----------|------------------------:
 [POST /api/v1/additional_requests](additional_requests_create.md) | 追加の質問の作成
 [PUT /api/v1/additional_requests/:id](additional_requests_update.md) | 追加の質問の更新

## user_assets
*個別資産。現金、株、FX、信用取引のポジション等*

 Resource | Description
:-----------|------------------------:
 [GET /api/v1/user_assets](user_assets_index.md) | 個別資産リストの取得
 [GET /api/v1/user_assets/:id](user_assets_show.md) | 個別資産詳細の取得
 
## user_asset_histories
*個別資産の履歴*

 Resource | Description
:-----------|------------------------:
 [GET /api/v1/user_asset_histories](user_asset_histories_index.md) | 個別資産履歴リストの取得
 [GET /api/v1/user_asset_histories/:id](user_asset_histories_show.md) | 個別資産履歴詳細の取得

## user_asset_summaries
*保有資産について、同一asset_subclass、同一sub_account、同一currencyでグルーピングした個別資産の合計*

 Resource | Description
:-----------|------------------------:
 [GET /api/v1/user_asset_summaries](user_asset_summaries_index.md) | 個別資産合計リストの取得
 [GET /api/v1/user_asset_summaries/:id](user_asset_summaries_show.md) | 個別資産合計詳細の取得

## user_asset_summary_histories
*個別資産合計の履歴*

 Resource | Description 
:-----------|------------------------:
 [GET /api/v1/user_asset_summary_histories](user_asset_summary_histories_index.md) | 個別資産合計履歴リストの取得
 [GET /api/v1/user_asset_summary_histories/:id](user_asset_summary_histories_show.md) | 個別資産合計履歴詳細の取得
 
## user_asset_classes
*現金や株式等の資産クラス別の資産合計*

 Resource | Description 
:-----------|------------------------:
 [GET /api/v1/user_asset_classes](user_asset_classes_index.md) | 資産クラス別合計リストの取得

## user_asset_class_histories
*資産クラス別の資産合計の履歴*

 Resource | Description 
:-----------|------------------------:
 [GET /api/v1/user_asset_class_histories](user_asset_class_histories_index.md) | 資産クラス別合計履歴リストの取得

## user
*ユーザー*

 Resource | Description 
:-----------|------------------------:
 [GET /api/v1/user](user_show.md) | ユーザー情報の取得
 [DELETE /api/v1/user](user_destroy.md) | ユーザーの退会 

## 認証

oAuth2

## データフォーマット

リクエスト、レスポンスともにJSON形式のみ

## ノーマルレスポンスのHTTPステータスコード

200 を返します。

## 共通エラーレスポンス

*  HTTPステータスコードは適切な4XX〜5xxのコードを返します。

レスポンスbodyの例

      {
        "error_code" : 2000,
        "error_message" : "バリデーションエラー"       
        "errors" : [
          "名前の長さは20文字以内にしてください。",
          "日付は現在日付以降にしてください。"
          ]
      }

## 連絡先

ご不明点、ご要望等は以下までご連絡ください。

feedback@moneyforward.co.jp
