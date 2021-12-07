# Processor

## /* POST

Send page metadata, header, and body to a [Processor](../Endpoints/Processor.md) plugin, and receive extracted data and outbound URLs to crawl.

### Request parameters

| Name            | Type    | Description                                   |
|-----------------|---------|-----------------------------------------------|
| `body`          | string  | response body (Base-64); e.g. HTML or image   |
| `header`        | object  | response HTTP header                          |
| `meta.config`   | object? | [Processor](../Endpoints/Processor.md) config |
| `meta.duration` | number? | request duration (ms)                         |
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
    "Age": "67245",
    "Cache-Control": "max-age=604800",
    "Content-Encoding": "gzip",
    "Content-Length": "648",
    "Content-Type": "text/html; charset=UTF-8",
    "Date": "Fri, 03 Dec 2021 10:42:58 GMT",
    "Etag": "\"3147526947\"",
    "Expires": "Fri, 10 Dec 2021 10:42:58 GMT",
    "Last-Modified": "Thu, 17 Oct 2019 07:18:26 GMT",
    "Server": "ECS (bsa/EB1B)",
    "Vary": "Accept-Encoding",
    "X-Cache": "HIT"
  },
  "meta": {
    "config": null,
    "duration": 103,
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
    "duration": 103,
    "error": null,
    "header": {
      "Accept-Ranges": "bytes",
      "Age": "67245",
      "Cache-Control": "max-age=604800",
      "Content-Encoding": "gzip",
      "Content-Length": "648",
      "Content-Type": "text/html; charset=UTF-8",
      "Date": "Fri, 03 Dec 2021 10:42:58 GMT",
      "Etag": "\"3147526947\"",
      "Expires": "Fri, 10 Dec 2021 10:42:58 GMT",
      "Last-Modified": "Thu, 17Oct 2019 07:18:26 GMT",
      "Server": "ECS (bsa/EB1B)",
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
