---
layout: layouts/api.njk
title: Quote
date: 2016-01-01T00:00:00.000Z
permalink: /apis/quote.html
eleventyNavigation:
  key: Stockquote API
  order: 10
---

# Stock Quote - REST/JSON

![](/static/img/i3.png)

This API returns the stock price of Yoisho Banking Corp. The data updates every minute, it's also sending additional Cache-Control headers.

## Version 1

<a href="https://backend.yoisho.dob.jp/stockquote/swagger" target="_new">Open API Specification</a>
<a href="https://editor.swagger.io/?url=https://backend.yoisho.dob.jp/stockquote/swagger" target="_new">Test the API</a>
<a href="https://backend.yoisho.dob.jp/stockquote/current" target="_new">Sample Request</a>

### Get the Swagger

`curl https://backend.yoisho.dob.jp/stockquote/swagger`

> { "swagger" : "2.0", "host" : "", "basePath" : "/stockquote", "schemes" : [ "http" ], "paths" : { "/current" : { "get" : { "description" : "", "operationId" : "get_quote", "produces" : [ "application/json" ], "responses" : { "default" : { "description" : "successful operation" } } } } }, "info" : { "title" : "Yoisho Stock Quote", "description" : "", "version" : "1.0" }, "x-axway" : { "corsEnabled" : true, "basePaths" : [ "" ], "serviceType" : "rest", "deprecated" : false, "tags" : { } } }

### Get current quote

`curl ttps://backend.yoisho.dob.jp/stockquote/current`

> {"message": "Stock Price refreshes every minute", "stockprice": "371.44"}
