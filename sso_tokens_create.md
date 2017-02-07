# POST /api/v1/sso_tokens

SSOトークン取得

## Resrouce URL
https://moneyforward.com/api/v1/sso_tokens

## Parameters
name | Description
-----|-----
sso_tokens[redirect_path] | リダイレクト先URI(default=/)

## Example

### request

> **POST** https://moneyforward.com/api/v1/sso_tokens

### request-body

    {
      "sso_token": {
        "redirect_path": "/accounts"
      }
    }

### response

    {
      "sso_token" {
        "token": トークン文字列
      }
    }
