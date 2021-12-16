# Streamer


## /* POST

Send extracted data and page metadata to a [Streamer](../Endpoints/Streamer.md) plugin.

### Request parameters

| Name             | Type   | Description                                                                            |
|------------------|--------|----------------------------------------------------------------------------------------|
| `crawl.began`    | string | [Crawl](../Endpoints/Crawl.md) time began                                              |
| `crawl.href`     | string | [Crawl](../Endpoints/Crawl.md) Href                                                    |
| `data`           | object | free-form extracted data; [Processor](../Endpoints/Processor.md) may define own schema |
| `processor.href` | string | [Processor](../Endpoints/Processor.md) Href                                            |
| `processor.tag`  | string | [Processor](../Endpoints/Processor.md) tag; used for conditional data-streamer logic   |
| `retrieved`      | string | Page time retrieved                                                                    |
| `site.href`      | string | [Site](../Endpoints/Site.md) Href                                                      |
| `site.url`       | string | [Site](../Endpoints/Site.md) URL (absolute)                                            |
| `url`            | string | Page URL (absolute)                                                                    |

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
    "began": "2021-12-16T14:29:02.556263Z",
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T14:29:02.556263Z"
  },
  "data": {
    "duration": 0.106178796,
    "error": null,
    "header": {
      "Accept-Ranges": "bytes",
      "Age": "602398",
      "Cache-Control": "max-age=604800",
      "Content-Encoding": "gzip",
      "Content-Length": "648",
      "Content-Type": "text/html; charset=UTF-8",
      "Date": "Thu, 16 Dec 2021 14:29:02 GMT",
      "Etag": "\"3147526947+ident\"",
      "Expires": "Thu, 23 Dec 2021 14:29:02 GMT",
      "Last-Modified": "Thu, 17 Oct 2019 07:18:26 GMT",
      "Server": "ECS (bsa/EB13)",
      "Vary": "Accept-Encoding",
      "X-Cache": "HIT"
    },
    "method": "GET",
    "status": 200
  },
  "processor": {
    "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73",
    "tag": "crawler-html"
  },
  "retrieved": "2021-12-16T14:29:02.851969124Z",
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
