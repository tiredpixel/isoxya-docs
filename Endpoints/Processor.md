# Processor

Processors are plugins which extract data from fetched pages. Processors must be registered within the system, making them available to [Crawls](Crawl.md).

### Routes

- [/processor GET](#processor-get)
- [/processor POST](#processor-post)
- [/processor/:processor_id DELETE](#processorprocessor_id-delete)
- [/processor/:processor_id GET](#processorprocessor_id-get)


## /processor GET

List Processors.

https://github.com/tiredpixel/isoxya-api/blob/latest/bin/isoxya-api-list-processor  

### Response parameters

Response parameters are as for [/processor/:processor_id GET](#processorprocessor_id-get).

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
link: </processor>; rel="first", </processor?_next=2021-12-16T14:20:16.32375Z>; rel="next", </processor?_prev=2021-12-16T14:20:16.32375Z>; rel="prev"
```

```json
[
  {
    "channels": 1,
    "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73",
    "tag": "crawler-html",
    "url": "http://isoxya-plugin-crawler-html.localhost/data"
  }
]
```


## /processor POST

Create a Processor.

https://github.com/tiredpixel/isoxya-api/blob/latest/bin/isoxya-api-create-processor  

### Request parameters

| Name       | Edition | Type    | Description                                             |
|------------|---------|---------|---------------------------------------------------------|
| `channels` | Pro     | number? | channels, used for scaling Processors                   |
| `tag`      |         | string  | tag, used for conditional [Streamer](Streamer.md) logic |
| `url`      |         | string  | plugin endpoint URL (absolute)                          |

### Response parameters

Response parameters are as for [/processor/:processor_id GET](#processorprocessor_id-get).

### Request example

```http
POST /processor HTTP/1.1
content-type: application/json
```

```json
{
  "channels": null,
  "tag": "crawler-html",
  "url": "http://isoxya-plugin-crawler-html.localhost/data"
}
```

### Response example

```http
HTTP/1.1 201 Created
content-type: application/json
location: /processor/7135e6c2-3026-44bf-abcc-c64af3efce73
```

```json
{
  "channels": 1,
  "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73",
  "tag": "crawler-html",
  "url": "http://isoxya-plugin-crawler-html.localhost/data"
}
```


## /processor/:processor_id DELETE

Delete a Processor.

https://github.com/tiredpixel/isoxya-api/blob/latest/bin/isoxya-api-delete  

### Response example

```http
HTTP/1.1 204 No Content
```


## /processor/:processor_id GET

Read a Processor.

https://github.com/tiredpixel/isoxya-api/blob/latest/bin/isoxya-api-read  

### Response parameters

| Name       | Edition | Type   | Description                                             |
|------------|---------|--------|---------------------------------------------------------|
| `channels` | Pro     | number | channels, used for scaling Processors                   |
| `href`     |         | string | Href                                                    |
| `tag`      |         | string | tag, used for conditional [Streamer](Streamer.md) logic |
| `url`      |         | string | plugin endpoint URL (absolute)                          |

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
  "channels": 1,
  "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73",
  "tag": "crawler-html",
  "url": "http://isoxya-plugin-crawler-html.localhost/data"
}
```
