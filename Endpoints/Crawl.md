# Crawl

Crawls are visits to a website, during which crawlers fetch pages, processors extract data from fetched pages, and streamers send extracted data elsewhere. It is not possible to crawl more than one Site within a single Crawl; for that, multiple Crawls should be utilised.

## /site/:site_id/crawl POST

Create a Crawl.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-create-crawl  

### Request parameters

| Name               | Type         | Description      |
|--------------------|--------------|------------------|
| `processor_config` | object       | Processor config |
| `processors`       | array.object | Processors       |
| `streamers`        | array.object | Streamers        |

### Response parameters

Response parameters are as for [/site/:site_id/crawl/:site_v GET](#sitesite_idcrawlsite_v-get).

### Request example

```http
POST /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl HTTP/1.1
content-type: application/json
```

```json
{
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/cebc70e8-b303-433e-a9ac-aa98a8410e1c"
    }
  ],
  "streamers": [
    {
      "href": "/streamer/85bdb819-5c47-4068-9b37-4992311dff79"
    }
  ]
}
```

### Response example

```http
HTTP/1.1 201 Created
content-type: application/json
location: /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-07T10:54:24.964572481Z
```

```json
{
  "began": "2021-12-07T10:54:24.964572481Z",
  "ended": null,
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-07T10:54:24.964572481Z",
  "pages": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/cebc70e8-b303-433e-a9ac-aa98a8410e1c"
    }
  ],
  "progress": null,
  "site": {
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
    "url": "http://example.com:80"
  },
  "status": "pending",
  "streamers": [
    {
      "href": "/streamer/85bdb819-5c47-4068-9b37-4992311dff79"
    }
  ]
}
```

## /site/:site_id/crawl GET

List Crawls.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-list-crawl  

### Response parameters

Response parameters are as for [/site/:site_id/crawl/:site_v GET](#sitesite_idcrawlsite_v-get).

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
link: </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl>; rel="first", </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl?_next=2021-12-07T10:54:24.964572481Z>; rel="next", </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl?_prev=2021-12-07T10:54:24.964572481Z>; rel="prev"
```

```json
[
  {
    "began": "2021-12-07T10:54:24.964572481Z",
    "ended": "2021-12-07T10:54:25.595Z",
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-07T10:54:24.964572481Z",
    "pages": 1,
    "processor_config": null,
    "processors": [
      {
        "href": "/processor/cebc70e8-b303-433e-a9ac-aa98a8410e1c"
      }
    ],
    "progress": 100,
    "site": {
      "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
      "url": "http://example.com:80"
    },
    "status": "completed",
    "streamers": [
      {
        "href": "/streamer/85bdb819-5c47-4068-9b37-4992311dff79"
      }
    ]
  }
]
```

## /site/:site_id/crawl/:site_v GET

Read a Crawl.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-read  

### Response parameters

| Name               | Type         | Description                                           |
|--------------------|--------------|-------------------------------------------------------|
| `began`            | string       | time began                                            |
| `ended`            | string?      | time ended                                            |
| `href`             | string       | Href                                                  |
| `pages`            | number?      | total pages discovered                                |
| `processor_config` | object       | Processor config                                      |
| `processors`       | array.object | Processors                                            |
| `progress`         | number?      | progress (%)                                          |
| `site`             | object       | Site                                                  |
| `status`           | string       | status: `pending`, `completed`, `limited`, `canceled` |
| `streamers`        | array.object | Streamers                                             |

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
  "began": "2021-12-07T10:54:24.964572481Z",
  "ended": "2021-12-07T10:54:25.595Z",
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-07T10:54:24.964572481Z",
  "pages": 1,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/cebc70e8-b303-433e-a9ac-aa98a8410e1c"
    }
  ],
  "progress": 100,
  "site": {
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
    "url": "http://example.com:80"
  },
  "status": "completed",
  "streamers": [
    {
      "href": "/streamer/85bdb819-5c47-4068-9b37-4992311dff79"
    }
  ]
}
```
