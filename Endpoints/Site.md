# Site

Sites are websites, such as might be crawled. Sites must be registered within the system, after which [Crawls](Crawl.md) may be created.

### Routes

- [/site POST](#site-post)
- [/site/:site_id GET](#sitesite_id-get)


## /site POST

Create a Site.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-create-site  

### Request parameters

| Name         | Edition | Type    | Description                         |
|--------------|---------|---------|-------------------------------------|
| `channels`   | Pro     | number? | channels, used for scaling Crawlers |
| `rate_limit` | Pro     | number? | rate limit (reqs/s) (decimal)       |
| `url`        |         | string  | URL (absolute)                      |

### Response parameters

Response parameters are as for [/site/:site_id GET](#sitesite_id-get).

### Request example

```http
POST /site HTTP/1.1
content-type: application/json
```

```json
{
  "channels": null,
  "rate_limit": null,
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
  "channels": 1,
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
  "rate_limit": 1,
  "url": "http://example.com:80"
}
```


## /site/:site_id GET

Read a Site.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-read  

### Response parameters

| Name         | Edition | Type   | Description                         |
|--------------|---------|--------|-------------------------------------|
| `channels`   | Pro     | number | channels, used for scaling Crawlers |
| `href`       |         | string | Href                                |
| `rate_limit` | Pro     | number | rate limit (reqs/s) (decimal)       |
| `url`        |         | string | Site URL (absolute)                 |

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
  "channels": 1,
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
  "rate_limit": 1,
  "url": "http://example.com:80"
}
```
