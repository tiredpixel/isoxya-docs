# Apex

### Routes

- [/ GET](#-get)


## / GET

Read the apex, returning metadata about the API and its status. This route is suitable for use as a healthcheck, indicating whether the API is available and healthy. Calling the route usually operates as a shallow healthcheck; periodically, however, a deep healthcheck is performed, the time of which is exposed as `time`.

https://github.com/tiredpixel/isoxya-api/blob/latest/bin/isoxya-api-apex  

### Response parameters

| Name      | Type   | Description           |
|-----------|--------|-----------------------|
| `time`    | string | deep healthcheck time |
| `version` | string | API version           |

### Response example

```http
HTTP/1.1 200 OK
server: Snap/1.1.2.0
content-type: application/json
date: Thu, 16 Dec 2021 17:36:44 GMT
transfer-encoding: chunked
```

```json
{
  "time": "2021-12-16T17:36:44.334647034Z",
  "version": "2.1.6.50"
}
```
