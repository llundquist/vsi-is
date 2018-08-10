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

# Connecting to your instance using Linux
To connect to your instance, complete the following steps:

## Before you begin
Locate your floating IP address for the instance to which you want to connect. To view the instance details, run the following command.

   ```
   $ ibmcloud is instance INSTANCE_ID
   ```
   {:codeblock}
   
Optionally, ping your instance to ensure it's running!
{:tip}

## Getting connected

The values returned below are for example purposes only.

1. To connect to your instance, use your private key and run the following command:

   ```
   $ ssh -i <path to your private key file> root@<floating ip address>
   ```
   {:codeblock}

   You receive a response similar to the following example. When prompted to continue connecting, type `yes`.
   ```
   The authenticity of host 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' can't be established.
   ECDSA key fingerprint is SHA256:abcdef1Gh/aBCd1EFG1H8iJkLMnOP21qr1s/8a3a8aa.
   Are you sure you want to continue connecting (yes/no)? yes
   Warning: Permanently added 'xxx.xxx.xxx.xxx' (ECDSA) to the list of known hosts.
   ```
   {:screen}

   You are now accessing your server.

2. When you are ready to end your connection, run the following command:

   ```
   # exit
   ```
   {:codeblock}

## What happens next
After you are connected to your instance, you can [manage your instances using the {{site.data.keyword.cloud_notm}} console](vsi_is_manage_instances.html) or [manage your instances using the CLI](vsi_is_manage_instances_cli.html).
