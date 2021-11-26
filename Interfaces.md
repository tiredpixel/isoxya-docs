# Processor

## /* POST

Send page metadata, header, and body to a processor plugin, and receive extracted data and outbound URLs to crawl.

### Request parameters

| Name            | Type    | Description                             |
|-----------------|---------|-----------------------------------------|
| `body`          | string  | page body (Base-64); e.g. HTML or image |
| `header`        | object  | response HTTP header                    |
| `meta.config`   | object? | processor config                        |
| `meta.duration` | number? | request duration (ms)                   |
| `meta.error`    | string? | error; e.g. `RobotDisallowed`           |
| `meta.method`   | string  | request HTTP method                     |
| `meta.status`   | number? | response HTTP status code               |
| `meta.url`      | string  | page URL (absolute)                     |

### Response parameters

| Name   | Type         | Description                                               |
|--------|--------------|-----------------------------------------------------------|
| `data` | object       | free-form extracted data; processor may define own schema |
| `urls` | array.string | outbound URLs (relative or absolute) to crawl             |

### Request example

```http
POST /* HTTP/1.1
content-type: application/json
```

```json
{
  "body": "PCFkb2N0eXBlIGh0bWw+CjxodG1sPgo8aGVhZD4KICAgIDx0aXRsZT5FeGFtcGxlIERvbWFpbjwvdGl0bGU+CgogICAgPG1ldGEgY2hhcnNldD0idXRmLTgiIC8+CiAgICA8bWV0YSBodHRwLWVxdWl2PSJDb250ZW50LXR5cGUiIGNvbnRlbnQ9InRleHQvaHRtbDsgY2hhcnNldD11dGYtOCIgLz4KICAgIDxtZXRhIG5hbWU9InZpZXdwb3J0IiBjb250ZW50PSJ3aWR0aD1kZXZpY2Utd2lkdGgsIGluaXRpYWwtc2NhbGU9MSIgLz4KICAgIDxzdHlsZSB0eXBlPSJ0ZXh0L2NzcyI+CiAgICBib2R5IHsKICAgICAgICBiYWNrZ3JvdW5kLWNvbG9yOiAjZjBmMGYyOwogICAgICAgIG1hcmdpbjogMDsKICAgICAgICBwYWRkaW5nOiAwOwogICAgICAgIGZvbnQtZmFtaWx5OiAtYXBwbGUtc3lzdGVtLCBzeXN0ZW0tdWksIEJsaW5rTWFjU3lzdGVtRm9udCwgIlNlZ29lIFVJIiwgIk9wZW4gU2FucyIsICJIZWx2ZXRpY2EgTmV1ZSIsIEhlbHZldGljYSwgQXJpYWwsIHNhbnMtc2VyaWY7CiAgICAgICAgCiAgICB9CiAgICBkaXYgewogICAgICAgIHdpZHRoOiA2MDBweDsKICAgICAgICBtYXJnaW46IDVlbSBhdXRvOwogICAgICAgIHBhZGRpbmc6IDJlbTsKICAgICAgICBiYWNrZ3JvdW5kLWNvbG9yOiAjZmRmZGZmOwogICAgICAgIGJvcmRlci1yYWRpdXM6IDAuNWVtOwogICAgICAgIGJveC1zaGFkb3c6IDJweCAzcHggN3B4IDJweCByZ2JhKDAsMCwwLDAuMDIpOwogICAgfQogICAgYTpsaW5rLCBhOnZpc2l0ZWQgewogICAgICAgIGNvbG9yOiAjMzg0ODhmOwogICAgICAgIHRleHQtZGVjb3JhdGlvbjogbm9uZTsKICAgIH0KICAgIEBtZWRpYSAobWF4LXdpZHRoOiA3MDBweCkgewogICAgICAgIGRpdiB7CiAgICAgICAgICAgIG1hcmdpbjogMCBhdXRvOwogICAgICAgICAgICB3aWR0aDogYXV0bzsKICAgICAgICB9CiAgICB9CiAgICA8L3N0eWxlPiAgICAKPC9oZWFkPgoKPGJvZHk+CjxkaXY+CiAgICA8aDE+RXhhbXBsZSBEb21haW48L2gxPgogICAgPHA+VGhpcyBkb21haW4gaXMgZm9yIHVzZSBpbiBpbGx1c3RyYXRpdmUgZXhhbXBsZXMgaW4gZG9jdW1lbnRzLiBZb3UgbWF5IHVzZSB0aGlzCiAgICBkb21haW4gaW4gbGl0ZXJhdHVyZSB3aXRob3V0IHByaW9yIGNvb3JkaW5hdGlvbiBvciBhc2tpbmcgZm9yIHBlcm1pc3Npb24uPC9wPgogICAgPHA+PGEgaHJlZj0iaHR0cHM6Ly93d3cuaWFuYS5vcmcvZG9tYWlucy9leGFtcGxlIj5Nb3JlIGluZm9ybWF0aW9uLi4uPC9hPjwvcD4KPC9kaXY+CjwvYm9keT4KPC9odG1sPgo=",
  "header": {
    "Vary": "Accept-Encoding",
    "Content-Type": "text/html; charset=UTF-8",
    "Content-Encoding": "gzip",
    "Etag": "\"3147526947+gzip\"",
    "Expires": "Tue, 02 Feb 2021 11:19:21 GMT",
    "Age": "264946",
    "Last-Modified": "Thu, 17 Oct 2019 07:18:26 GMT",
    "Date": "Tue, 26 Jan 2021 11:19:21 GMT",
    "Server": "ECS (dcb/7EC6)",
    "Content-Length": "648",
    "Cache-Control": "max-age=604800",
    "X-Cache": "HIT"
  },
  "meta": {
    "status": 200,
    "config": null,
    "url": "http://example.com:80/",
    "method": "GET",
    "err": null,
    "duration": {
      "denominator": 1000000000,
      "numerator": 119165427
    }
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
    "status": 200,
    "method": "GET",
    "header": {
      "Vary": "Accept-Encoding",
      "Content-Type": "text/html; charset=UTF-8",
      "Content-Encoding": "gzip",
      "Etag": "\"3147526947+gzip\"",
      "Expires": "Tue, 02 Feb 2021 11:19:21 GMT",
      "Age": "264946",
      "Last-Modified": "Thu, 17 Oct 2019 07:18:26 GMT",
      "Date": "Tue, 26 Jan 2021 11:19:21 GMT",
      "Server": "ECS (dcb/7EC6)",
      "Content-Length": "648",
      "Cache-Control": "max-age=604800",
      "X-Cache": "HIT"
    },
    "err": null,
    "duration": {
      "denominator": 1000000000,
      "numerator": 119165427
    }
  },
  "urls": [
    "https://www.iana.org/domains/example"
  ]
}
```

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
