---
title: Requirements
date: 2018-12-29T11:02:05.000+06:00
lastmod: 2020-01-05T10:42:26.000+06:00
weight: "1"
keywords:
- db
- rabbitmq
- requirements
- installation
- cache

---
## Domain

Due to the use of personal data, TeSLA CE will use encrypted communications. As part of the deployment, [Traefik ](https://traefik.io/)proxy and load-balancer will be deployed by default, which will manage the certificates using [LetsEncrypt](https://letsencrypt.org/). 

In order to deploy TeSLA CE, you will require to have a valid domain name pointing to the 

## Services

### Self-Hosted

In order to operate, TeSLA CE needs a set of services ready to use:

* Database ([MySQL](https://www.mysql.com/)/[MariaDB](https://mariadb.org/), [PostgreSQL](https://www.postgresql.org/))
* [HashiCorp Vault](https://www.vaultproject.io/)
* [RabbitMQ](https://www.rabbitmq.com/)
* [Redis](https://redis.io/)
* [MinIO](https://min.io/)

The configuration and credentials to access those services is required in order to perform the initial setup of the system

The initial setup process will prepare all the services in order to be used by TeSLA CE. 

### Production

In production scenarios some of the services can be replaced by SAAS equivalents:

* RDS database
* SQS instead of RabbitMQ
* S3 instead of MinIO
* Elastic Cache instead of Redis
* HashiCorp also provides a commercial version for Vault as a service

Is expected that **all services are already available and ready to use** for the installation.