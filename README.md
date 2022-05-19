# Isoxya Docs

Documentation for [Isoxya](https://www.isoxya.com/) web crawler.


## Isoxya

Isoxya is an extensible data processing system for crawling and scraping the internet. It is written in a compiled, statically typed language for speed and reliability. Isoxya is free, open-source, and packaged as a container. The API can be used by CLI scripts or called by another project. Various plugins are available, many also open-source.

https://www.isoxya.com/  
https://hub.docker.com/r/isoxya/isoxya-api  
https://github.com/tiredpixel/isoxya-api  


## Isoxya Pro

Isoxya Pro adds high availability, error recovery, and horizontal scaling. It is available on-premises for installation on your servers, or in the cloud via SaaS subscription. Isoxya Pro is available via commercial licence. The API is able to scale crawlers, processors, and streamers. Support or custom development is available from Isoxya's creator.

https://www.isoxya.com/pro/  


## Tutorial

To get started, follow the [tutorial](Tutorial.md).


## Routes

- [/ GET](Endpoints/Apex.md#-get)
- [/list/:list_id DELETE (Pro)](Endpoints/List.md#listlist_id-delete-pro)
- [/list/:list_id GET (Pro)](Endpoints/List.md#listlist_id-get-pro)
- [/list/:list_id/list_page POST (Pro)](Endpoints/ListPage.md#listlist_idlist_page-post-pro)
- [/processor GET](Endpoints/Processor.md#processor-get)
- [/processor POST](Endpoints/Processor.md#processor-post)
- [/processor/:processor_id DELETE](Endpoints/Processor.md#processorprocessor_id-delete)
- [/processor/:processor_id GET](Endpoints/Processor.md#processorprocessor_id-get)
- [/site POST](Endpoints/Site.md#site-post)
- [/site/:site_id GET](Endpoints/Site.md#sitesite_id-get)
- [/site/:site_id/crawl GET](Endpoints/Crawl.md#sitesite_idcrawl-get)
- [/site/:site_id/crawl POST](Endpoints/Crawl.md#sitesite_idcrawl-post)
- [/site/:site_id/crawl/:site_v GET](Endpoints/Crawl.md#sitesite_idcrawlsite_v-get)
- [/site/:site_id/crawl/:site_v PATCH (Pro)](Endpoints/Crawl.md#sitesite_idcrawlsite_v-patch-pro)
- [/site/:site_id/crawl/:site_v/crawl GET (Pro)](Endpoints/Crawl.md#sitesite_idcrawlsite_vcrawl-get-pro)
- [/site/:site_id/crawl/:site_v/list GET (Pro)](Endpoints/List.md#sitesite_idcrawlsite_vlist-get-pro)
- [/site/:site_id/list GET (Pro)](Endpoints/List.md#sitesite_idlist-get-pro)
- [/site/:site_id/list POST (Pro)](Endpoints/List.md#sitesite_idlist-post-pro)
- [/streamer GET](Endpoints/Streamer.md#streamer-get)
- [/streamer POST](Endpoints/Streamer.md#streamer-post)
- [/streamer/:streamer_id DELETE](Endpoints/Streamer.md#streamerstreamer_id-delete)
- [/streamer/:streamer_id GET](Endpoints/Streamer.md#streamerstreamer_id-get)


## Licence

Copyright © [Nic Williams](https://www.tiredpixel.com/). It is free software, released under the BSD 3-Clause licence, and may be redistributed under the terms specified in `LICENSE`.
