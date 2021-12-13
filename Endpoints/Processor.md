# Processor

Processors are plugins which extract data from fetched pages. Processors must be registered within the system, making them available to [Crawls](Crawl.md).


## /processor POST

Create a Processor.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-create-processor  

### Request parameters

| Name       | Edition | Type    | Description                                             |
|------------|---------|---------|---------------------------------------------------------|
| `channels` | Pro     | number? | channels, used for scaling processors                   |
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
location: /processor/7b3162d0-4519-4231-900c-797e882f964c
```

```json
{
  "channels": 1,
  "href": "/processor/7b3162d0-4519-4231-900c-797e882f964c",
  "tag": "crawler-html",
  "url": "http://isoxya-plugin-crawler-html.localhost/data"
}
```


## /processor GET

List Processors.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-list-processor  

### Response parameters

Response parameters are as for [/processor/:processor_id GET](#processorprocessor_id-get).

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
link: </processor>; rel="first", </processor?_next=2021-12-13T10:51:11.271233Z>; rel="next", </processor?_prev=2021-12-13T10:51:11.271233Z>; rel="prev"
```

```json
[
  {
    "channels": 1,
    "href": "/processor/7b3162d0-4519-4231-900c-797e882f964c",
    "tag": "crawler-html",
    "url": "http://isoxya-plugin-crawler-html.localhost/data"
  }
]
```


## /processor/:processor_id GET

Read a Processor.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-read  

### Response parameters

| Name       | Edition | Type   | Description                                             |
|------------|---------|--------|---------------------------------------------------------|
| `channels` | Pro     | number | channels, used for scaling processors                   |
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
  "href": "/processor/7b3162d0-4519-4231-900c-797e882f964c",
  "tag": "crawler-html",
  "url": "http://isoxya-plugin-crawler-html.localhost/data"
}
```


## /processor/:processor_id DELETE

Delete a Processor.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-delete  

### Response example

```http
HTTP/1.1 204 No Content
```
