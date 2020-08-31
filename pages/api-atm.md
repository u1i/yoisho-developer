---
layout: layouts/api.njk
title: ATM
date: 2016-01-01T00:00:00.000Z
permalink: /apis/atm.html
eleventyNavigation:
  key: atm
  title: ATM Locator API
  order: 7
---

# ATM Locator - REST/JSON

![](/static/img/i6.png)

This API gives you a full CRUDL interface (Create, Read, Update, Delete, List) for ATM locations, using an in memory database.

Two versions:

* /banking/v1 offers CREATE, READ, UPDATE
* /banking/v2 offers CREATE, READ, UPDATE, DELETE, LIST ALL

## Version 1

<a href="https://backend.yoisho.dob.jp/banking/v1/swagger" target="_new">Open API Specification</a>
<a href="https://editor.swagger.io/?url=https://backend.yoisho.dob.jp/banking/v1/swagger" target="_new">Test the API</a>
<a href="https://backend.yoisho.dob.jp/banking/v1/atm/1" target="_new">Sample Request</a>

## Version 2

<a href="https://backend.yoisho.dob.jp/banking/v2/swagger" target="_new">Open API Specification</a>
<a href="https://editor.swagger.io/?url=https://backend.yoisho.dob.jp/banking/v2/swagger" target="_new">Test the API</a>
<a href="https://backend.yoisho.dob.jp/banking/v2/atm/1" target="_new">Sample Request</a>

### Get the Swagger

`curl https://backend.yoisho.dob.jp/banking/v2/swagger`

> { "swagger": "2.0", "info": { "version": "", "title": "ATM Locations", "description": "List of ATM locations for Yoisho Banking Corporation" }, "basePath": "/banking/v2", "consumes": [ "application/json" ], "produces": [ "application/json" ], "paths": { "/atm/{id}": { "parameters": [ { "name": "id", "in": "path", "required": true, "type": "string" } ], "get": { "operationId": "GET-atm-location", "summary": "Get ATM Location", "tags": [ "Atm locations" ], "responses": { "200": { "description": "", "schema": { "$ref": "#/definitions/api-location-input" } } } }, "put": { "operationId": "PUT-atm-location", "summary": "Update ATM Location", "tags": [ "Atm locations" ], "parameters": [ { "name": "body", "in": "body", "schema": { "$ref": "#/definitions/api-location-input" } } ], "responses": { "200": { "description": "", "schema": { "$ref": "#/definitions/api-location-input" } } } }, "delete": { "operationId": "DELETE-atm-location", "summary": "Delete ATM Location", "tags": [ "Atm locations" ], "responses": { "204": { "description": "" } } } }, "/atm": { "get": { "operationId": "LIST-atm-locations", "summary": "List Atm locations", "tags": [ "Atm locations" ], "responses": { "200": { "description": "", "schema": { "type": "object", "properties": { "result": { "type": "array", "items": { "type": "object", "properties": { "lat": { "type": "string" }, "lon": { "type": "string" }, "location": { "type": "string" }, "id": { "type": "string" } } } } } }, "examples": { "application/json": { "data": [ { "lat": "35.6684231", "lon": "139.6833085", "location": "Ebisu Station" }, { "lat": "35.6284713", "lon": "139.736571", "location": "Shinagawa Station" } ] } } } } }, "post": { "operationId": "POST-atm-location", "summary": "Create ATM Location", "tags": [ "Atm locations" ], "parameters": [ { "name": "body", "in": "body", "schema": { "$ref": "#/definitions/api-location-input" } } ], "responses": { "201": { "description": "", "schema": { "$ref": "#/definitions/api-location-input" } } } } } }, "definitions": { "atm-location-input": { "title": "ATM Location Input", "type": "object", "properties": { "location": { "type": "string" }, "lat": { "type": "string" }, "lon": { "type": "string" } }, "required": [ "location" ] } }

### Get an ATM Location

The entries with id 1 and 2 are prepopulated when the container starts:

`curl https://backend.yoisho.dob.jp/banking/v2/atm/1`

> {"lat": "35.6284713", "lon": "139.736571", "location": "Shinagawa Station"}

`curl https://backend.yoisho.dob.jp/banking/v2/atm/2`

> {"lat": "35.6684231", "lon": "139.6833085", "location": "Ebisu Station"}

### Create an ATM

`curl -X POST https://backend.yoisho.dob.jp/banking/v2/atm -d '{ "lat": "35.4657858", "lon": "139.6201245,17", "location": "Yokohama Station" }'"`

> {"message": "created", "id": "565"}

### Delete an ATM

`curl -X DELETE https://backend.yoisho.dob.jp/banking/v2/atm/565`

> {"message": " 565 deleted"}

### Update an ATM

`curl -X PUT https://backend.yoisho.dob.jp/banking/v2/atm/105 -d '{"lat": "123", "lon": "982", "location": "some place"}'`

> {"message": "updated", "id": 105}

### Get all ATM's

`curl https://backend.yoisho.dob.jp/banking/v2/atm`

> {"result": [{"lat": "35.6684231", "lon": "139.6833085", "location": "Ebisu Station", "id": "2"}, {"lat": "35.6284713", "lon": "139.736571", "location": "Shinagawa Station", "id": "1"}]}
