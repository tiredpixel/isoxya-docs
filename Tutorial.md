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
  "time": "2021-12-16T14:19:34.138417603Z",
  "version": "2.1.6.49"
}
```


## Register [Processor](Endpoints/Processor.md) plugin

```sh
isoxya-api-create-processor
```

```txt
channels (Pro) [null]: 
tag [crawler-html]: 
url [http://isoxya-plugin-crawler-html.localhost/data]: 
```

```json
{
  "channels": 1,
  "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73",
  "tag": "crawler-html",
  "url": "http://isoxya-plugin-crawler-html.localhost/data"
}
```


## Register [Streamer](Endpoints/Streamer.md) plugin

```sh
isoxya-api-create-streamer
```

```txt
channels (Pro) [null]: 
tag [nginx]: 
url [http://isoxya-plugin-nginx.localhost]: 
```

```json
{
  "channels": 1,
  "href": "/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac",
  "tag": "nginx",
  "url": "http://isoxya-plugin-nginx.localhost"
}
```


## Register [Site](Endpoints/Site.md)

```sh
isoxya-api-create-site
```

```txt
channels (Pro) [null]: 
rate_lim (Pro) [null]: 
url [http://example.com]: 
```

```json
{
  "channels": 1,
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
  "rate_lim": 1,
  "url": "http://example.com:80"
}
```


## Start [Crawl](Endpoints/Crawl.md)

```sh
isoxya-api-create-crawl
```

```txt
site.href [/site/aHR0cDovL2V4YW1wbGUuY29tOjgw]: 
agent (Pro) [null]: 
depth_max (Pro) [null]: 
list.href (Pro):
    0: null
    1: 
  [0]: 
  null
pages_max (Pro) [null]: 
processor_config [null]: 
processors.hrefs [/processor/7135e6c2-3026-44bf-abcc-c64af3efce73]: 
streamers.hrefs [/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac]: 
validate (Pro) [null]: 
```

```json
{
  "agent": null,
  "began": "2021-12-16T14:21:41.719297Z",
  "depth_max": null,
  "ended": null,
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T14:21:41.719297Z",
  "list": null,
  "pages": null,
  "pages_max": null,
  "parent": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73"
    }
  ],
  "progress": null,
  "site": {
    "channels": 1,
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
    "rate_lim": 1,
    "url": "http://example.com:80"
  },
  "status": "pending",
  "streamers": [
    {
      "href": "/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac"
    }
  ],
  "validate": false
}
```


## Check [Crawl](Endpoints/Crawl.md) status

```sh
isoxya-api-read
```

```txt
href:
    0: /processor/7135e6c2-3026-44bf-abcc-c64af3efce73
    1: /streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac
    2: /site/aHR0cDovL2V4YW1wbGUuY29tOjgw
    3: 
    4: /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T14:21:41.719297Z
  [4]: 
  /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T14:21:41.719297Z
```

```json
{
  "agent": null,
  "began": "2021-12-16T14:21:41.719297Z",
  "depth_max": null,
  "ended": "2021-12-16T14:23:28.937469Z",
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-16T14:21:41.719297Z",
  "list": null,
  "pages": 1,
  "pages_max": null,
  "parent": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/7135e6c2-3026-44bf-abcc-c64af3efce73"
    }
  ],
  "progress": 100,
  "site": {
    "channels": 1,
    "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw",
    "rate_lim": 1,
    "url": "http://example.com:80"
  },
  "status": "completed",
  "streamers": [
    {
      "href": "/streamer/b49fcc24-6562-415a-94a6-3e8dcd848aac"
    }
  ],
  "validate": false
}
```


## Next

To crawl the same [Site](Endpoints/Site.md) again, use `isoxya-api-create-crawl`.

To crawl another [Site](Endpoints/Site.md), register it with `isoxya-api-create-site` first.

That's it!
