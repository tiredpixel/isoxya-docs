# List (Pro)

Lists are lists of Pages within a [Site](Site.md). Lists can be used to start a List rather than Web [Crawl](Crawl.md). Lists are also created automatically when validating external links; these are subsequently used to create child [Crawls](Crawl.md). Pro edition only.

### Routes

- [/list/:list_id DELETE (Pro)](#listlist_id-delete-pro)
- [/list/:list_id GET (Pro)](#listlist_id-get-pro)
- [/site/:site_id/crawl/:site_v/list GET (Pro)](#sitesite_idcrawlsite_vlist-get-pro)
- [/site/:site_id/list GET (Pro)](#sitesite_idlist-get-pro)
- [/site/:site_id/list POST (Pro)](#sitesite_idlist-post-pro)


## /list/:list_id DELETE (Pro)

Delete a List. Pro edition only.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-delete  

### Response example

```http
HTTP/1.1 204 No Content
```


## /list/:list_id GET (Pro)

Read a List. Pro edition only.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/isoxya-api-read  

### Response parameters

| Name    | Type    | Description                                           |
|---------|---------|-------------------------------------------------------|
| `crawl` | object? | [Crawl](Crawl.md); set when validating external links |
| `href`  | string  | Href                                                  |
| `pages` | number  | total Pages contained in List                         |
| `site`  | object  | [Site](Site.md)                                       |

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
```

```json
{
  "crawl": null,
  "href": "/list/4a20e10b-58cf-4310-954a-77e9be03e1d9",
  "pages": 3,
  "site": {
    "channels": 1,
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
    "rate_lim": 1,
    "url": "http://example.com:80"
  }
}
```


## /site/:site_id/crawl/:site_v/list GET (Pro)

List a [Crawl's](Crawl.md) Lists. These are created automatically when validating external links. Pro edition only.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/pro/isoxya-api-list-crawl-list  

### Response parameters

Response parameters are as for [/list/:list_id GET](#listlist_id-get).

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
link: </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T16:16:55.511303Z/list>; rel="first", </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T16:16:55.511303Z/list?_next=2021-12-16T16:16:55.940975Z>; rel="next", </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T16:16:55.511303Z/list?_prev=2021-12-16T16:16:55.940975Z>; rel="prev"
```

```json
[
  {
    "crawl": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T16:16:55.511303Z",
    "href": "/list/57602e9c-2ffd-497c-a097-6e8eef3f92bb",
    "pages": 1,
    "site": {
      "channels": 1,
      "href": "/site/aHR0cHM6Ly93d3cuaWFuYS5vcmc6NDQz",
      "rate_lim": 1,
      "url": "https://www.iana.org:443"
    }
  }
]
```


## /site/:site_id/list GET (Pro)

List Lists. Pro edition only.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/pro/isoxya-api-list-list  

### Response parameters

Response parameters are as for [/list/:list_id GET](#listlist_id-get).

### Response example

```http
HTTP/1.1 200 OK
content-type: application/json
link: </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/list>; rel="first", </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/list?_next=2021-12-16T15:43:07.146331Z>; rel="next", </site/aHR0cDovL2V4YW1wbGUuY29tOjgw/list?_prev=2021-12-16T15:43:26.923Z>; rel="prev"
```

```json
[
  {
    "crawl": null,
    "href": "/list/4a20e10b-58cf-4310-954a-77e9be03e1d9",
    "pages": 3,
    "site": {
      "channels": 1,
      "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
      "rate_lim": 1,
      "url": "http://example.com:80"
    }
  }
]
```


## /site/:site_id/list POST (Pro)

Create a List. Pro edition only.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/pro/isoxya-api-create-list  

### Request parameters

No request parameters are supported.

### Response parameters

Response parameters are as for [/list/:list_id GET](#listlist_id-get).

### Request example

```http
POST /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/list HTTP/1.1
content-type: application/json
```

```json
{}
```

### Response example

```http
HTTP/1.1 201 Created
content-type: application/json
location: /list/4a20e10b-58cf-4310-954a-77e9be03e1d9
```

```json
{
  "crawl": null,
  "href": "/list/4a20e10b-58cf-4310-954a-77e9be03e1d9",
  "pages": 0,
  "site": {
    "channels": 1,
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
    "rate_lim": 1,
    "url": "http://example.com:80"
  }
}
```
