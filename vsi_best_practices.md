---

copyright:
  years: 2018
lastupdated: "2018-06-01"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}

# Planning for instances

When you are planning to provision {{site.data.keyword.BluVirtServers}} instances, you might find this configuration checklist helpful to get the most out of your virtual server deployment.
{:shortdesc}

Currently, in the IBM Cloud Virtual Private Cloud (VPC), you cannot create an instance before you create a VPC.  If you do not have a virtual private cloud created, see [Getting started with IBM Cloud Virtual Private Cloud (VPC)](/docs/infrastructure/vpc/getting-started.html) first.
{:tip}

After you have a VPC available, consider the following before you provision your instance.

|        Considerations|
|-------------------|
|__ 1. Does your account have the required [user permissions](/docs/infrastructure/vpc/vpc-user-permissions.html)?|
|__ 2. Do you know your account limits for concurrent instances? |
|__3. Do you have your [SSH key](vsi_is_ssh_keys_about.html) available?
|__ 4. Do you know what instance location to select and why?|
|__ 5. Have you considered the popular profile options or does your workload require additional vCPU and RAM combinations? Profiles contain preconfigured instances that are ready to use in a matter of minutes. It's important to ensure your instances will have the necessary resources to keep your workloads and your environment up and running.|
|__ 6. What image are you selecting? You can choose among the current stock [images](vsi_is_images.html). |
|__ 7. What are the port speeds you need? You have two port speed options: 100 Mbps, or 1000 Mbps. This option cannot be modified after you create the instance.  Choose a network interface with the speed that best balances cost versus performance for your design. |
|__ 8. Have you selected a unique name for the instance? If you have a method to naming virtual server instances, it is much easier to filter and search on them later. |

**We'd like your input!** When it comes to compute resources, we often hear requests for better tips on capacity considerations, account limitations, or permissions... what other tips or best practice areas are you curious about? what do you think would help?  We would love to hear from you. Please click **Edit in Github** on this page to open a pull request or create an issue with your thoughts and ideas. Thank you!

## What's next?
When you're ready to get started, see the following resources to create your instance:
* [Creating an instance using the {{site.data.keyword.cloud_notm}} console](vsi_is_create_instance.html)
* [Creating an instance using the CLI](vsi_is_create_instance_cli.html)
