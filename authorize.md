# 認可を得る

OAuth2 Authorization Code Flow による認証を行い、特定のAPIエンドポイントにアクセスする権限を取得する。

各APIエンドポイントには、アクセスに必要な権限(スコープ)が指定されている。クライアントソフトウェアは、指定された全ての権限について本エンドポイントから認可された時にのみ、当該のAPIエンドポイントにアクセスできる。本エンドポイントへのアクセスは、APIエンドポイントへのアクセスごとや権限ごとに行う必要は無く、複数のAPIエンドポイントで必要な権限をまとめて認可されうる。各権限は、次の全てを満たした場合に認可される。

* クライアントソフトウェアの登録時に、マネーフォワードがクライアントソフトウェアに対してその権限を与えている。
* クライアントソフトウェアが本エンドポイントにアクセスした時に、要求のパラメーターにその権限が含まれている。
* クライアントソフトウェアがその権限を持ってユーザーの情報にアクセスすることをユーザーがウェブブラウザを通じて認める。

本エンドポイントから権限の認可を受けるだけではAPIエンドポイントを使うことは出来ず、戻り値に含まれる `code` の値を使ってさらに[アクセストークンを得る](token.md)必要がある。

クライアントソフトウェアが秘密の文字列を生成して要求時にパラメーター `state` の値として渡すと、応答にも同じ値が返され、クライアントソフトウェアがその同一性を検証することによって、応答がマネーフォワードのなりすましからのものでないことの目安にできる。

## 要求

### エンドポイント

```
GET https://moneyforward.com/oauth/authorize
```

または

```
POST https://moneyforward.com/oauth/authorize
```

### パラメーター

場所 | 随意性 | 名称 | 内容
---- | ---- | ---- | ---
クエリー | 必須 | `response_type` | `code`
クエリー | 必須 | `client_id` | クライアントソフトウェア登録時にマネーフォワード担当者がお渡ししたクライアントソフトウェア固有の文字列
クエリー | 必須 | `redirect_uri` | クライアントソフトウェアの登録時に指定された、クライアントソフトウェア上のアクセスポイント
クエリー | 任意 | `state` | クライアントソフトウェアから提出される秘密の文字列
クエリー | 必須 | `scope` | このあと発行されるトークンを使ってアクセスするAPIエンドポイントに必要な全ての権限を空白でつないだもの

### 例

```
GET https://moneyforward.com/oauth/authorize?response_type=code&client_id=710c7d597a85ebb461802267bebb83ff58cabd62f2ff9&redirect_uri=http%3A%2F%2Flocalhost%3A1234%2Fcallback&state=NzHDXGuMme5c4GkCEd7TXUYebK0%3D&scope=openid+email+accounts+acquire_accounts+manage_accounts+assets+transactions+manage_transactions+manage_sso
```

## 応答の本文

### パラメーター

名称 | 内容
---- | ---
`code` | 認可を受けたことを示す、アクセストークンを得るために必要な秘密の文字列
`state` | 要求の `state` パラメーターの値

### 例

```
{
  "code": e885b973e64797bcf3342529d57cd2adca97a11f787ef9736ea92d8061e5aa59,
  "state": NzHDXGuMme5c4GkCEd7TXUYebK0
}
```