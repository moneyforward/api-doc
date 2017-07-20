# 特定の口座を解除する

## 要求

### エンドポイント

```
DELETE https://moneyforward.com/api/v1/accounts/:id
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| パス | 必須 | `id` | [金融機関](https://github.com/moneyforward/api-doc/blob/master/accounts_index.md)の `hashed_id` |

### 例

```
DELETE https://moneyforward.com/api/v1/accounts/e2RPphY9_-bdYZ1PBLMmjg==
```

## 応答の本文

なし

