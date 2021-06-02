---
title: "Requirements"
date: 2018-12-29T11:02:05+06:00
lastmod: 2020-01-05T10:42:26+06:00
weight: 1
draft: false
# search related keywords
keywords: ["db", "rabbitmq", "requirements", "installation", "cache"]
---
In order to operate, TeSLA CE needs a set of services ready to use:

* Database (MySQL, PostgreSQL)
* HashiCorp Vault
* RabbitMQ
* Redis
* MinIO

The configuration and credentials to access those services is required in order to perform the initial setup of the system

The initial setup process will prepare all the services in order to be used by TeSLA CE. In production scenarios
some of the services can be replaced by Amazon equivalents. In concrete:

* RDS database
* SQS instead of RabbitMQ
* S3 instead of MinIO
* Elastic Cache instead of Redis
* HashiCorp also provides a commercial version for Vault as a service

Is expected that all services are already available and ready to use for the installation.
If you want to deploy the services as part of the TeSLA CE system, see the Installing Services section.
To install TeSLA CE, follow those steps from any computer with access to the services:

Thanks to the simplicity of Hugo, this page is as empty as this theme needs requirements.

Just download latest version of [Hugo binary (> 0.53)](https://gohugo.io/getting-started/installing/) for your OS (Windows, Linux, Mac) : it's that simple.

![image example](hugo.jpg "image")
