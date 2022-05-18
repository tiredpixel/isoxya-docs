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

https://github.com/isoxya/isoxya-api/blob/latest/bin/isoxya-api-list-crawl  

### Response parameters

Response parameters are as for [/site/:site_id/crawl/:site_v GET](#sitesite_idcrawlsite_v-get).

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
link: </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl>; rel="first", </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl?_next=2021-12-20T18:09:22.066654Z>; rel="next", </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl?_prev=2021-12-21T10:22:25.188021Z>; rel="prev"
```

```json
[
  {
    "agent": "Isoxya/2.1.6.57 (+https://www.isoxya.com/)",
    "began": "2021-12-20T18:09:22.066654Z",
    "depth_max": null,
    "duration": 0.912608,
    "ended": "2021-12-20T18:09:22.979262Z",
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-20T18:09:22.066654Z",
    "list": null,
    "pages": 1,
    "pages_max": null,
    "parent": null,
    "processor_config": null,
    "processors": [
      {
        "href": "/processor/7490dcfc-9756-46e0-a641-e0fe57ce3e20"
      }
    ],
    "progress": 100,
    "site": {
      "channels": 1,
      "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
      "rate_limit": 1,
      "url": "http://example.com:80"
    },
    "speed": 1.095760720922,
    "status": "completed",
    "streamers": [
      {
        "href": "/streamer/9426239c-97e3-4879-a689-6d5e4f19eadf"
      }
    ],
    "validate": false
  }
]
```


## /site/:site_id/crawl POST

Create a Crawl.

https://github.com/isoxya/isoxya-api/blob/latest/bin/isoxya-api-create-crawl  

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
location: /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-21T10:25:56.434859Z
```

```json
{
  "agent": "Isoxya/0.0.0 (+https://www.isoxya.com/)",
  "began": "2021-12-21T10:25:56.434859Z",
  "depth_max": null,
  "duration": null,
  "ended": null,
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-21T10:25:56.434859Z",
  "list": null,
  "pages": null,
  "pages_max": null,
  "parent": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/7490dcfc-9756-46e0-a641-e0fe57ce3e20"
    }
  ],
  "progress": null,
  "site": {
    "channels": 1,
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
    "rate_limit": 1,
    "url": "http://example.com:80"
  },
  "speed": null,
  "status": "pending",
  "streamers": [
    {
      "href": "/streamer/9426239c-97e3-4879-a689-6d5e4f19eadf"
    }
  ],
  "validate": false
}
```


## /site/:site_id/crawl/:site_v GET

Read a Crawl.

https://github.com/isoxya/isoxya-api/blob/latest/bin/isoxya-api-read  

### Response parameters

| Name               | Edition | Type         | Description                                                       |
|--------------------|---------|--------------|-------------------------------------------------------------------|
| `agent`            | Pro     | string       | user agent                                                        |
| `began`            |         | string       | time began                                                        |
| `depth_max`        | Pro     | number?      | max depth to crawl before terminating; status: `completed`        |
| `duration`         |         | number?      | duration (s) (decimal)                                            |
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
| `speed`            |         | number?      | speed (reqs/s) (decimal)                                          |
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
  "agent": "Isoxya/0.0.0 (+https://www.isoxya.com/)",
  "began": "2021-12-21T10:25:56.434859Z",
  "depth_max": null,
  "duration": 0.574148,
  "ended": "2021-12-21T10:25:57.009007Z",
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-21T10:25:56.434859Z",
  "list": null,
  "pages": 1,
  "pages_max": null,
  "parent": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/7490dcfc-9756-46e0-a641-e0fe57ce3e20"
    }
  ],
  "progress": 100,
  "site": {
    "channels": 1,
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
    "rate_limit": 1,
    "url": "http://example.com:80"
  },
  "speed": 1.741711196416,
  "status": "completed",
  "streamers": [
    {
      "href": "/streamer/9426239c-97e3-4879-a689-6d5e4f19eadf"
    }
  ],
  "validate": false
}
```


## /site/:site_id/crawl/:site_v PATCH (Pro)

Update a Crawl. Currently, this only supports cancelling a Crawl. Pro edition only.

https://github.com/isoxya/isoxya-api/blob/latest/bin/pro/isoxya-api-update-crawl-cancel  

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
  "agent": "Isoxya/0.0.0 (+https://www.isoxya.com/)",
  "began": "2021-12-21T10:27:22.331372Z",
  "depth_max": null,
  "duration": null,
  "ended": null,
  "href": "/site/aHR0cHM6Ly93d3cuaXNveHlhLmNvbTo0NDM/crawl/2021-12-21T10:27:22.331372Z",
  "list": null,
  "pages": 1,
  "pages_max": null,
  "parent": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/7490dcfc-9756-46e0-a641-e0fe57ce3e20"
    }
  ],
  "progress": 0,
  "site": {
    "channels": 1,
    "href": "/site/aHR0cHM6Ly93d3cuaXNveHlhLmNvbTo0NDM",
    "rate_limit": 1,
    "url": "https://www.isoxya.com:443"
  },
  "speed": null,
  "status": "canceled",
  "streamers": [
    {
      "href": "/streamer/9426239c-97e3-4879-a689-6d5e4f19eadf"
    }
  ],
  "validate": false
}
```


## /site/:site_id/crawl/:site_v/crawl GET (Pro)

List a Crawl's child Crawls. These are created automatically when validating external links. Pro edition only.

https://github.com/isoxya/isoxya-api/blob/latest/bin/pro/isoxya-api-list-crawl-crawl  

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
    "agent": "Isoxya/0.0.0 (+https://www.isoxya.com/)",
    "began": "2021-12-21T10:28:23.236312Z",
    "depth_max": 1,
    "duration": null,
    "ended": null,
    "href": "/site/aHR0cHM6Ly93d3cuaWFuYS5vcmc6NDQz/crawl/2021-12-21T10:28:23.236312Z",
    "list": {
      "href": "/list/ea0f9a97-7e61-4295-a689-ac1a80ec2f04"
    },
    "pages": 1,
    "pages_max": null,
    "parent": {
      "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-21T10:28:06.384183Z"
    },
    "processor_config": null,
    "processors": [
      {
        "href": "/processor/7490dcfc-9756-46e0-a641-e0fe57ce3e20"
      }
    ],
    "progress": 0,
    "site": {
      "channels": 1,
      "href": "/site/aHR0cHM6Ly93d3cuaWFuYS5vcmc6NDQz",
      "rate_limit": 1,
      "url": "https://www.iana.org:443"
    },
    "speed": null,
    "status": "pending",
    "streamers": [
      {
        "href": "/streamer/9426239c-97e3-4879-a689-6d5e4f19eadf"
      }
    ],
    "validate": false
  }
]
```
