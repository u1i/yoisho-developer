---
layout: layouts/api.njk
title: Forex
date: 2016-01-01T00:00:00.000Z
permalink: /apis/currency.html
eleventyNavigation:
  key: Forex API
  order: 9
---

# Currency Exchange Rates - REST/JSON

![](/static/img/i4.png)

This API gives you exchange rates for currencies (USD, GBP and SGD) that the bank buys and sells. Each time you ask for a quote the amounts might be slighly different - they're really busy adjusting the rates constantly!

## Version 1

<a href="https://backend.yoisho.dob.jp/fx/swagger" target="_new">Open API Specification</a>
<a href="https://editor.swagger.io/?url=https://backend.yoisho.dob.jp/fx/swagger" target="_new">Test the API</a>
<a href="https://backend.yoisho.dob.jp/fx/currency?currency=USD" target="_new">Sample Request</a>

### Get the Swagger

`curl https://backend.yoisho.dob.jp/fx/swagger`

> {"info": {"version": "1.0", "description": "", "title": "Yoisho Currency Exchange"}, "paths": {"/get_currency": {"get": {"responses": {"default": {"description": "successful operation"}}, "produces": ["application/json"], "description": "", "parameters": [{"required": true, "type": "string", "description": "The desired currency", "name": "currency", "in": "query"}], "operationId": "get_currency"}}}, "schemes": ["http"], "basePath": "/currency", "host": "", "x-axway": {"deprecated": false, "serviceType": "rest", "basePaths": [""], "corsEnabled": true, "tags": {}}, "swagger": "2.0"}

### Get exchange rates - USD (also supported: GBP, SGD)

`curl https://backend.yoisho.dob.jp/fx/currency?currency=USD`

> {"sell": "489.185", "timestamp": "2017-09-17 02:58:40.194337", "buy": "389.105"}

