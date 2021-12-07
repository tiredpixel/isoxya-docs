# Apex

## / GET

Read the apex, returning metadata about the API and its status. This route is suitable for use as a healthcheck, indicating whether the API is available and healthy. Calling the route usually operates as a shallow healthcheck; periodically, however, a deep healthcheck is performed, the time of which is exposed as `now`.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-apex  

### Response parameters

| Name      | Type   | Description           |
|-----------|--------|-----------------------|
| `now`     | string | deep healthcheck time |
| `version` | string | API version           |

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
  "now": "2021-12-07T09:10:00.288572447Z",
  "version": "2.1.6.38"
}
```
