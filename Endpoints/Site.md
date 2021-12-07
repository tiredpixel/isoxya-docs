# Site

Sites are websites, such as might be crawled. Sites must be registered within the system, after which Crawls may be created.

## /site POST

Create a Site.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-create-site  

### Request parameters

| Name   | Type   | Description         |
|--------|--------|---------------------|
| `url`  | string | Site URL (absolute) |

### Response parameters

| Name   | Type   | Description         |
|--------|--------|---------------------|
| `href` | string | Href                |
| `url`  | string | Site URL (absolute) |

### Request example

```http
POST /site HTTP/1.1
content-type: application/json
```

```json
{
  "url": "http://example.com"
}
```

### Response example

```http
HTTP/1.1 201 Created
content-type: application/json
location: /site/aHR0cDovL2V4YW1wbGUuY29tOjgw
```

```json
{
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
  "url": "http://example.com:80"
}
```

## /site/:site_id GET

Read a Site.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-read  

### Response parameters

| Name   | Type   | Description         |
|--------|--------|---------------------|
| `href` | string | Href                |
| `url`  | string | Site URL (absolute) |

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
  "url": "http://example.com:80"
}
```
