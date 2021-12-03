# Tutorial

## Initialise state directory

```sh
isoxya-api-init
```

```txt
endpoint [http://localhost]: 
```

```json
{
  "now": "2021-12-02T13:35:22.149003003Z",
  "version": "0.0.0"
}
```

## Register processor plugin

```sh
isoxya-api-create-processor
```

```txt
url [http://isoxya-plugin-crawler-html.localhost/data]: 
tag [crawler-html]: 
```

```json
{
  "href": "/processor/17f17cef-6eb3-4bf4-bbf0-a3d729b3d650",
  "tag": "crawler-html",
  "url": "http://isoxya-plugin-crawler-html.localhost/data"
}
```

## Register streamer plugin

```sh
isoxya-api-create-streamer
```

```txt
url [http://nginx-test-upstream.localhost]: 
tag [nginx-test-upstream]: 
```

```json
{
  "href": "/streamer/68e526ee-dd89-4a0e-932f-bf23825fabd0",
  "tag": "nginx-test-upstream",
  "url": "http://nginx-test-upstream.localhost"
}
```

## Register site

```sh
isoxya-api-create-site
```

```txt
url [http://example.com]: 
```

```json
{
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
  "url": "http://example.com:80"
}
```

## Start crawl

```sh
isoxya-api-create-crawl
```

```txt
site.href [/site/aHR0cDovL2V4YW1wbGUuY29tOjgw]: 
processor_config [null]: 
processors.hrefs [/processor/17f17cef-6eb3-4bf4-bbf0-a3d729b3d650]: 
streamers.hrefs [/streamer/68e526ee-dd89-4a0e-932f-bf23825fabd0]: 
```

```json
{
  "began": "2021-12-02T13:37:02.063613916Z",
  "ended": null,
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-02T13:37:02.063613916Z",
  "pages": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/17f17cef-6eb3-4bf4-bbf0-a3d729b3d650"
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
      "href": "/streamer/68e526ee-dd89-4a0e-932f-bf23825fabd0"
    }
  ]
}
```

## Check crawl status

```sh
isoxya-api-read
```

```txt
href:
    0: /processor/17f17cef-6eb3-4bf4-bbf0-a3d729b3d650
    1: /streamer/68e526ee-dd89-4a0e-932f-bf23825fabd0
    2: 
    3: /site/aHR0cDovL2V4YW1wbGUuY29tOjgw
    4: 
    5: /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-02T13:37:02.063613916Z
  [5]: 
  /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-02T13:37:02.063613916Z
```

```json
{
  "began": "2021-12-02T13:37:02.063613916Z",
  "ended": "2021-12-02T13:37:02.596Z",
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-02T13:37:02.063613916Z",
  "pages": 1,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/17f17cef-6eb3-4bf4-bbf0-a3d729b3d650"
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
      "href": "/streamer/68e526ee-dd89-4a0e-932f-bf23825fabd0"
    }
  ]
}
```

## Next

To crawl the same site again, use `isoxya-api-create-crawl`.

To crawl another site, register it with `isoxya-api-create-site` first.

That's it!
