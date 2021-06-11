---
title: "Getting Started"
weight: 2
draft: false
parent: _index.en.md
# search related keywords
keywords: ["install", "production", "docker", "self-hosted", "deployment"]
---

For the installation process, you will need a computer with Python 3 installed. It is highly recommended using a 
virtual environment.

{{< highlight bash >}}
python -m venv venv
source venv/bin/activate
pip install tesla-ce
{{< / highlight >}}

Alternatively, you can use a docker image to run the installation commands:

{{< highlight bash >}}
docker run -it -v "$PWD":/tesla teslace/core /bin/bash
source /venv/bin/activate
{{< / highlight >}}

In both cases, the **tesla_ce** command will be available. You can try:

{{< highlight bash >}}
tesla_ce tesla_version
{{< / highlight >}}

