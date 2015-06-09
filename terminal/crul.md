# CURL & RESTful API

使用 CRUL 指令，在「終端機」程式裡，測試 RESTful API。

http://localhost:9000/api/stores

## List - GET

```
$ curl -i -X GET localhost:9000/api/stores

HTTP/1.1 200 OK
X-Powered-By: Express
content-type: application/json
content-length: 523
etag: "-493307099"
set-cookie: connect.sid=s%3ASK9Kc4u9Rg8J8jpXGCECqAmu.e3TaPE1EADAQkVtMgJYJdJRpixv2461DKu3JwGgxQqI; Path=/; HttpOnly
Vary: Accept-Encoding
Date: Wed, 15 Apr 2015 04:30:14 GMT
Connection: keep-alive

[{"_id":"552bd53e98f4825c4bf3c807","name":"CCC","info":"好吃的的素食店","active":true,"__v":0},{"_id":"552c7b9c5f4a62ae0a94ef5b","name":"XYZ","info":"good food for Veg","active":true,"__v":0},{"_id":"552c7c6b5f4a62ae0a94ef5c","name":"CCC","info":"Veg food","active":true,"__v":0},{"_id":"552d16cf25d005bc0d30b4cf","__v":0},{"_id":"552d1e9925d005bc0d30b4d0","name":"ABC","info":"Tech Books Store","active":false,"__v":0},{"_id":"552d1f4e25d005bc0d30b4d1","name":"XYZ","info":"Vegan Food Store","active":true,"__v":0}]```


## Create - POST

```
$ curl -i -X POST -H "Content-type: application/json" -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{"name":"ABC", "info":"Veg food", "active": true }' localhost:9000/api/stores

HTTP/1.1 201 Created
X-Powered-By: Express
content-type: application/json
content-length: 87
set-cookie: connect.sid=s%3AlFKKif4wEj8yih8DallRlWGP.X5w95Zdy4TFvkG9m54oZqKnSJ50iAKS2S5nl%2BsVB9iA; Path=/; HttpOnly
Vary: Accept-Encoding
Date: Wed, 15 Apr 2015 04:36:52 GMT
Connection: keep-alive

{"__v":0,"name":"ABC","info":"Veg food","active":true,"_id":"552deae4eacdedb112666df3"}
```


## Read - GET

```
$ curl -i -X GET -H "Content-type: application/json" -H "Content-Type: application/json" -H "Cache-Control: no-cache" localhost:9000/api/stores/552deae4eacdedb112666df3

HTTP/1.1 200 OK
X-Powered-By: Express
content-type: application/json
content-length: 87
etag: "10606073"
set-cookie: connect.sid=s%3AzXXnSPTDRl8PmvSPWmf1UqhY.MvpANKkx1QwubR2NKrYnPMcVXMFYZ%2Fgg%2FbMui6Yu8YU; Path=/; HttpOnly
Vary: Accept-Encoding
Date: Wed, 15 Apr 2015 04:38:31 GMT
Connection: keep-alive

{"_id":"552deae4eacdedb112666df3","name":"ABC","info":"Veg food","active":true,"__v":0}
```



## Update - PUT

```
$ curl -i -X PUT -H "Content-type: application/json" -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d  '{"name": "XYZ", "info": "Tech books", "active": false}' localhost:9000/api/stores/552deae4eacdedb112666df3

HTTP/1.1 200 OK
X-Powered-By: Express
content-type: application/json
content-length: 90
set-cookie: connect.sid=s%3Aq2Pt2FudFnaqWnZJU5JIARHy.PIBuMG046AeOnV5qnrmpeEj%2FWo20tz5nxlkD7dimTPg; Path=/; HttpOnly
Vary: Accept-Encoding
Date: Wed, 15 Apr 2015 04:42:09 GMT
Connection: keep-alive

{"_id":"552deae4eacdedb112666df3","name":"XYZ","info":"Tech books","active":false,"__v":0}
```


## Delete - DELETE

```
$ curl -i -X DELETE localhost:9000/api/stores/552deae4eacdedb112666df3

HTTP/1.1 204 No Content
X-Powered-By: Express
set-cookie: connect.sid=s%3APE0PKz1JocPNWuod8MPLTQYI.eug%2BfTbrxPDgVBnPsndbYuBWAGDmWfqw43VfzW2O9uA; Path=/; HttpOnly
Date: Wed, 15 Apr 2015 04:43:44 GMT
Connection: keep-alive

```




