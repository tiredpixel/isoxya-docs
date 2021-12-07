# Processor

Processors are plugins which extract data from a crawled page. Processors must be registered within the system, making them available to Crawls.

## /processor POST

Create a Processor.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-create-processor  

### Request parameters

| Name   | Type   | Description                              |
|--------|--------|------------------------------------------|
| `tag`  | string | tag, used for conditional Streamer logic |
| `url`  | string | plugin endpoint URL (absolute)           |

### Response parameters

Response parameters are as for [/processor/:processor_id GET](#processorprocessor_id-get).

### Request example

```http
POST /processor HTTP/1.1
content-type: application/json
```

```json
{
  "tag": "crawler-html",
  "url": "http://isoxya-plugin-crawler-html.localhost/data"
}
```

### Response example

```http
HTTP/1.1 201 Created
content-type: application/json
location: /processor/0ba4a54a-f9a0-4cad-8f66-a8e94e8cd30a
```

```json
{
  "href": "/processor/0ba4a54a-f9a0-4cad-8f66-a8e94e8cd30a",
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
link: </processor>; rel="first", </processor?_next=2021-12-03T12:34:05.199Z>; rel="next", </processor?_prev=2021-12-03T12:34:05.199Z>; rel="prev"
```

```json
[
  {
    "href": "/processor/0ba4a54a-f9a0-4cad-8f66-a8e94e8cd30a",
    "tag": "crawler-html",
    "url": "http://isoxya-plugin-crawler-html.localhost/data"
  }
]
```

## /processor/:processor_id GET

Read a Processor.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-read  

### Response parameters

| Name   | Type   | Description                              |
|--------|--------|------------------------------------------|
| `href` | string | Href                                     |
| `tag`  | string | tag, used for conditional Streamer logic |
| `url`  | string | plugin endpoint URL (absolute)           |

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
  "href": "/processor/0ba4a54a-f9a0-4cad-8f66-a8e94e8cd30a",
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
