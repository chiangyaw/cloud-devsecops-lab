![alt text](/resources/PRISMA_CLOUD_LOGO_color_dark_background.png?raw=true)
# Cloud DevSecOps for Terraform with Prisma Cloud Hands on Lab
## Prisma Cloud by Palo Alto Networks

### Introduction
In this workshop, you’ll learn how to leverage infrastructure as code (IaC) and DevSecOps to automate, scale, and improve the security posture of your cloud infrastructure. We’ll create a pipeline that provides frequent, easy-to-digest improvements to ensure our configurations are secure and compliant from the build-time to runtime.

We will be using the following tools as part of this lab:
- Prisma Cloud
- Terraform Cloud
- Github

[Prisma Cloud](https://www.paloaltonetworks.com/prisma/cloud) is the industry’s most complete Cloud Native Application Protection Platform (CNAPP), with the industry’s broadest security and compliance coverage—for infrastructure, workloads, and applications, across the entire cloud native technology stack—throughout the development lifecycle and across hybrid and multicloud environments. As part of this lab, we would be leveraging one of Prisma Cloud's feature, which is Infrastructure as Code (IaC) Security to provide visibility & guardrail on IaC misconfigurations across the development lifecycle, embedding security in integrated development environments, continuous integration tools, repositories and runtime environments.

[Terraform Cloud](https://www.hashicorp.com/resources/what-is-terraform-cloud) is a cloud infrastructure management tool that allows users to easily create and remotely manage their cloud infrastructure in a consistent and efficient manner. You can use it to manage cloud infrastructure, including Amazon Web Services, Google Cloud Platform, and Microsoft Azure. We will be using Terraform Cloud as part of this lab to provision resources in AWS, and integrating with Prisma Cloud for IaC security.

[GitHub](https://github.com/) is a platform and cloud-based service for software development and version control, allowing developers to store and manage their code. We will be using GitHub as the version control system here to store the Terraform templates, and integrating with Terraform Cloud for cloud resource provisioning. In the meantime, integrating with Prisma Cloud for IaC security as well.

Using Prisma Cloud, VS Code, GitHub, Terraform Cloud, and AWS, we’ll get hands-on experience implementing an automated Terraform security and compliance workflow.

#### Prerequisites
* Access to Prisma Cloud Lab Tenant
* AWS Cloud Account
* Personal Git Account (register one [here](https://github.com/signup) for free)
* Terraform Cloud Account (register one [here](https://app.terraform.io/public/signup/account) for free)
* A willingness to learn and experiment
* A laptop where you can install or already have the following:
  * A reliable browser such as Google Chrome, Firefox, etc
  * VS Code
  * Git
  * Terraform

#### Learning Objectives
* Get an overview of DevSecOps and Terraform infrastructure as code (IaC)
* Scan IaC files for misconfigurations locally
* Set up CI/CD pipelines to automate security scanning and policy enforcement
* Fix IaC security errors and AWS resource misconfigurations with Bridgecrew

Click [here](/01-SettingUpAWSAccount.md) to get started!