# Apex

### Routes

- [/ GET](#-get)


## / GET

Read the apex, returning metadata about the API and its status. This route is suitable for use as a healthcheck, indicating whether the API is available and healthy. Calling the route usually operates as a shallow healthcheck; periodically, however, a deep healthcheck is performed, the time of which is exposed as `time`.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-apex  

### Response parameters

| Name      | Type   | Description           |
|-----------|--------|-----------------------|
| `time`    | string | deep healthcheck time |
| `version` | string | API version           |

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
  "time": "2021-12-16T14:34:28.704403831Z",
  "version": "2.1.6.49"
}
```
