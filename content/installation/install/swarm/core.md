---
title: "Deploy TeSLA CE"
date: 2018-12-29T11:02:05+06:00
lastmod: 2020-01-05T10:42:26+06:00
weight: 6
draft: false
parent: _index.en.md
# search related keywords
keywords: ["install", "production", "docker", "self-hosted", "deployment"]
---

To generate all scripts to deploy the TeSLA CE core on your cluster, run:

{{< highlight bash >}}
tesla_ce deploy_core
{{< / highlight >}}

This command will create a folder **deploy** with:
- **config**: Folder with required configuration files
- **secrets**: Folder with required secret files
- **tesla_lb.yml**: Docker Stack file for the Load Balancer
- **tesla_core.yml**: Docker Stack file to deploy all TeSLA CE core modules
