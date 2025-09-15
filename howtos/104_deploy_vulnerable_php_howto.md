
# HowTo 104: Deploy a vulnerable PHP app on Azure and protect it with Zen Firewall

## Overview

This howto walks you through deploying a deliberately vulnerable PHP application on an Ubuntu VM running on Microsoft Azure and securing it with Aikido Security’s Zen Firewall. The goal is to demonstrate how an in-app firewall (or Application Detection and Response capability, previously referred to as RASP or Runtime Application Self-Protection) can detect and block real-world attack traffic in a cloud environment, giving you hands-on experience with both exploitation and defense.

---

## Learning Objectives

By the end of this howto, you will:

- create a free Azure subscription
- provision an Ubuntu Linux VM
- install an Apache webserver with PHP 8
- deploy a Let's Encrypt x509 certificate
- protect the vulnerable PHP application
- verify that rate limiting and TOR browser blocking are applied

---

## Tools & Requirements

- a domain name that you own and admin (recommend purchasing one via [Cloudlflare](https://www.cloudflare.com/products/registrar/))
- [GitHub](https://github.com/)
- [Azure Cloud](https://azure.microsoft.com/en-us/pricing/free-services)
- [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
- [Ubuntu Linux VM](https://ubuntu.com/server)
- [certbot](https://certbot.eff.org/)
- [ApacheBench](https://httpd.apache.org/docs/2.4/programs/ab.html)
- [cURL](https://en.wikipedia.org/wiki/CURL)
- [Aikido Zen Firewall for PHP](https://github.com/AikidoSec/firewall-php)

---

## Setup

1. **Buy a domain**

Before diving into the capabilities of the Aikido Zen Firewall to protect a legacy application or API, we first need to build some core elements like purchasing a domain name. This will be useful for other labs and howtos and we highly recommend that everyone learn cybersecurity by doing cybersecurity. You can purchase a domain for around US$15 per year from [Cloudflare](https://www.cloudflare.com/products/registrar/) who are a reputable registrar and who offer lots of great free features for protecting your website.

2. **Create an Azure Subscription**

You’ll need access to an Azure Cloud account. If you don’t already have one, Microsoft offers a [free subscription](https://azure.microsoft.com/en-us/pricing/free-services) to new users for 12 months that provides a limited set of services and credits to get started. Setting up the free subscription only takes a few minutes and ensures you’ll be able to complete the steps in this guide without incurring unexpected costs.

---

## Instructions

### Step 1: Pick an FQDN for your vulnerable PHP application

An [FQDN](https://en.wikipedia.org/wiki/Fully_qualified_domain_name), or Fully Qualified Domain Name, is the complete, unique address of a device or server on the internet's Domain Name System (DNS), much like a full street address for a house. It consists of a hostname, one or more subdomains, a domain name, and a top-level domain (like .com or .edu or .net or .dev or .io), providing the exact path to identify a resource without ambiguity. An example of an FQDN is hailhydra.com or archive.org.

One of the great benefits to owning your own domain is that you immediately gain an infinite supply of email addresses to use as you see fit. And if you configure Cloudflare to host your DNS services and records, you can have them all forwarded to a free Gmail account and never have to use your real email address again when downloading whitepapers or signing up for services and trial accounts. But that particular construction is it's own howto article unto itself and best left for another day. For the moment, just make sure that you are able to add a DNS record to your personal domain so that you can complete the rest of the tasks below.

---

### Step 2: Provision an Ubuntu Linux VM on Azure

Install the [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/?view=azure-cli-latest) and run the following commands

```
az login
az group create -l eastus -n mytest104
```

This will trigger a login page to be displayed on your web browser and then create a resource group named **mytest104**

If you already have an ssh private key in your ~/.ssh/ directory, you can proceed to the VM creation step below. If you have never created an ssh private/public keypair, you will need to do so using this command on a Mac (for Windows you will need to replace the ssh-key-value path below to the location of your public key in openssh format):

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

where you replace "your_email@example.com" with your actual email address. This creates a file in your ~/.ssh/ directory called id_rsa.pub (the public key) and id_rsa (the private key). Make sure to note the passphrase that you set on your private key because if you lose it or forget it you will need to delete the VM and start over since you cannot login to it anymore using ssh.

Next, create an Ubuntu Linux VM in that resource group in the US East Azure Cloud datacenter:

```
az vm create \
  --resource-group mytest104 \
  --name ubuntu104 \
  --image Ubuntu2404 \
  --size Standard_D2s_v3 \
  --admin-username azureuser \
  --ssh-key-value ~/.ssh/id_rsa.pub \
  --public-ip-sku Standard 

az vm open-port --port 22,80,443 --resource-group mytest104 --name ubuntu104

```

The ouput from this command, if successful, will include the public IP address that was assigned to your VM. Make a note of this address as you need it later in subsequent steps of this howto.

This creates a VM named **ubuntu104** using the Ubuntu LTS 22.04 release with a username for ssh remote access of **azureuser** and to create the necessary ssh private/public keys for accessing the server once it is provisioned. The commands above also instruct Azure to add firewall rules to allow the server to be reachable on TCP ports 22 (for ssh and scp), 80 (for http) and 443 (for https). You will see why we include port 80 in a later step involving certbot.

Now, verify that you can ssh to the server by using the ssh .pem file that was created. The command will look something like this (where the public IP address will be different of course as this is dynamically assigned at the time of creation from a pool of available IP addresses for that region of Azure cloud):

```
ssh azureuser@<public-ip-address>
```

---

### Step 3: Install Apache and PHP on the VM

---

### Step 4: Install Zen Firewall PHP package on the VM

---

### Step 5: Run some tests and configure some protections

- ApacheBench
- BlazeMeter Taurus
- cURL
- TOR Browser
- Geo Blocking
- BOT Blocking
- SQL Injection
- Directory Traversal

## Submission Checklist

- [ ] Screenshot of your FQDN DNS entry
- [ ] Screenshot of your Azure VM resources.

---

## Optional Extension

- **Try some more attacks like TBD**
  - one
  - two
  - three

---

## Grading Rubric (Sample)

| Task                              | Points |
|-----------------------------------|--------|
| Domain purchase                   | 10     |
| Azure subscription                | 10     |
| Ubuntu VM provisioning            | 10     |
| Zen Firewall Install and Testing  | 10     |
| **Total**                         | **40** |

---

## Additional Resources

- one
- two
- three

---

## License

© 2025 [Mike Wilkes](https://www.linkedin.com/in/eclectiqus/). This work is licensed under the [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) license.

Attribution should be given to [Aikido Security](https://aikido.dev).

[![Creative Commons License](https://licensebuttons.net/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/)

