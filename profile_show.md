# ユーザーのデモグラフィック情報を閲覧する

## 要求

### エンドポイント

```
GET https://moneyforward.com/api/v1/profile
```

### パラメーター

場所 | 随意性 | 名称 | 内容
---- | ---- | ---- | ---
ヘッダー | 必須 | `Authorization` または `X-MFOAuthToken` | ```Bearer `アクセストークン` ```; ここで `アクセストークン` は [`access_token`](token.md) の値

### 例

```
GET https://moneyforward.com/api/v1/profile
X-MFOAuthToken: "Bearer 5e566bda4cb16a1bd1c3beecdf09e1a1c8d5e60b23fa13ebd5ed220c9453f9ac"
```

## 応答の本文

### パラメーター

プロフィール登録は、ユーザー登録直後に `https://moneyforward.com/users/welcome/profile/edit` で行われます。ユーザー登録後でプロフィールの全項目が(必須項目も含めて)未登録の場合が有り得ます。プロフィール変更は、`https://moneyforward.com/profile` で行われます。

名称 | 内容
---- | ---
`profile[gender]` | 性別; プロフィール登録・変更で選択出来る値(`"男"`, `"女"` のいずれか)、もしくは `null`: 未登録
`profile[birth_year]` | 誕生年; プロフィール登録・変更で選択出来る値(`1920` から `2012` までの整数)、もしくは `null`: 未登録
`profile[job]` | 職業; プロフィール登録・変更で選択出来る表示文字列のいずれか、もしくは `null`: 未登録
`profile[family_structure]` | 家族形態; プロフィール登録・変更で選択出来る表示文字列のいずれか、もしくは `null`: 未登録
`profile[living_arrangement]` | 居住形態; プロフィール変更で選択出来る表示文字列のいずれか、もしくは `null`: 未登録

### 例

```
{
  "profile": {
    "family_structure": "既婚（子ども3人以上）",
    "living_arrangement": "集合住宅（分譲）",
    "job": "コンサルティング",
    "gender": "女",
    "birth_year": 1995
  }
}
```
