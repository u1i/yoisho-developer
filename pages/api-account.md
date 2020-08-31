---
layout: layouts/api.njk
title: Home
date: 2016-01-01T00:00:00.000Z
permalink: /
eleventyNavigation:
  key: Home
  order: 0
---

![](/static/img/i2.png)

# Account Info & Balance - REST/JSON OAuth

Gives you an account balance API with a 3-legged OAuth flow including consumer consent management & login.

##### 3-legged OAuth components

1. Consumer: the app, identified by client\_id and client\_secret
2. Resource Owner: the banking customer, here it's Dave and Jane
3. API: the account balance service

![](https://raw.githubusercontent.com/u1i/yoisho/master/resources/account-2.png)

### Credentials:

* client_id: 7b6fc8ed5127b0b2f076d
* client_secret: 724e6890757b0ae624684b70e111b705fe6b050c
* user accounts: jane, dave (use any random password)

### Start the flow

Access this URL in the browser (replace the redirect_uri with your own):

`https://backend.yoisho.dob.jp/account/authorize?redirect_uri=http://www3.sotong.io&client_id=7b6fc8ed5127b0b2f076d`

Login with either 'dave' or 'jane' (any random password).

> ?code=4990047

### Get the access_token - valid for 60 seconds

Use the code from the previous step to exchange it for an access token. Of course, you'd typically do that server side.

`curl https://backend.yoisho.dob.jp/account/access_token?code=4990047&client_id=7b6fc8ed5127b0b2f076d&client_secret=724e6890757b0ae624684b70e111b705fe6b050c`

> {"token_type": "bearer", "scope": "read", "access_token": "eSlcNwnLxTuzsYXyzFrhGGU3mrCKPxQ5fy51Jx93.MTUzMjM1NDM0OA=="}
>

### Get account info for user

Now with this access token we can call the actual API and retrieve the account info from the resource owner, which is the banking client.

`curl -X GET https://backend.yoisho.dob.jp/account/info -H 'Authorization: Bearer eSlcNwnLxTuzsYXyzFrhGGU3mrCKPxQ5fy51Jx93.MTUzMjM1NDM0OA=='`

> {"account_owner": "dave", "fullname": "Dave Thompson", "email": "daveth271@gmail.com", "address": "491-1295, Nishimiyanosawa 6-jo, Teine-ku Sapporo-shi, Hokkaido", "phone": "+8183-977-7817"}
> 


### Get account balance for user

With the same access token we retrieve the account balance from the resource owner, which is the banking client.

`curl -X GET https://backend.yoisho.dob.jp/account/balance -H 'Authorization: Bearer eSlcNwnLxTuzsYXyzFrhGGU3mrCKPxQ5fy51Jx93.MTUzMjM1NDM0OA=='`

> {"account_owner": "dave", "account_balance": "10,187.91"}
> 

### OAuth client - Python implementation

Here's a simple web based client implementation that shows the entire flow in the browser - the banking customer logs in and authorizes the app to access the account balance on their behalf: [Yoisho OAuth Client (Python)](https://github.com/u1i/yoisho/tree/master/yoisho-account-oauth-client)
