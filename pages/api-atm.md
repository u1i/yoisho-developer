---
layout: layouts/api.njk
title: Investment
date: 2016-01-01T00:00:00.000Z
permalink: /apis/atm.html
eleventyNavigation:
  key: ATM Locator API
  order: 7
---

# ATM Locator - REST/JSON

![](/static/img/i6.png)

This API gives you a full CRUDL interface (Create, Read, Update, Delete, List) for ATM locations, using an in memory database.

Two versions:

* /banking/v1 offers CREATE, READ, UPDATE
* /banking/v2 offers CREATE, READ, UPDATE, DELETE, LIST ALL

## Version 1

<a href="http://backend.yoisho.dob.jp/banking/v1/swagger" target="_new">Open API Specification</a>
<a href="https://editor.swagger.io/?url=https://backend.yoisho.dob.jp/banking/v1/swagger" target="_new">Test the API</a>
<a href="http://backend.yoisho.dob.jp/banking/v1/atm/1" target="_new">Sample Request</a>

## Version 2

<a href="http://backend.yoisho.dob.jp/banking/v2/swagger" target="_new">Open API Specification</a>
<a href="https://editor.swagger.io/?url=https://backend.yoisho.dob.jp/banking/v2/swagger" target="_new">Test the API</a>
<a href="http://backend.yoisho.dob.jp/banking/v2/atm/1" target="_new">Sample Request</a>


### Get the Swagger (Version 1)

`curl https://backend.yoisho.dob.jp/invest/v1/swagger`

> {"info": {"version": "", "description": "Provides investment insights of top performing funds", "title": "Investments"}, "paths": {"/investments": {"get": {"summary": "Get Top Performing Funds", "responses": {"200": {"description": "", "schema": {"$ref": "#/definitions/investments"}}}, "tags": ["Investments"], "operationId": "GET-investments"}}}, "produces": ["application/json"], "definitions": {"investments": {"items": {"type": "object", "properties": {"performance": {"type": "string"}, "currency": {"type": "string"}, "performance_rating": {"type": "string"}, "id": {"type": "string"}, "name": {"type": "string"}}}, "type": "array", "example": [{"performance": "78", "currency": "JPY", "performance_rating": "1", "id": "YB0GB893", "name": "First Arima Onsen"}, {"performance": "71", "currency": "USD", "performance_rating": "2", "id": "YB0IM691", "name": "Castle Rock Index Fund"}], "title": "investments"}}, "basePath": "/v1", "swagger": "2.0", "consumes": ["application/json"]}

### Get top performing funds (Version 1)

`curl https://backend.yoisho.dob.jp/invest/v1/products`

> [{"performance": "78", "currency": "JPY", "performance_rating": "1", "id": "YB0GB893", "name": "First Arima Onsen"}, {"performance": "71", "currency": "USD", "performance_rating": "2", "id": "YB0IM691", "name": "Castle Rock Index Fund"}, {"performance": "69", "currency": "RMB", "performance_rating": "2", "id": "YB0SD611", "name": "Odee Hangzhou BC"}, {"performance": "56", "currency": "USD", "performance_rating": "3", "id": "YB0AA223", "name": "Sedona 500"}, {"performance": "51", "currency": "EUR", "performance_rating": "4", "id": "YB0DE781", "name": "Munich WB2"}]

### Get the Swagger (Version 2)

`curl https://backend.yoisho.dob.jp/invest/v2/swagger`

> {"info": {"version": "", "description": "Provides investment insights of top performing funds", "title": "Investments"}, "paths": {"/investments": {"get": {"summary": "Get Top Performing Funds", "responses": {"200": {"description": "", "schema": {"$ref": "#/definitions/investments"}}}, "tags": ["Investments"], "operationId": "GET-investments"}}}, "produces": ["application/json"], "definitions": {"investments": {"items": {"type": "object", "properties": {"performance_rating": {"type": "string"}, "name": {"type": "string"}, "previous_performance_rating": {"type": "string"}, "currency": {"type": "string"}, "performance": {"type": "string"}, "id": {"type": "string"}}}, "type": "array", "example": [{"performance_rating": "1", "name": "First Arima Onsen", "previous_performance_rating": "2", "currency": "JPY", "performance": "78", "id": "YB0GB893"}, {"performance_rating": "2", "name": "Castle Rock Index Fund", "previous_performance_rating": "3", "currency": "USD", "performance": "71", "id": "YB0IM691"}], "title": "investments"}}, "basePath": "/v2", "swagger": "2.0", "consumes": ["application/json"]}

### Get top performing funds (Version 2)

`curl https://backend.yoisho.dob.jp/invest/v2/products`

> [{"performance_rating": "1", "name": "First Arima Onsen", "previous_performance_rating": "1", "currency": "JPY", "performance": "78", "id": "YB0GB893"}, {"performance_rating": "2", "name": "Castle Rock Index Fund", "previous_performance_rating": "1", "currency": "USD", "performance": "71", "id": "YB0IM691"}, {"performance_rating": "2", "name": "Odee Hangzhou BC", "previous_performance_rating": "0", "currency": "RMB", "performance": "69", "id": "YB0SD611"}, {"performance_rating": "3", "name": "Sedona 500", "previous_performance_rating": "4", "currency": "USD", "performance": "56", "id": "YB0AA223"}, {"performance_rating": "4", "name": "Munich WB2", "previous_performance_rating": "2", "currency": "EUR", "performance": "51", "id": "YB0DE781"}]

