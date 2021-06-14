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

## Database

The database must exist before trying to configure TeSLA CE. If root credentials are provided, this process
will create the not privileged user, otherwise, the not privileged should have owner permissions in the TeSLA database.

## Storage Buckets

If you are using MinIO, the configuration process will create and initialize the buckets if they do not exist. If using 
another storage like Amazon S3 or the provided credentials cannot create buckets, they may exist before trying to run the
configuration script. 

If the buckets are created by the configuration script, at the end of the configuration process you need to set
the correct policy to the public bucket. This can be done with the MinIO client following those steps:

1. Get the configuration parameters **STORAGE_URL**, **BUCKET_NAME**, **STORAGE_KEY** and **STORAGE_SECRET** from the configuration 
   file ```tesla-ce.cfg``` generated previously (see [Configuration](../configuration)). 

{{< highlight cfg >}}
# Storage configuration (S3 or Minio)
[storage]
# Storage url
# (str) default: http://localhost:9000
url=STORAGE_URL
# Storage default public bucket
# (str) default: tesla-public
public_bucket_name=BUCKET_NAME
...
# Storage access key id
# (str)
access_key=STORAGE_KEY
# Storage secret access key
# (str)
secret_key=STORAGE_SECRET
{{< / highlight >}}

2. Run a MinIO client
{{< highlight bash >}}
docker run -it --entrypoint=/bin/bash minio/mc
{{< / highlight >}}

3. Setup the MinIO connection. If you are not using a real domain, use ```--insecure``` option to avoid certificate errors.
{{< highlight bash >}}
mc alias set minio STORAGE_URL STORAGE_KEY STORAGE_SECRET [--insecure]
{{< / highlight >}}

3. Change the policy for the public bucket. If you are not using a real domain, use ```--insecure``` option to avoid certificate errors.
{{< highlight bash >}}
mc policy set download minio/BUCKET_NAME [--insecure]
{{< / highlight >}}

## Initialize TeSLA CE

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
