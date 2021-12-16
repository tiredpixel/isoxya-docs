# Processor


## /* POST

Send page metadata, header, and body to a [Processor](../Endpoints/Processor.md) plugin, and receive extracted data and outbound URLs to crawl.

### Request parameters

| Name            | Type    | Description                                   |
|-----------------|---------|-----------------------------------------------|
| `body`          | string  | response body (Base-64); e.g. HTML or image   |
| `header`        | object  | response HTTP header                          |
| `meta.config`   | object? | [Processor](../Endpoints/Processor.md) config |
| `meta.duration` | number? | request duration (s)                          |
| `meta.error`    | string? | error; e.g. `RobotDisallowed`                 |
| `meta.method`   | string  | request HTTP method                           |
| `meta.status`   | number? | response HTTP status code                     |
| `meta.url`      | string  | request URL (absolute)                        |

### Response parameters

| Name   | Type         | Description                                                                            |
|--------|--------------|----------------------------------------------------------------------------------------|
| `data` | object       | free-form extracted data; [Processor](../Endpoints/Processor.md) may define own schema |
| `urls` | array.string | outbound URLs (relative or absolute) to crawl                                          |

### Request example

```http
POST /* HTTP/1.1
content-type: application/json
```

```json
{
  "body": "…",
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
  "meta": {
    "config": null,
    "duration": 0.106178796,
    "error": null,
    "method": "GET",
    "status": 200,
    "url": "http://example.com:80/"
  }
}
```

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
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
  "urls": [
    "https://www.iana.org/domains/example"
  ]
}
```
