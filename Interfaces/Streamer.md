# Interfaces: Streamer

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
  "crwl": {
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crwl/2021-01-26T11:46:21.411346Z",
    "t_begin": "2021-01-26T11:46:21.411346Z"
  },
  "org": {
    "href": "/org/1df9ee03-3c25-4ea6-9276-d4c7a58de332"
  },
  "t_retrieval": "2021-01-26T11:46:21.908809003Z",
  "data": {
    "status": 200,
    "method": "GET",
    "header": {
      "Vary": "Accept-Encoding",
      "Content-Type": "text/html; charset=UTF-8",
      "Content-Encoding": "gzip",
      "Etag": "\"3147526947\"",
      "Expires": "Tue, 02 Feb 2021 11:46:21 GMT",
      "Age": "425384",
      "Last-Modified": "Thu, 17 Oct 2019 07:18:26 GMT",
      "Date": "Tue, 26 Jan 2021 11:46:21 GMT",
      "Server": "ECS (dcb/7F15)",
      "Content-Length": "648",
      "Cache-Control": "max-age=604800",
      "Accept-Ranges": "bytes",
      "X-Cache": "HIT"
    },
    "err": null,
    "duration": {
      "denominator": 250000000,
      "numerator": 30304037
    }
  },
  "url": "http://example.com:80/",
  "plug_proc": {
    "tag": "crawler-html",
    "href": "/plug_proc/76ce4d4a-a965-4ab4-9fae-2c375750cb0f"
  },
  "site": {
    "url": "http://example.com:80",
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw"
  }
}
```

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```
