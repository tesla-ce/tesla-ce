---
title: "Deploy Services"
date: 2018-12-29T11:02:05+06:00
lastmod: 2020-01-05T10:42:26+06:00
weight: 4
draft: false
parent: _index.en.md
# search related keywords
keywords: ["install", "production", "docker", "self-hosted", "deployment"]
---

{{% notice warning%}}
Deploy services as part of TeSLA CE installation is not recommended for production. 
Skip this step if you already have your services deployed.
{{% /notice %}}

## Requirements

The storage needs to be publicly accessible. You will need to create a subdomain:
- storage.<domain>

that points to your Docker Swarm cluster.

## Generate deployment scripts

To generate all scripts to deploy services on your cluster, run:

{{< highlight bash >}}
tesla_ce deploy_services
{{< / highlight >}}

This command will create a folder **deploy** with:
- **config**: Folder with required configuration files
- **secrets**: Folder with required secret files
- **tesla_lb.yml**: Docker Stack file for the Load Balancer
- **tesla_services.yml**: Docker Stack file to deploy all services


