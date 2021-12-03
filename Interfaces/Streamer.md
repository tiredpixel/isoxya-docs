# Streamer

## /* POST

Send extracted data and page metadata to a streamer plugin.

### Request parameters

| Name             | Type   | Description                                               |
|------------------|--------|-----------------------------------------------------------|
| `crawl.began`    | string | Crawl time began                                          |
| `crawl.href`     | string | Crawl Href                                                |
| `data`           | object | free-form extracted data; processor may define own schema |
| `processor.href` | string | Processor Href                                            |
| `processor.tag`  | string | Processor tag; used for conditional data-streamer logic   |
| `retrieved`      | string | page time retrieved                                       |
| `site.href`      | string | Site Href                                                 |
| `site.url`       | string | Site URL (absolute)                                       |
| `url`            | string | page URL (absolute)                                       |

### Response parameters

None.

### Request example

```http
POST /* HTTP/1.1
content-type: application/json
```

```json
{
  "crawl": {
    "began": "2021-12-03T10:59:54.064096684Z",
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-03T10:59:54.064096684Z"
  },
  "data": {
    "duration": 205,
    "error": null,
    "header": {
      "Accept-Ranges": "bytes",
      "Age": "201579",
      "Cache-Control": "max-age=604800",
      "Content-Encoding": "gzip",
      "Content-Length": "648",
      "Content-Type": "text/html; charset=UTF-8",
      "Date": "Fri, 03 Dec 2021 10:59:54 GMT",
      "Etag": "\"3147526947+gzip\"",
      "Expires": "Fri, 10 Dec 2021 10:59:54 GMT",
      "Last-Modified": "Thu, 17 Oct 2019 07:18:26 GMT",
      "Server": "ECS (bsa/EB24)",
      "Vary": "Accept-Encoding",
      "X-Cache": "HIT"
    },
    "method": "GET",
    "status": 200
  },
  "processor": {
    "href": "/processor/17f17cef-6eb3-4bf4-bbf0-a3d729b3d650",
    "tag": "crawler-html"
  },
  "retrieved": "2021-12-03T10:59:54.188859267Z",
  "site": {
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
    "url": "http://example.com:80"
  },
  "url": "http://example.com:80/"
}
```

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```
