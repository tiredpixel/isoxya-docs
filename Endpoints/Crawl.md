# Crawl

Crawls are visits to a website, during which Crawlers fetch pages, [Processors](Processor.md) extract data from fetched pages, and [Streamers](Streamer.md) send extracted data elsewhere. It is not possible to crawl more than one [Site](Site.md) within a single Crawl; for that, multiple Crawls should be utilised.

### Routes

- [/site/:site_id/crawl GET](#sitesite_idcrawl-get)
- [/site/:site_id/crawl POST](#sitesite_idcrawl-post)
- [/site/:site_id/crawl/:site_v GET](#sitesite_idcrawlsite_v-get)
- [/site/:site_id/crawl/:site_v PATCH (Pro)](#sitesite_idcrawlsite_v-patch-pro)
- [/site/:site_id/crawl/:site_v/crawl GET (Pro)](#sitesite_idcrawlsite_vcrawl-get-pro)


## /site/:site_id/crawl GET

List Crawls.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-list-crawl  

### Response parameters

Response parameters are as for [/site/:site_id/crawl/:site_v GET](#sitesite_idcrawlsite_v-get).

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
link: </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl>; rel="first", </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl?_next=2021-12-16T14:21:41.719297Z>; rel="next", </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl?_prev=2021-12-16T14:39:43.509573Z>; rel="prev"
```

```json
[
  {
    "agent": null,
    "began": "2021-12-16T14:39:43.509573Z",
    "depth_max": null,
    "ended": "2021-12-16T14:39:44.239858Z",
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T14:39:43.509573Z",
    "list": null,
    "pages": 1,
    "pages_max": null,
    "parent": null,
    "processor_config": null,
    "processors": [
      {
        "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73"
      }
    ],
    "progress": 100,
    "site": {
      "channels": 1,
      "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
      "rate_lim": 1,
      "url": "http://example.com:80"
    },
    "status": "completed",
    "streamers": [
      {
        "href": "/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac"
      }
    ],
    "validate": false
  }
]
```


## /site/:site_id/crawl POST

Create a Crawl.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-create-crawl  

### Request parameters

| Name               | Edition | Type         | Description                                                       |
|--------------------|---------|--------------|-------------------------------------------------------------------|
| `agent`            | Pro     | string?      | user agent                                                        |
| `depth_max`        | Pro     | number?      | max depth to crawl before terminating; status: `completed`        |
| `list`             | Pro     | object?      | [List](List.md) Crawl; otherwise Web Crawl                        |
| `pages_max`        | Pro     | number?      | max Pages (approx) to crawl before terminating; status: `limited` |
| `processor_config` |         | object?      | [Processor](Processor.md) config                                  |
| `processors`       |         | array.object | [Processors](Processor.md)                                        |
| `streamers`        |         | array.object | [Streamers](Streamer.md)                                          |
| `validate`         | Pro     | boolean?     | validate external links by automatically creating child Crawls    |

### Response parameters

Response parameters are as for [/site/:site_id/crawl/:site_v GET](#sitesite_idcrawlsite_v-get).

### Request example

```http
POST /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl HTTP/1.1
content-type: application/json
```

```json
{
  "agent": null,
  "depth_max": null,
  "list": null,
  "pages_max": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73"
    }
  ],
  "streamers": [
    {
      "href": "/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac"
    }
  ],
  "validate": null
}
```

### Response example

```http
HTTP/1.1 201 Created
content-type: application/json
location: /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T14:39:43.509573Z
```

```json
{
  "agent": null,
  "began": "2021-12-16T14:39:43.509573Z",
  "depth_max": null,
  "ended": null,
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T14:39:43.509573Z",
  "list": null,
  "pages": null,
  "pages_max": null,
  "parent": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73"
    }
  ],
  "progress": null,
  "site": {
    "channels": 1,
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
    "rate_lim": 1,
    "url": "http://example.com:80"
  },
  "status": "pending",
  "streamers": [
    {
      "href": "/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac"
    }
  ],
  "validate": false
}
```


## /site/:site_id/crawl/:site_v GET

Read a Crawl.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-read  

### Response parameters

| Name               | Edition | Type         | Description                                                       |
|--------------------|---------|--------------|-------------------------------------------------------------------|
| `agent`            | Pro     | string?      | user agent                                                        |
| `began`            |         | string       | time began                                                        |
| `depth_max`        | Pro     | number?      | max depth to crawl before terminating; status: `completed`        |
| `ended`            |         | string?      | time ended                                                        |
| `href`             |         | string       | Href                                                              |
| `list`             | Pro     | object?      | [List](List.md) Crawl; otherwise Web Crawl                        |
| `pages`            |         | number?      | total Pages discovered                                            |
| `pages_max`        | Pro     | number?      | max Pages (approx) to crawl before terminating; status: `limited` |
| `parent`           | Pro     | object?      | parent Crawl; set when validating external links                  |
| `processor_config` |         | object?      | [Processor](Processor.md) config                                  |
| `processors`       |         | array.object | [Processors](Processor.md)                                        |
| `progress`         |         | number?      | progress (%)                                                      |
| `site`             |         | object       | [Site](Site.md)                                                   |
| `status`           |         | string       | status: `pending`, `completed`, `limited`, `canceled`             |
| `streamers`        |         | array.object | [Streamers](Streamer.md)                                          |
| `validate`         | Pro     | boolean      | validate external links by automatically creating child Crawls    |

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
  "agent": null,
  "began": "2021-12-16T14:39:43.509573Z",
  "depth_max": null,
  "ended": "2021-12-16T14:39:44.239858Z",
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T14:39:43.509573Z",
  "list": null,
  "pages": 1,
  "pages_max": null,
  "parent": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73"
    }
  ],
  "progress": 100,
  "site": {
    "channels": 1,
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
    "rate_lim": 1,
    "url": "http://example.com:80"
  },
  "status": "completed",
  "streamers": [
    {
      "href": "/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac"
    }
  ],
  "validate": false
}
```


## /site/:site_id/crawl/:site_v PATCH (Pro)

Update a Crawl. Currently, this only supports cancelling a Crawl. Pro edition only.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/pro/isoxya-api-update-crawl-cancel  

### Request parameters

| Name               | Edition | Type    | Description                      |
|--------------------|---------|---------|----------------------------------|
| `status`           | Pro     | string? | status: `canceled` cancels Crawl |

### Response parameters

Response parameters are as for [/site/:site_id/crawl/:site_v GET](#sitesite_idcrawlsite_v-get).

### Request example

```http
PATCH /site/aHR0cHM6Ly93d3cuaXNveHlhLmNvbTo0NDM/crawl/2021-12-16T15:09:17.270107Z HTTP/1.1
content-type: application/json
```

```json
{
  "status": "canceled"
}
```

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
  "agent": null,
  "began": "2021-12-16T15:09:17.270107Z",
  "depth_max": null,
  "ended": null,
  "href": "/site/aHR0cHM6Ly93d3cuaXNveHlhLmNvbTo0NDM/crawl/2021-12-16T15:09:17.270107Z",
  "list": null,
  "pages": 1,
  "pages_max": null,
  "parent": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73"
    }
  ],
  "progress": 0,
  "site": {
    "channels": 1,
    "href": "/site/aHR0cHM6Ly93d3cuaXNveHlhLmNvbTo0NDM",
    "rate_lim": 1,
    "url": "https://www.isoxya.com:443"
  },
  "status": "canceled",
  "streamers": [
    {
      "href": "/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac"
    }
  ],
  "validate": false
}
```


## /site/:site_id/crawl/:site_v/crawl GET (Pro)

List a Crawl's child Crawls. These are created automatically when validating external links. Pro edition only.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/pro/isoxya-api-list-crawl-crawl  

### Response parameters

Response parameters are as for [/site/:site_id/crawl/:site_v GET](#sitesite_idcrawlsite_v-get).

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
link: </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T16:16:55.511303Z/crawl>; rel="first", </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T16:16:55.511303Z/crawl?_next=2021-12-16T16:18:47.399965Z>; rel="next", </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T16:16:55.511303Z/crawl?_prev=2021-12-16T16:18:47.399965Z>; rel="prev"
```

```json
[
  {
    "agent": null,
    "began": "2021-12-16T16:18:47.399965Z",
    "depth_max": 1,
    "ended": null,
    "href": "/site/aHR0cHM6Ly93d3cuaWFuYS5vcmc6NDQz/crawl/2021-12-16T16:18:47.399965Z",
    "list": {
      "href": "/list/57602e9c-2ffd-497c-a097-6e8eef3f92bb"
    },
    "pages": 1,
    "pages_max": null,
    "parent": {
      "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T16:16:55.511303Z"
    },
    "processor_config": null,
    "processors": [
      {
        "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73"
      }
    ],
    "progress": 0,
    "site": {
      "channels": 1,
      "href": "/site/aHR0cHM6Ly93d3cuaWFuYS5vcmc6NDQz",
      "rate_lim": 1,
      "url": "https://www.iana.org:443"
    },
    "status": "pending",
    "streamers": [
      {
        "href": "/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac"
      }
    ],
    "validate": false
  }
]
```
