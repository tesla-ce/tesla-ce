---
title: "Requirements"
date: 2018-12-29T11:02:05+06:00
lastmod: 2020-01-05T10:42:26+06:00
weight: 1
draft: false
parent: _index.en.md
# search related keywords
keywords: ["install", "production", "docker", "self-hosted", "deployment"]
---

In order to work, TeSLA CE needs a set of services ready to use:

**Services**:
- Database (MySQL, PostgreSQL)
- HashiCorp Vault
- RabbitMQ
- Redis
- MinIO
  
**and**:
- A valid DNS domain name pointing to the Docker Swarm cluster
- Access from the installation computer to all services
- Access from the cluster to all services
- Permission to deploy services on the Docker Swarm cluster

Although for production deployments it is recommended to use customized instances of the services, it is
possible to deploy such services as part of the TeSLA CE deployment.
