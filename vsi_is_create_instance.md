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

# Creating virtual server instances
{: #creating-virtual-servers}

You can create instances from the *Virtual server instances* page in {{site.data.keyword.cloud}} console.
{:shortdesc}

To create an instance, select the following instance details.
1. In {{site.data.keyword.cloud_notm}} console, navigate to **Menu icon ![Menu icon](../icons/icon_hamburger.svg) > Infrastructure VPC (Beta) > Compute > Virtual server instances**.
2. From this page, click **New instance** and enter the following information:

    <table>
    <CAPTION>Table 1. Instance provisioning selections</CAPTION>
    <THEAD>
    <TR>
    <th>Field</th>
    <th>Value</th>
    </TR>
    </THEAD>
    <TBODY>
    <tr>
    <td>Name </td>
    <td>A name is required for your virtual server instance.</td>
    </tr>
    <tr>
    <td>Virtual private cloud</td>
    <td>Specify the virtual private cloud that is required for your design.</td>
    </tr>
    <tr>
    <td>Location</td>
    <td>Select the specific location that is required for your design. Locations are composed of regions: each region is a separate geographic area.</td>
    </tr>
    <tr>
    <td>Profile</td>
    <td><p>
    Select from popular profiles or all available vCPU and RAM combinations. The following families are supported:
    <ul>
    <li>Balanced</li>
    <li>Compute</li>
    <li>Memory</li>
    </ul>
    </p>
    <p>Each physical core on the server is hyper-threaded and presented as two virtual CPUs (vCPUs). The virtual server offering provides 2.0GHz or better per vCPU with up to 48 vCPU available on a single virtual server.</p>

    <p>RAM is extremely straight-forward. The offering fully dedicates the amount of RAM that you select to your instance, with up to 256 GB on a single instance.</p>
    <note>Note: Maximum values vary by family.</note>
    </td>
    </tr>
    <tr>
    <td>Image</td>
    <td><p>All images use cloud-init, which allows you to enter user meta data associated with the instance for post provisioning scripts.</p>
    <p>The following stock images are supported:
    <ul>
    <li>CentOS 7.x minimal</li>
    <li>Ubuntu 16.04 minimal</li>
    </ul></p>
    <p>For more information, see [Images](vsi_is_images.html).</p>
    </td>
    </tr>
    <td>SSH Key</td>
    <td>
    <p>You must enter or upload an SSH key to connect before provisioning. SSH keys give you access to the instance without using a password. While you cannot generate a key, you can add a key by providing your unique alpha-numeric combination.</p>
    <p>Note: Alpha-numeric combinations are limited to 100 characters.</p>
    <p>For more information, see [SSH Keys](vsi_is_ssh_keys_about.html).</p></td>
    </tr>
    <tr>
    <td>User data</td>
    <td>
    <p>You can add user data that automatically performs common configuration tasks or runs scripts. <p>For more information, see [User Data](vsi_is_provisioning_scripts.html).</p>
    </td>
    </tr>
    <tr>
    <td>Boot volume</td>
    <td>The default boot volume size for all profiles is 100 GB.</td>
    </tr>
    <tr>
    <td>Network interfaces</td>
    <td>Assign networking options to connect into the virtual private cloud. You can create and assign a single network interface to your instance.</td>
    </tr>
    </TBODY>
    </table>

    Your *Cost summary* displays on the right side of the *New virtual server instance* page.

3. Click **Create virtual server instance** when you are ready to provision.

Do you prefer to create an instance using the CLI? For more information, see [Creating an instance using the CLI](vsi_is_create_instance_cli.html).
{: tip}

## What happens next
<!-- A series of emails are sent to your administrator: acknowledgment of the virtual server instance order, order approval and processing, and a message stating the instance is created. -->

After the server is created, associate a floating IP address to the instance. Then you can [connect to your instance](vsi_is_connecting_linux_gc.html).
