# Streamer

Streamers are plugins which send extracted data elsewhere. Streamers must be registered within the system, making them available to [Crawls](Crawl.md).

### Routes

- [/streamer GET](#streamer-get)
- [/streamer POST](#streamer-post)
- [/streamer/:streamer_id DELETE](#streamerstreamer_id-delete)
- [/streamer/:streamer_id GET](#streamerstreamer_id-get)


## /streamer GET

List Streamers.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-list-streamer  

### Response parameters

Response parameters are as for [/streamer/:streamer_id GET](#streamerstreamer_id-get).

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
link: </streamer>; rel="first", </streamer?_next=2021-12-16T14:20:42.418362Z>; rel="next", </streamer?_prev=2021-12-16T14:20:42.418362Z>; rel="prev"
```

```json
[
  {
    "channels": 1,
    "href": "/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac",
    "tag": "nginx",
    "url": "http://isoxya-plugin-nginx.localhost"
  }
]
```


## /streamer POST

Create a Streamer.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-create-streamer  

### Request parameters

| Name       | Edition | Type    | Description                          |
|------------|---------|---------|--------------------------------------|
| `channels` | Pro     | number? | channels, used for scaling Streamers |
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
  "tag": "nginx",
  "url": "http://isoxya-plugin-nginx.localhost"
}
```

### Response example

```http
HTTP/1.1 201 Created
content-type: application/json
location: /streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac
```

```json
{
  "channels": 1,
  "href": "/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac",
  "tag": "nginx",
  "url": "http://isoxya-plugin-nginx.localhost"
}
```


## /streamer/:streamer_id DELETE

Delete a Streamer.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-delete  

### Response example

```http
HTTP/1.1 204 No Content
```


## /streamer/:streamer_id GET

Read a Streamer.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-read  

### Response parameters

| Name       | Edition | Type   | Description                          |
|------------|---------|--------|--------------------------------------|
| `channels` | Pro     | number | channels, used for scaling Streamers |
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
  "href": "/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac",
  "tag": "nginx",
  "url": "http://isoxya-plugin-nginx.localhost"
}
```
