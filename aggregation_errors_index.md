# マネーフォワードが金融機関から情報を取得しようとする際に生じうる全てのエラーの種類を得る

## 要求

### 必要な権限

なし

### エンドポイント

```
GET https://moneyforward.com/api/v1/aggregation_errors
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで ``` `アクセストークン` ``` は [`access_token`](token.md) の値 |

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
            "id": 1,
            "error_type": "UNKNOWN",
            "error_msg": "ScrapingException",
            "msg_title": "一時停止中"
        }
    },
    {
        "aggregation_error": {
            "id": 2,
            "error_type": "NORMAL",
            "error_msg": "MaintenanceException",
            "msg_title": "メンテナンス中"
        }
    },
    {
        "aggregation_error": {
            "id": 3,
            "error_type": "NORMAL",
            "error_msg": "TimeoutException",
            "msg_title": "一時停止中"
        }
    },
    {
        "aggregation_error": {
            "id": 4,
            "error_type": "USER",
            "error_msg": "LoginAnnouncementException",
            "msg_title": "重要なお知らせ"
        }
    },
    {
        "aggregation_error": {
            "id": 5,
            "error_type": "FATAL",
            "error_msg": "LoginErrorException",
            "msg_title": "設定エラー"
        }
    },
    {
        "aggregation_error": {
            "id": 6,
            "error_type": "FATAL",
            "error_msg": "PincodeException",
            "msg_title": "要暗証番号"
        }
    },
    {
        "aggregation_error": {
            "id": 7,
            "error_type": "FATAL",
            "error_msg": "SecretQuestionException",
            "msg_title": "要追加認証の情報"
        }
    },
    {
        "aggregation_error": {
            "id": 8,
            "error_type": "FATAL",
            "error_msg": "OneTimePasswordException",
            "msg_title": "要ワンタイムパスワード"
        }
    },
    {
        "aggregation_error": {
            "id": 9,
            "error_type": "GRAY",
            "error_msg": "GrayException",
            "msg_title": "一時停止中"
        }
    },
    {
        "aggregation_error": {
            "id": 10,
            "error_type": "UNKNOWN",
            "error_msg": "GrayPageException",
            "msg_title": "一時停止中"
        }
    },
    {
        "aggregation_error": {
            "id": 11,
            "error_type": "FATAL",
            "error_msg": "CaptchaException",
            "msg_title": "要画像認証"
        }
    },
    {
        "aggregation_error": {
            "id": 12,
            "error_type": "FATAL",
            "error_msg": "Captcha2Exception",
            "msg_title": "要追加認証"
        }
    }
]
```
