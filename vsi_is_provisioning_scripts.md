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

# User data
{: #user-data}

When you launch an instance, you can add user data that automatically performs common configuration tasks or runs scripts. In the **User Data** field on the order form, you can enter optional cloud-init user data for the server.
{:shortdesc}

The following is an example of how to add a new user and provide the user with an authorized SSH key. The **Name** field will have the public key added to `~/.ssh/authorized_keys`. You can paste these examples directly into the **User Data** field. The user data is then available to the virtual server instance during provisioning.

```
#cloud-config
users:
  - name: demouser
    gecos: Demo User
    sudo: ALL=(ALL) NOPASSWD:ALL
    groups: users, admin
    ssh_import_id: None
    lock_passwd: true
    ssh_authorized_keys:
        - <ssh public key>
```
{:codeblock}

The following shell script is an example of how to add an SSH key to the current user.

```
#!/bin/bash
echo <sshKey> > ~/.ssh/authorized_keys
```
{:codeblock}
