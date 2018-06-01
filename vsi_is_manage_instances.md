---



copyright:
  years: 2018
lastupdated: "2018-06-01"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Managing virtual server instances
{: #managing-virtual-server-instances}

You can view and manage your instances from the *Virtual server instances* page in {{site.data.keyword.cloud}} console.
{:shortdesc}

To manage your instances, complete the following steps.
1. In {{site.data.keyword.cloud_notm}} console, navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > Infrastructure VPC (Beta) > Compute > Virtual server instances**.
2. From this page, you can perform management tasks for a specific instance, or click an instance to view and edit its properties.

The following management tasks are available to you:

|              Instance actions          |  Description              |  What happens next           |
| ---------------------------------------| --------------------------|----------------------------- |
| Restart          |Immediately power off an instance and then power it back on again.   |     |
| Stop/Start          | Remotely turn an instance on or off.  | If the device has been stopped, the device remains in the stopped state and must be manually started. You cannot interact with an instance if it is stopped. If the device is started, normal interaction continues.    |
| Rename          | Change or update an instance name.  | After renaming the device, the name is automatically updated. When performing a search, use the new instance name when attempting to locate content associated with it.    |
| Delete         | Permanently remove an instance and its connected vNIC, boot volume, and data from your account.  | After confirming the delete action, the process to delete the instance and its associated vNIC, boot volume, and data begins. The delete action can take several minutes, but when the process is complete, the instance no longer appears on the Virtual server instances page. The floating IP address that is associated to the virtual server instance is unassociated, but remains on your account.    |
{: caption="Table 1. Required instance details" caption-side="top"}

You can interact with instances by viewing the summary of all instances on the *Virtual server instances* page, or by clicking an individual instance to view details and make changes.

Do you prefer to manage your instances using the CLI? For more information, see [Managing an instance using the CLI](vsi_is_manage_instances_cli.html).
{: tip}
