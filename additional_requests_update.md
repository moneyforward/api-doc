# 特定の口座への代替のログイン方法で必要な追加の質問の答えを更新する

## 要求

### エンドポイント

```
PUT https://moneyforward.com/api/v1/additional_requests/:id
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| パス | 必須 | `id` | [追加の質問](https://github.com/moneyforward/api-doc/blob/master/additional_requests_create.md)の `hashed_id` |
| 本文 | 必須 | `additional_request[response_data]` | 追加の質問の答え |

### 例

```
PUT https://moneyforward.com/api/v1/additional_requests/e2RPphY9_-bdYZ1PBLMmjg==

{
  "additional_request": {
    "response_data": "追加の質問の答え"
  }
}
```

## 応答の本文

なし
