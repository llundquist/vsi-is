---

copyright:
  years: 2018
lastupdated: "2018-07-31"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:tip: .tip}

# Profiles
{: #profiles}

When you provision a virtual server instance, you can select from three families of profiles: Balanced, Compute, and Memory. A profile is a combination of vCPU and RAM that can be instantiated quickly to start up a virtual server instance. In the {{site.data.keyword.cloud}} Console, you can choose from popular profile configurations or select from a list of profiles that best fit your needs.
{: shortdesc}

The following families are available:

| Families | Description |
| -------- | ----------- |
| Balanced | Best for common cloud workloads that require a balance of performance and scalability. The balanced profiles (with network-attached storage) provide higher performance, since resources are not oversubscribed. |
| Compute  | Best for moderate to high web traffic workloads. Compute profiles are best for workloads with intensive CPU demands, such as high web traffic workloads, production batch processing, and front-end web servers. |
| Memory   | Best for memory caching and real-time analytics workloads. Memory profiles are best for memory intensive workloads, such as large caching workloads, intensive database applications, or in-memory analytics workloads. |
{: caption="Table 1. Virtual server family selections" caption-side="top"}

## Viewing profile configurations
{: #popularprofiles}

You can view available profile configurations using the {{site.data.keyword.cloud_notm}} Console or the CLI. In the {{site.data.keyword.cloud_notm}} Console, you can select from popular profile configurations that support most common use cases.

### Using the IBM Cloud Console
1. In the {{site.data.keyword.cloud_notm}} Console, navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > Infrastructure VPC (Beta) > Compute > Virtual server instances**.
2. From this page, click **New instance**.
3. You can either select a profile configuration from **Popular profiles** or click **All profiles** to view additional configurations. 

### Using the CLI
To view the list of available profiles using the CLI, run the following command:
```
$ ibmcloud is instance-profiles
```
{:codeblock}
