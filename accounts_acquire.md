# 特定の口座の情報をマネーフォワードに金融機関から再取得させる

## 要求

### エンドポイント

```
POST https://moneyforward.com/api/v1/accounts/:id/acquire
```

### パラメーター

| 場所 | 随意性 | 名称 | 内容 |
| ---- | ---- | ---- | --- |
| パス | 必須 | `id` | [口座](https://github.com/moneyforward/api-doc/blob/master/accounts_index.md)の `hashed_id` |

### 例

```
POST https://moneyforward.com/api/v1/accounts/e2RPphY9_-bdYZ1PBLMmjg==/acquire
```

## 応答の本文

なし

