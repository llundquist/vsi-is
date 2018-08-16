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


# Images

When you provision a virtual server instance, you can select from the supported stock images. Custom images are not supported
currently.
{:shortdesc}

## Stock images
The following operating systems are available as stock images when you create a virtual server.
* CentOS 7.x
* Ubuntu 16.04 LTS

When you order an instance, the images are cloud-init enabled to optimize provisioning times. With a cloud-init enabled image, you can provide user data. In the **User Data** field on the order form, you can enter optional cloud-init user data for the server. For more information about user data and automation, see [User Data](vsi_is_provisioning_scripts.html).

## Virtualization
Instances require an image that supports Hardware Virtualization Machine (HVM) boot mode. The HVM virtualization type allows an image to run directly on a virtual server, which is required for advanced networking and GPU capabilities.
