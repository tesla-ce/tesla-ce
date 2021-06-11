---
title: "Deploy TeSLA CE"
weight: 6
draft: false
parent: _index.en.md
# search related keywords
keywords: ["install", "production", "docker", "self-hosted", "deployment"]
---

{{% notice tip %}}
If you have deployed the services as part of the TeSLA CE deployment process, you should **skip 
the network creation and load balancer deployment**. 
{{% /notice %}}

## Generate deployment scripts
To generate all scripts to deploy the TeSLA CE core on your cluster, run:

{{< highlight bash >}}
tesla_ce deploy_core
{{< / highlight >}}

This command will create a folder **deploy** with:
- **config**: Folder with required configuration files
- **secrets**: Folder with required secret files
- **tesla_lb.yml**: Docker Stack file for the Load Balancer
- **tesla_core.yml**: Docker Stack file to deploy all TeSLA CE core modules

## Deploy TeSLA CE core services

Before deploying, move **deploy** folder to a Docker Swarm master node and **move to this folder** of the node machine.

### Create networks

TeSLA CE will use two different networks, to create them run:

{{< highlight bash >}}
docker network create --driver overlay tesla_public
docker network create --driver overlay tesla_private
{{< / highlight >}}


### Deploy the load balancer

Traefik is used as a default load balancer and certificate management. We need to create a persistence folder for traefik.
All data folders are expected under the folder provided in the **deployment_data_path** configuration option (see [Configuration](../configuration)). 
By default, this folder is ```/var/tesla```.

{{< highlight bash >}}
sudo mkdir -p /var/tesla/traefik
{{< / highlight >}}

Now we are ready to deploy the load balancer service:

{{< highlight bash >}}
docker stack deploy -c tesla_lb.yml tesla
{{< / highlight >}}

You can check the deployment progress with:

{{< highlight bash >}}
watch docker service ls
{{< / highlight >}}

### Deploy services to Docker Swarm cluster

Once Traefik service is up, we can deploy the rest of the services:

{{< highlight bash >}}
docker stack deploy -c tesla_core.yml tesla
{{< / highlight >}}
