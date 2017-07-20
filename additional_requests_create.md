# 特定の口座への代替のログイン方法で必要な追加の質問の質問部分を得る

## 要求

### エンドポイント

```
POST https://moneyforward.com/api/v1/additonal_requests
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| 本文 | 必須 | `additional_request[account_id]` | [口座](https://github.com/moneyforward/api-doc/blob/master/accounts_index.md)の `hashed_id` |

### 例

```
POST https://moneyforward.com/api/v1/additional_requests

{
  "additional_request": {
    "account_id": "84dG3OLcZt_gLm66DESKzw=="
  }
}
```

## 応答の本文

### 例

```
[
  {
    "additional_request": {
      "hashed_id": "ZUwr8sW8oXjm5uThdVSZPw==",
      "message": "合言葉／秘密の質問 への記入が必要です。",
      "request_data": "子供の頃の一番の親友の名前は何ですか"
    }
  }
]
```
