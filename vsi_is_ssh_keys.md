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
{:table: .aria-labeledby="caption"}

# Managing SSH keys
{: #managing-ssh-keys}

## Managing SSH keys with IBM Cloud console

When you provision a virtual server, you can select from available SSH keys or upload a new one. You cannot generate SSH keys.
{:shortdesc}

You can manage and delete SSH keys by using the {{site.data.keyword.cloud}} console.
1. In {{site.data.keyword.cloud_notm}} console, navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > Infrastructure VPC (Beta) > Compute > SSH keys**.
2. From this page, you can edit and delete SSH keys, or add a new SSH Key.

## Managing SSH keys using the CLI

You can also manage your SSH keys by using the CLI.

| Action           | Command                     | What happens next |
| ---------------- | --------------------------- | ----------------- |
| Create SSH key   | `ibmcloud is key-create`    | After you create an SSH key, it is added to the list of keys. |
| View key details | `ibmcloud is key`           | You can view the name of the key and the ID of the key. |
| List keys        | `ibmcloud is keys`          | You can view all of your existing SSH keys. |
| Update key       | `ibmcloud is key-update`    | After you update an existing key, the key is renamed immediately. |
| Delete key       | `ibmcloud is key-delete`    | After you remove an SSH key, it no longer exists. The key can no longer be used when you provision a new device or when you perform an OS reload on an existing device. Once you delete a key, you can also no longer access existing provisions by using that key. |
{: caption="Table 1. SSH key actions" caption-side="top"}
