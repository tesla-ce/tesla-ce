---
title: "Initialize"
weight: 5
draft: false
parent: _index.en.md
# search related keywords
keywords: ["install", "production", "docker", "self-hosted", "deployment"]
---

{{% notice warning%}}
Double check that all **required services** are running and accessible before trying this step.
{{% /notice %}}

Once the configuration options are set on the configuration file, in this step we will prepare all 
the services to be used. First check that configuration is valid:

{{< highlight bash >}}
tesla_ce reconfigure --check
{{< / highlight >}}

And finally apply the configuration:

{{< highlight bash >}}
tesla_ce reconfigure
{{< / highlight >}}

This command will initialize all the services to be ready for TeSLA CE deployment.

{{% notice tip %}}
Depending on the services and connection performance, some actions can take longer than default HTTP timeout. 
If this happens, the command will fail. Just run this command again to finish the configuration process. 
{{% /notice %}}
