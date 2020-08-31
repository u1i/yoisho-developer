---
layout: layouts/api.njk
title: Deposits
date: 2016-01-01T00:00:00.000Z
permalink: /apis/deposit.html
eleventyNavigation:
  key: Deposits
  order: 4
---

![](/static/img/i7.png)

# Fixed Deposit Calculator - REST/JSON

This API calculates the total interest earned from a fixed deposit, along with a breakdown for the number of years the deposit is running. Parameters: amount, number of years the fixed deposit will run

| Version 1| | |
|---|---|---|
| [OpenAPI Specification](https://backend.yoisho.dob.jp/fixeddeposit/swagger)| [Swagger Editor](https://editor.swagger.io/?url=https://backend.yoisho.dob.jp/fixeddeposit/swagger) | [Sample Request](https://backend.yoisho.dob.jp/fixeddeposit/calculate?years=10&amount=20000) |

## API Version 1
<a href="https://backend.yoisho.dob.jp/fixeddeposit/swagger" target="_new">Open API Specification</a>
<a href="https://editor.swagger.io/?url=https://backend.yoisho.dob.jp/fixeddeposit/swagger" target="_new">Test the API</a>
<a href="https://backend.yoisho.dob.jp/fixeddeposit/calculate?years=10&amount=20000" target="_new">Sample Request</a>


### Get the Swagger

`curl https://backend.yoisho.dob.jp/fixeddeposit/swagger`

> { "swagger" : "2.0", "host" : "", "basePath" : "/fixeddeposit", "schemes" : [ "http" ], "paths" : { "/calculate" : { "get" : { "description" : "Calculates the total interest earned from a fixed deposit, along with a breakdown for the number of years the deposit is running.", "operationId" : "calculate", "produces" : [ "application/json" ], "parameters" : [ { "description" : "The number of years the fixed deposit is running.", "required" : true, "in" : "query", "name" : "years", "type" : "string" }, { "description" : "The amount for the fixed deposit", "required" : true, "in" : "query", "name" : "amount", "type" : "string" } ], "responses" : { "200" : { "description" : "OK" }, "400" : { "description" : "Invalid request" } } } } }, "info" : { "title" : "Fixed Deposit Calculator", "description" : "", "version" : "1.0" } }

### Perform Calculation

`curl "https://backend.yoisho.dob.jp/fixeddeposit/calculate?amount=50000&years=12"`

> {"info": "Current interest rate is 3.15% pa.", "yield_breakdown_by_year": [{"amount": "50,000.00", "year": "1"}, {"amount": "51,575.00", "year": "2"}, {"amount": "53,199.61", "year": "3"}, {"amount": "54,875.40", "year": "4"}, {"amount": "56,603.98", "year": "5"}, {"amount": "58,387.00", "year": "6"}, {"amount": "60,226.19", "year": "7"}, {"amount": "62,123.32", "year": "8"}, {"amount": "64,080.20", "year": "9"}, {"amount": "66,098.73", "year": "10"}, {"amount": "68,180.84", "year": "11"}, {"amount": "70,328.53", "year": "12"}], "deposit_amount": "50,000.00", "yield_amount": "70,328.53", "years": "12"}