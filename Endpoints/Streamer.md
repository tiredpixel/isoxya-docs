# Streamer

Streamers are plugins which send extracted data elsewhere. Streamers must be registered within the system, making them available to Crawls.

## /streamer POST

Create a Streamer.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-create-streamer  

### Request parameters

| Name   | Type   | Description                    |
|--------|--------|--------------------------------|
| `tag`  | string | tag                            |
| `url`  | string | plugin endpoint URL (absolute) |

### Response parameters

Response parameters are as for [/streamer/:streamer_id GET](#streamerstreamer_id-get).

### Request example

```http
POST /streamer HTTP/1.1
content-type: application/json
```

```json
{
  "tag": "nginx-test-upstream",
  "url": "http://nginx-test-upstream.localhost"
}
```

### Response example

```http
HTTP/1.1 201 Created
content-type: application/json
location: /streamer/9a4b2917-524a-4487-a2e2-3f13556fca94
```

```json
{
  "href": "/streamer/9a4b2917-524a-4487-a2e2-3f13556fca94",
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
link: </streamer>; rel="first", </streamer?_next=2021-12-03T12:34:18.166Z>; rel="next", </streamer?_prev=2021-12-03T12:34:18.166Z>; rel="prev"
```

```json
[
  {
    "href": "/streamer/9a4b2917-524a-4487-a2e2-3f13556fca94",
    "tag": "nginx-test-upstream",
    "url": "http://nginx-test-upstream.localhost"
  }
]
```

## /streamer/:streamer_id GET

Read a Streamer.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-read  

### Response parameters

| Name   | Type   | Description                    |
|--------|--------|--------------------------------|
| `href` | string | Href                           |
| `tag`  | string | tag                            |
| `url`  | string | plugin endpoint URL (absolute) |

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
  "href": "/streamer/9a4b2917-524a-4487-a2e2-3f13556fca94",
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
