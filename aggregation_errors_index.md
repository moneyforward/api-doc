# マネーフォワードが金融機関から情報を取得しようとする際に生じうる全てのエラーの種類を閲覧する

## 要求

### エンドポイント

```
GET https://moneyforward.com/api/v1/aggregation_errors
```

### パラメーター

場所 | 随意性 | 名称 | 内容
---- | ---- | ---- | ---
ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで `アクセストークン` は [`access_token`](token.md) の値

### 例

```
GET https://moneyforward.com/api/v1/aggregation_errors
X-MFOAuthToken: "Bearer 0d171c8d5e6b023fa13ebd2209453f95e566ba4cb16a1bd1c3becdf09e5e6a0c"
```

## 応答の本文

### 例

```
[
  {
    "aggregation_error": {
      "error_msg": "ScrapingException",
      "error_type": "UNKNOWN",
      "id": 1,
      "msg_title": "一時停止中"
    }
  },
  {
    "aggregation_error": {
      "error_msg": "MaintenanceException",
      "error_type": "NORMAL",
      "id": 2,
      "msg_title": "メンテナンス中"
    }
  },
  {
    "aggregation_error": {
      "error_msg": "TimeoutException",
      "error_type": "NORMAL",
      "id": 3,
      "msg_title": "一時停止中"
    }
  },
  {
    "aggregation_error": {
      "error_msg": "LoginAnnouncementException",
      "error_type": "USER",
      "id": 4,
      "msg_title": "重要なお知らせ"
    }
  },
  {
    "aggregation_error": {
      "error_msg": "LoginErrorException",
      "error_type": "FATAL",
      "id": 5,
      "msg_title": "設定エラー"
    }
  },
  {
    "aggregation_error": {
      "error_msg": "PincodeException",
      "error_type": "FATAL",
      "id": 6,
      "msg_title": "要暗証番号"
    }
  },
  {
    "aggregation_error": {
      "error_msg": "SecretQuestionException",
      "error_type": "FATAL",
      "id": 7,
      "msg_title": "要合言葉"
    }
  },
  {
    "aggregation_error": {
      "error_msg": "OneTimePasswordException",
      "error_type": "FATAL",
      "id": 8,
      "msg_title": "要ワンタイムパスワード"
    }
  },
  {
    "aggregation_error": {
      "error_msg": "GrayException",
      "error_type": "GRAY",
      "id": 9,
      "msg_title": "一時停止中"
    }
  },
  {
    "aggregation_error": {
      "error_msg": "GrayPageException",
      "error_type": "UNKNOWN",
      "id": 10,
      "msg_title": "一時停止中"
    }
  },
  {
    "aggregation_error": {
      "error_msg": "CaptchaException",
      "error_type": "FATAL",
      "id": 11,
      "msg_title": "要画像認証"
    }
  }
]
```
