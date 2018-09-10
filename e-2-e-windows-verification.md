---

copyright:
  years: 2017, 2018

lastupdated: "2018-08-29"


---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Using the CLI for end-to-end verification of a Windows instance

This example shows you how to get end-to-end authorization when connecting to a Windows instance, using the CLI.

## Pre-requisites

* Ask your account administrator to grant you Windows access to retrieve the password from the VSI.
* Make sure you create a new VPC and subnet. (An old VPC and subnet won't support this feature.)
* Create a new security group or add the rule to default security group to allow the remote port for a user to log in.

## Step 1. Prepare an SSH RSA Key

Use the command `ssh-keygen` to generate your SSH RSA key.

Note: Two formats exist for the key: the `SSH` RSA key and the `openssl` RSA key. The RIAS API supports an SSH RSA key only.

## Step 2. Create the Windows image

Replace parameters with proper ones for _`name`_, _`vpc`_, _`subnet`_, _`security_groups`_, _`key`_ (RSA key), and _`user_data`_.

```
curl -k -X POST -H "Authorization: $iam_token" https://us-south.iaas.cloud.ibm.com/v1/instances  -d "@windows-2012-amd64-b-4x16-sg--perty.json"
cat windows-2012-amd64-b-4x16-sg-perty.json
{
        "name": "perty-win2012sg",
        "type": "virtual",
        "primary_network_interface": {
                "port_speed": 1000,
                "primary_ipv4_address": "",
                "subnet": {
                        "id": "68cca60a-bd74-40a9-864e-1caddc2ca07d"
                },
               "security_groups": [
                  {
                    "id": "b597cff2-38e8-4e6e-999d-000000563459"
                  },
                  {
                    "id": "b597cff2-38e8-4e6e-999d-000000563461"
                  }
                ]
         },
        "zone": {
                "name": "us-south-2"
        },
        "vpc": {
                "id": "e2f75eed-2f06-4cc0-bd58-c0a766c654cc"
        },
        "flavor": {
                "name": "b-4x16"
        },
        "image": {
               "id": "b45450d3-1a17-2226-c518-a8ad0a75f5f8"
        },
        "keys": [{
                "id": "e72af8ee-f3b0-4f4b-b915-0ab091d1f00d"
        }],
        "user_data": "#ps1_sysnative\nSet-Content -Path \"C:\\test.txt\" -Value \"Hello IBM Cloud instance\""
}
```
## Step 3. Get the decrypted password

When you create an instance with a Windows image, a password for your instance is generated automatically. As long as you provided an RSA key when you provisioned the instance, and as long as you have access to the VSI (or you created it), you should be able to retrieve the instance's password.

Before you can get the password, the instance must be running. Query the status until it is running, which could take approcimately 9 minutes, then try to get the password.

```
curl -k -X  GET -H "Authorization: $iam_token" https://us-south.iaas.cloud.ibm.com/v1/instances/50719d04-7463-4172-8ec7-4b874bfdd345/initialization 
{"code":14,"message":"Password is not ready, try later."}

curl -k -X  GET -H "Authorization: $iam_token" https://us-south.iaas.cloud.ibm.com/v1/instances/50719d04-7463-4172-8ec7-4b874bfdd345/initialization | jq .  
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1194    0  1194    0     0    583      0 --:--:--  0:00:02 --:--:--   583
{
  "keys": [
    {
      "fingerprint": "SHA256:dQVLX8DGTX1BItw9LeBjRPeOVO228HHSJ5HKZ5pFRJQ",
      "id": "6e574731-76c7-4760-add4-604da4e30835",
      "name": "exampleKey",
    }
  ],
  "password": {
    "encrypted_password": "dSTUbtxTZ/txrYJK8cQ3VxzOFKWwOmFX9JA57ZmPh4seafjRHvYhobnK8Ix5bVeuPDbGpA0uIGloQiSoS6TjDZZgqvubzOKYyfB5UIzI5Lst63HmaxzXuD6K5z9aQ6O6DJjD+e7akAJhWh//ZVC5aPoVmCsHuQCio5caonvizCsq30o1DTTYUPFkIm5xhkpdqMwMWpAFwKKZuYNtAMs6NN1mWibvMFpiWrqNMZ+TehBCTFh93VN0f8JrP+eurHlbQTPX05kXnkSw7ThV+oRXq77eFsICUYF6vy9vofxjyl8WHYjR5H7Ii8SEWV8W9bfosodcsmz/5zJoUNau8Qocqw==",
    "encryption_key": {
        "fingerprint": "SHA256:dQVLX8DGTX1BItw9LeBjRPeOVO228HHSJ5HKZ5pFRJQ",
        "id": "6e574731-76c7-4760-add4-604da4e30835",
        "name": "exampleKey"
    }
  }
}
```

## Step 4. Decrypt the password

Note that `libressl` doesn't currently seem to support the command 
`-pkeyopt rsa_oaep_md:sha256 -pkeyopt rsa_mgf1_md:sha256` 

Run the `openssl` version and ensure that you are not using `libressl`

You can use the commands that follow as an example.

```
echo "dSTUbtxTZ/txrYJK8cQ3VxzOFKWwOmFX9JA57ZmPh4seafjRHvYhobnK8Ix5bVeuPDbGpA0uIGloQiSoS6TjDZZgqvubzOKYyfB5UIzI5Lst63HmaxzXuD6K5z9aQ6O6DJjD+e7akAJhWh//ZVC5aPoVmCsHuQCio5caonvizCsq30o1DTTYUPFkIm5xhkpdqMwMWpAFwKKZuYNtAMs6NN1mWibvMFpiWrqNMZ+TehBCTFh93VN0f8JrP+eurHlbQTPX05kXnkSw7ThV+oRXq77eFsICUYF6vy9vofxjyl8WHYjR5H7Ii8SEWV8W9bfosodcsmz/5zJoUNau8Qocqw==" | base64 --decode > ~/testpwd64

openssl pkeyutl -in testpwd64 -decrypt -inkey ~/.ssh/exampleKey -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256 -pkeyopt rsa_mgf1_md:sha256

cat ~/output
lukUM1vBb7idroW5pGvK
```

## Step 5. Associate the floating IP

Follow this example:

```
curl -k -X  GET -H "Authorization: $iam_token" https://us-south.iaas.cloud.ibm.com/v1/instances/50719d04-7463-4172-8ec7-4b874bfdd345/network_interfaces
cat perty-floatingip-reserver.json
{
  "name": "perty-new-floating-ip",
  "target": {
    "id": "ab5d2245-fd56-43e1-bc64-84d17d1f405e"
  }
}
curl -k -X  POST  -H "Authorization: $iam_token"  https://us-south.iaas.cloud.ibm.com/v1/floating_ips -d "@perty-floatingip-reserver.json"
{"id":"a261bc05-aeec-414e-a152-5081226009ab","name":"perty-new-floating-ip","address":"169.61.161.142",
...
```

## Step 6. Log in to the Windows instance

Ping and then use the proper tool to log in to the Windows instance.

The username is `Administrator` by default.

Example:

```
zous-mbp:regional-compute PertyZou$ ping 169.61.161.142
PING 169.61.161.142 (169.61.161.142): 56 data bytes
64 bytes from 169.61.161.142: icmp_seq=0 ttl=101 time=263.660 ms

```
