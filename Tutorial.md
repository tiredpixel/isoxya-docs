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
  "now": "2021-12-07T12:20:45.350666784Z",
  "version": "2.1.6.39"
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
  "href": "/processor/cebc70e8-b303-433e-a9ac-aa98a8410e1c",
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
  "href": "/streamer/85bdb819-5c47-4068-9b37-4992311dff79",
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
processors.hrefs [/processor/cebc70e8-b303-433e-a9ac-aa98a8410e1c]: 
streamers.hrefs [/streamer/85bdb819-5c47-4068-9b37-4992311dff79]: 
```

```json
{
  "began": "2021-12-07T12:22:18.374602995Z",
  "ended": null,
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-07T12:22:18.374602995Z",
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

## Check crawl status

```sh
isoxya-api-read
```

```txt
href:
    0: /processor/cebc70e8-b303-433e-a9ac-aa98a8410e1c
    1: /streamer/85bdb819-5c47-4068-9b37-4992311dff79
    2: 
    3: /site/aHR0cDovL2V4YW1wbGUuY29tOjgw
    4: 
    5: /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-07T12:22:18.374602995Z
  [5]: 
  /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-07T12:22:18.374602995Z
```

```json
{
  "began": "2021-12-07T12:22:18.374602995Z",
  "ended": "2021-12-07T12:22:19.07Z",
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-07T12:22:18.374602995Z",
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

## Next

To crawl the same site again, use `isoxya-api-create-crawl`.

To crawl another site, register it with `isoxya-api-create-site` first.

That's it!
