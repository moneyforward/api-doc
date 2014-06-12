# POST /api/v1/additonal_requests
追加の質問の作成を行う

## Resrouce URL
https://moneyforward.com/api/v1/additional_requests

## Parameters
name | Description 
-----------|------------------------
additional_request[:account_id] <br> *required* | 追加の質問を作成する金融機関のID *hashed*

## Example

### request

> **POST* *https://moneyforward.com/api/v1/additional_requests

### request-body

    {
      "additional_request": {
        "account_id": "84dG3OLcZt_gLm66DESKzw=="
      }
    }

### rsponse-body

    [
      {
        "additional_request": {
          "hashed_id": "ZUwr8sW8oXjm5uThdVSZPw==",
          "message": "合言葉／秘密の質問 への記入が必要です。",
          "request_data": "子供の頃の一番の親友の名前は何ですか"
        }
      }
    ]