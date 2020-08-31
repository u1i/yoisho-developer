---
layout: layouts/api.njk
title: Assets
date: 2016-01-01T00:00:00.000Z
permalink: /apis/assets.html
eleventyNavigation:
  key: assets
  title: Bank Assets API
  order: 8
---

# Bank Assets - SOAP/XML

![](/static/img/i3.png)

A webservice that gives you total assets and debt of the bank. Each request will produce a slightly different result - it's a busy bank so cash is flowing in & out constantly!

## Version 1

<a href="https://backend.yoisho.dob.jp/soap?WSDL" target="_new">WSDL</a>

### Get the WSDL

`curl https://backend.yoisho.dob.jp/soap/?WSDL`

<img src="https://raw.githubusercontent.com/u1i/yoisho/master/resources/wsdl.png" width="650"/>

### Import & run the request in SoapUI

<img src="https://raw.githubusercontent.com/u1i/yoisho/master/resources/soap.png" width="650"/>

### SOAP to REST Conversion

We're working on that. In fact, we saw that Axway's API Management solution can do that automatically!
