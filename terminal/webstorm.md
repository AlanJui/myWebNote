# WebStorm

使用 WebStorm 的 RESTful Client Test Tool 作為 API 測試工具。

## Create (POST)

HTTP method: `POST`

Host/port: `http://localhost:9000`

Path: `/api/stores`

Request Headers:

`Accept: application/json`

`Content-Type: application/json`

`Cache-Control: no-cache`

Request Parameters:

`<nothing>`

Request Body

 `Test`:

 `{"name":"ABC", "info":"Vegan food", "active": true } `


## Update (PUT)

HTTP method: `PUT`

Host/port: `http://localhost:9000`

Path: `/api/stores/552d0d5125d005bc0d30b4cc`

Request Headers:

`Accept: application/json`

`Content-Type: application/json`

`Cache-Control: no-cache`

Request Parameters:

`<nothing>`

Request Body

 `Test`:

 `{"name":"XYZ", "info":"Tech books", "active": false } `

