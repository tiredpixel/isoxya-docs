# Streamer

Streamers are plugins which send extracted data elsewhere. Streamers must be registered within the system, making them available to [Crawls](Crawl.md).


## /streamer POST

Create a Streamer.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-create-streamer  

### Request parameters

| Name       | Edition | Type    | Description                          |
|------------|---------|---------|--------------------------------------|
| `channels` | Pro     | number? | channels, used for scaling streamers |
| `tag`      |         | string  | tag                                  |
| `url`      |         | string  | plugin endpoint URL (absolute)       |

### Response parameters

Response parameters are as for [/streamer/:streamer_id GET](#streamerstreamer_id-get).

### Request example

```http
POST /streamer HTTP/1.1
content-type: application/json
```

```json
{
  "channels": null,
  "tag": "nginx-test-upstream",
  "url": "http://nginx-test-upstream.localhost"
}
```

### Response example

```http
HTTP/1.1 201 Created
content-type: application/json
location: /streamer/15e7409e-f7c7-4179-aa25-6e2e1c0babe7
```

```json
{
  "channels": 1,
  "href": "/streamer/15e7409e-f7c7-4179-aa25-6e2e1c0babe7",
  "tag": "nginx-test-upstream",
  "url": "http://nginx-test-upstream.localhost"
}
```


## /streamer GET

List Streamers.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-list-streamer  

### Response parameters

Response parameters are as for [/streamer/:streamer_id GET](#streamerstreamer_id-get).

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
link: </streamer>; rel="first", </streamer?_next=2021-12-13T10:51:20.599317Z>; rel="next", </streamer?_prev=2021-12-13T10:51:20.599317Z>; rel="prev"
```

```json
[
  {
    "channels": 1,
    "href": "/streamer/15e7409e-f7c7-4179-aa25-6e2e1c0babe7",
    "tag": "nginx-test-upstream",
    "url": "http://nginx-test-upstream.localhost"
  }
]
```


## /streamer/:streamer_id GET

Read a Streamer.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-read  

### Response parameters

| Name       | Edition | Type   | Description                          |
|------------|---------|--------|--------------------------------------|
| `channels` | Pro     | number | channels, used for scaling streamers |
| `href`     |         | string | Href                                 |
| `tag`      |         | string | tag                                  |
| `url`      |         | string | plugin endpoint URL (absolute)       |

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
  "channels": 1,
  "href": "/streamer/15e7409e-f7c7-4179-aa25-6e2e1c0babe7",
  "tag": "nginx-test-upstream",
  "url": "http://nginx-test-upstream.localhost"
}
```


## /streamer/:streamer_id DELETE

Delete a Streamer.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-delete  

### Response example

```http
HTTP/1.1 204 No Content
```
