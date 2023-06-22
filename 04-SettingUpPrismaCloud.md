# Cloud DevSecOps Lab
## Preparing Prisma Cloud
Prisma Cloud is the industry’s most complete Cloud Native Application Protection Platform (CNAPP), with the industry’s broadest security and compliance coverage—for infrastructure, workloads, and applications, across the entire cloud native technology stack—throughout the development lifecycle and across hybrid and multicloud environments. Prisma Cloud Code Security provides a single tool for securing code across all modern architectures and software supply chains, including identifying misconfiguration on IaC.

### Logging in to Prisma Cloud & Generating API Access Key
As part of this workshop, you will be given access to Prisma Cloud Lab tenant, with your registered corporate email. You should have received an email regarding access to Prisma Cloud. The email should look like this:
![Alt Text](/resources/prisma-cloud-welcome-email.png?raw=true)
If you have no receive an email regarding the login, please contact the lab instructor for further assistance. 

1. Click on the "Get Started" button, where you will be redirect to the login page. Login with your credentials created with Palo Alto Networks Customer Support Portal. Once logged in, you will see the home page of Prisma Cloud.
![Alt Text](/resources/prisma-cloud-home-page.png?raw=true)

2. Go to Settings > Access Control, click Add > Access Key.
![Alt Text](/resources/pc-add-ak.png?raw=true)

3. Insert a name for your Access Key (use initials for easy identification, such as bechong-ci-accesskey), and click Save. Download the access key & secret key in csv file so that you are able to use it later.
![Alt Text](/resources/pc-save-ak.png?raw=true)

### Checkov
In this tutorial, we will be using [Checkov](https://www.checkov.io/). Install Checkov in your Cloud9 CLI with pip:
```
pip3 install checkov
```

### Install Yor.io
We will also be using Yor, an open-srouce tool from Prisma Cloud (formally bridgecrew) that helps add informative and consistent tags across infrastructure as code (IaC) frameworks.
```
wget -q -O - https://github.com/bridgecrewio/yor/releases/download/0.1.62/yor-0.1.62-linux-amd64.tar.gz | sudo tar -xvz -C /usr/bin
```




