# PUT /api/v1/transactions/:id

入出金履歴の更新を行います。

## Resource URL

https://moneyforward.com/api/v1/transactions/:id

## Parameters

Name | Description
-----------|------------------------
id <br> *required* | 入出金ID。GET /api/v1/transactionsやPOST /api/v1/transactionsの返り値で得られるtransactionのhashed_idを与える。
account_id <br> *required* | 入金元・出金先の財布口座。GET /api/v1/accountsにより得られる一覧のうちで該当する財布口座のhashed_account_idの値を与える。自動連携している口座は指定出来ない。財布口座の場合には、口座とサブアカウントが1対1対応しているので、hashed_sub_account_idも決定される。
updated_at <br> *optional* | 入出金日。YY/MM/DD形式で記す。省略した場合には現在日になる。
content <br> *optional* | 入出金内容を記す文字列。最大65535byte。
large_category_id <br> *optional* | 大項目カテゴリ。省略した場合には未設定(large_category_id=0)になる。
middle_category_id <br> *optional* | 中項目カテゴリ。省略した場合には未設定(middle_category_id=0)になる。
is_income <br> *required* | 収入(1またはtrue)または支出(0またはfalse)。
amount <br> *required* | 金額。入出金に関わらず0または正の整数。

## Example

***
> **PATCH/PUT** https://moneyforward.com/api/v1/transactions/hqZkZiBY-WIP8mlohrug7Q

    {"transaction": {
      "hashed_id": "hqZkZiBY-WIP8mlohrug7Q",
      "hashed_account_id": "c6f7fTZ_BfttQZ2fBg2eTQ",
      "hashed_sub_account_id": "c6f7fTZ_BfttQZ2fBg2eTQ",
      "amount": 1234,
      "content": "labour",
      "currency": "JPY",
      "is_income": true,
      "is_transfer": false,
      "jpyrate": 1.0,
      "large_category_id": 0,
      "middle_category_id": 0,
      "created_at": "2017-01-31T11:44:10+09:00",
      "updated_at": "2017-01-31T00:00:00+09:00"
    }}
