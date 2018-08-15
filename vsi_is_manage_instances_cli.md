---



copyright:
  years: 2018
lastupdated: "2018-08-15"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Managing virtual server instances (CLI)
{: #managing-virtual-servers-cli}

You can view and manage your instances using the command line interface (CLI).
{:shortdesc}

## Before you begin
Ensure you have downloaded, installed, and initialized the following CLI plug-ins:

* {{site.data.keyword.cloud_notm}} CLI
* {{site.data.keyword.cloud_notm}} Regional API CLI

For more information, see [CLI access](/docs/infrastructure/vpc/how-to-verify-access.html).

## Viewing instance actions
To view the management actions performed on your instance, run the following command:

```
ibmcloud is instance-actions <instance-ID>
```
{:codeblock}

You will see a list similar to the following output:

```
ID                                     Type     Status      Created       Started            Completed   
123xxxx4-123x-1234-56x7-80xx37xx1234   delete   Completed   6 hours ago   a long while ago   a long while ago         
```
{:screen}

## Managing your instances
Need a little help? Run the `ibmcloud is help` command to view commands at anytime.

Common management actions

|              Instance action          |  Command              |  What happens next           |
| ---------------------------------------| --------------------------|----------------------------- |
| Restart          |`ibmcloud is instance-reboot`   |     |
| Stop/Start          | `ibmcloud is instance-start` or `ibmcloud is instance-stop`  | If the device has been stopped, the device remains in the stopped state and must be manually started. You cannot interact with an instance if it is stopped. If the device is started, normal interaction continues.    |
| Update          | `ibmcloud is instance-update`  | After renaming the device, the name is automatically updated. When performing a search, use the new instance name when attempting to locate content associated with it.    |
| Delete         | `ibmcloud is instance-delete` | After confirming the delete action, the process to delete the instance and its associated vNIC, boot volume, and data begins. The delete action can take several minutes, but when the process is complete, the instance no longer appears on the Virtual server instances page. The floating IP address that is associated to the virtual server instance is unassociated, but remains on your account.    |
{: caption="Table 1. Management actions for your instances" caption-side="top"}

Do you prefer to manage instances using the {{site.data.keyword.cloud}} console? For more information, see [Managing an instance](vsi_is_manage_instances.html).
{: tip}
