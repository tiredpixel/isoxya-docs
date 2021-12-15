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
  "time": "2021-12-15T14:35:19.139808249Z",
  "version": "2.1.6.41"
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
  "href": "/processor/e94e9103-0b92-4248-8ad3-c56e9f974d41",
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
  "href": "/streamer/e91056f9-55e2-43e4-9ace-3f2c8db5858c",
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
processor_config [null]: 
processors.hrefs [/processor/e94e9103-0b92-4248-8ad3-c56e9f974d41]: 
streamers.hrefs [/streamer/e91056f9-55e2-43e4-9ace-3f2c8db5858c]: 
```

```json
{
  "agent": null,
  "began": "2021-12-15T14:37:24.827475Z",
  "depth_max": null,
  "ended": null,
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-15T14:37:24.827475Z",
  "list": null,
  "pages": null,
  "pages_max": null,
  "parent_href": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/e94e9103-0b92-4248-8ad3-c56e9f974d41"
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
      "href": "/streamer/e91056f9-55e2-43e4-9ace-3f2c8db5858c"
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
    0: /processor/e94e9103-0b92-4248-8ad3-c56e9f974d41
    1: /streamer/e91056f9-55e2-43e4-9ace-3f2c8db5858c
    2: /site/aHR0cDovL2V4YW1wbGUuY29tOjgw
    3: 
    4: /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-15T14:37:24.827475Z
  [4]:
  /site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-15T14:37:24.827475Z
```

```json
{
  "agent": null,
  "began": "2021-12-15T14:37:24.827475Z",
  "depth_max": null,
  "ended": "2021-12-15T14:38:52.366202Z",
  "href": "/site/aHR0cDovL2V4YW1wbGUuY29tOjgw/crawl/2021-12-15T14:37:24.827475Z",
  "list": null,
  "pages": 1,
  "pages_max": null,
  "parent_href": null,
  "processor_config": null,
  "processors": [
    {
      "href": "/processor/e94e9103-0b92-4248-8ad3-c56e9f974d41"
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
      "href": "/streamer/e91056f9-55e2-43e4-9ace-3f2c8db5858c"
    }
  ],
  "validate": false
}
```


## Next

To crawl the same [Site](Endpoints/Site.md) again, use `isoxya-api-create-crawl`.

To crawl another [Site](Endpoints/Site.md), register it with `isoxya-api-create-site` first.

That's it!
