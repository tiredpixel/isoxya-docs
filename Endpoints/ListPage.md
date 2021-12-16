# ListPage (Pro)

ListPages are Pages within a [List](List.md), within a [Site](Site.md). Using this, it's possible to insert Pages into a [List](List.md). It's not possible to read them afterwards, however—only the total number of Pages in a [List](List.md). Pro edition only.


## /list/:list_id/list_page POST (Pro)

Insert one or more Pages into a [List](List.md). `urls` are normalised and deduplicated, after which any not matching the [List's](List.md) [Site](Site.md) are discarded. Pro edition only.

https://github.com/isoxya/isoxya-api/blob/unstable/bin/pro/isoxya-api-create-list  

### Request parameters

| Name   | Type         | Description                      |
|--------|--------------|----------------------------------|
| `urls` | array.string | Page URLs (relative or absolute) |

### Request example

```http
POST /list/79b35953-ed12-45f0-ae09-491835731ad7/list_page HTTP/1.1
content-type: application/json
```

```json
{
  "urls": [
    "a",
    "b",
    "c",
    "http://example.com:80/b",
    "/b",
    "http://example.com:666"
  ]
}
```

This will result in inserting only 3 Pages, since:

- `http://example.com:80/b` normalises to the same as `b`
- `/b` normalises to the same as `b`
- `http://example.com:666` is a different [Site](Site.md) and thus discarded

### Response example

```http
HTTP/1.1 204 No Content
```
