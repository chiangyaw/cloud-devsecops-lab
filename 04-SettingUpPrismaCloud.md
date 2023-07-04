# Cloud DevSecOps Lab
## Preparing Prisma Cloud
Prisma Cloud is the industry’s most complete Cloud Native Application Protection Platform (CNAPP), with the industry’s broadest security and compliance coverage—for infrastructure, workloads, and applications, across the entire cloud native technology stack—throughout the development lifecycle and across hybrid and multicloud environments. Prisma Cloud Code Security provides a single tool for securing code across all modern architectures and software supply chains, including identifying misconfiguration on IaC.

### Logging in to Prisma Cloud & Generating API Access Key
As part of this workshop, you will be given access to Prisma Cloud Lab tenant, with your registered corporate email. You should have received an email regarding access to Prisma Cloud. The email should look like this:
![Alt Text](/resources/prisma-cloud-welcome-email.png?raw=true)
If you have no receive an email regarding the login, please contact the lab instructor for further assistance. 

1. Click on the "Get Started" button, where you will be redirect to the login page. Login with your credentials created with Palo Alto Networks Customer Support Portal (CSP). If you don't have a CSP account, refer to the troubleshooting steps below for workaround.
Once logged in, you should see the First Time Wizard. Choose "Code/Build" and click "Continue". It will land you into the repository page.
![Alt Text](/resources/pc-ftw.png?raw=true)
Note: If you don't see the First Time Wizard page, it means that you have logged into Prisma Cloud before. Just proceed to the next step.

2. Go to Settings > Access Control, click Add > Access Key.
![Alt Text](/resources/pc-add-ak.png?raw=true)

3. Insert a name for your Access Key (use initials for easy identification, such as bechong-ci-accesskey), and click Save. Download the access key & secret key in csv file so that you are able to use it later.
![Alt Text](/resources/pc-save-ak.png?raw=true)

Once you are done setting up Prisma Cloud environment, you can move on to the next section [here](/05-IaCScanning.md)


### Troubleshooting access to Prisma Cloud 
There are situation where you are not able to access to Prisma Cloud as you do not have a Customer Support Portal (CSP) account with Palo Alto Networks. Upon clicking the link on the received email and if you can't login because you don't have the CSP account, run through these steps to access Prisma Cloud. 

1. Click on the Prisma Cloud Legacy Sign In Link [here](https://app.sg.prismacloud.io/legacy/signin).

2. Click on "Forgot Password?" and input the email you provided as part the workshop registration (it should be your work email). Click "Send Link".
![alt text](/resources/pc-legacy-signin.png?raw=true)

3. You should receive the password reset email, where you are able to update your password. Once done, use the new password to login to Prisma Cloud.
![alt text](/resources/pc-reset-password.png?raw=true)

Once you are able to login to Prisma Cloud, continue with the steps on 