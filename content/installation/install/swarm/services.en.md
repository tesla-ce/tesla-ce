---
title: "Deploy Services"
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

Some services need to be publicly accessible. You will need to create subdomains:
- vault.\<domain\>
- storage.\<domain\>
- rabbitmq.\<domain\>

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


## Deploy services

Before deploying, move **deploy** folder to a Docker Swarm master node and **move to this folder** of the node machine.

### Create networks

TeSLA CE will use two different networks, to create them run:

{{< highlight bash >}}
docker network create --driver overlay tesla_public
docker network create --driver overlay tesla_private
{{< / highlight >}}


### Create persistent data folders

To provide persistence of the data, all services will be provided with a mounted volume. 
All data folders are created under the folder provided in the **deployment_data_path** configuration option (see [Configuration](../configuration)). 
By default, this folder is ```/var/tesla```.

Traefik is used as a default load balancer and certificate management. We need to create a persistence folder for traefik:  
{{< highlight bash >}}
sudo mkdir -p /var/tesla/traefik
{{< / highlight >}}

In the same way, all services will have their own persistence folder. We need to create a folder for each service:
{{< highlight bash >}}
sudo mkdir -p /var/tesla/db
sudo mkdir -p /var/tesla/rabbitmq
sudo mkdir -p /var/tesla/redis
sudo mkdir -p /var/tesla/minio
{{< / highlight >}}

### Deploy services to Docker Swarm cluster

Finally, we are ready to deploy all services to the cluster. We need to start by deploying the load balancer:

{{< highlight bash >}}
docker stack deploy -c tesla_lb.yml tesla
{{< / highlight >}}

You can check the deployment progress with:

{{< highlight bash >}}
watch docker service ls
{{< / highlight >}}

Once Traefik service is up, we can deploy the rest of the services:

{{< highlight bash >}}
docker stack deploy -c tesla_services.yml tesla
{{< / highlight >}}

## Additional DNS entries

Some of the deployed services requires external access through the load balancer. You will need to define
the following subdomains pointing to the cluster:

* vault.\<domain\>
* storage.\<domain\>
* rabbitmq.\<domain\>

The rest of the services open their ports on the cluster, and are accessible directly on the cluster address pointed by 
\<domain\>.

### Working with not public domains

TeSLA CE assumes that provided \<domain\> is a valid domain configured in a public DNS. In the case you are using a not
valid domain, you should perform some extra actions:

1. Add entries for \<domain\> and subdomains on the installation computer local hosts ```/etc/hosts```:

{{< highlight bash >}}
192.168.1.X <domain>
192.168.X.Y vault.<domain>
192.168.X.Y storage.<domain>
192.168.X.Y rabbitmq.<domain>
{{< / highlight >}}

2. Add an extra hosts option to your services, so they can resolve the domain names:
{{< highlight yaml >}}
   extra_hosts:      
      192.168.1.X: <domain>
      192.168.X.Y: vault.<domain>
      192.168.X.Y: storage.<domain>
      192.168.X.Y: rabbitmq.<domain>
{{< / highlight >}}

3. As traefik will not be able to generate valid certificates, you will need to **disable the SSL check** options on the 
   configuration file.

