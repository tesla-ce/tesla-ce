---
title: "Docker-Compose"
weight: 2
draft: false
# search related keywords
keywords: ["install", "test", "docker", "self-hosted", "deployment"]
---

For a fast deployment for testing purposes, TeSLA CE can be deployed using [docker-compose](https://docs.docker.com/compose/).
The provided scripts will deploy:
- All required services
- TeSLA CE system (APIs and workers)
- Moodle as VLE
- Face Recognition provider

### Requirements

Computer with:
- Docker
- docker-compose
- Internet access
- Git
- Valid domain name is recommended

### Getting started
1- Clone the repository
{{< highlight bash >}}
git clone https://github.com/tesla-ce/docker-compose-test-version.git
{{< / highlight >}}

2- Follow the instructions on the [README.md](https://github.com/tesla-ce/docker-compose-test-version/blob/main/README.md)
