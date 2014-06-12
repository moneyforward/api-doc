# Moneyforward API v1.0

クラウド家計簿Moneyforwardの開発者向けAPIのドキュメントです。

## 概要

本APIを利用することで、あなたのアプリやサービスをMoneyforwardと連携させることができます。

### 提供機能（2014/5/31現在）

* ユーザ情報の取得
* 登録可能金融機関の取得
* 登録済み金融機関の取得
* 個別資産リストの取得
* 個別資産合計リストの取得
* アセットクラス別資産合計の取得
* アセットクラスの取得
* アセットサブクラスの取得

## 仕様

### エンドポイント

https://moneyforward.com (httpsのみ)

* authorize : /oauth/authorize
* token : /oauth/token

### 認証
oAuth2 に対応

### データフォーマット

リクエスト、レスポンスともにJSON形式をサポート

## [APIリファレンス]

[APIリファレンス]: api-referrence

## 注意点

* 本機能は予告なく新規APIが追加され、既存APIについても変更が入ることがありますのでご了承ください。

## 連絡先

feedback@moneyforward.co.jp 
