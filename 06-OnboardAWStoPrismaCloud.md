# Cloud DevSecOps Lab
## Onboard AWS Account to Prisma Cloud
Prisma Cloud is able to provide comprehensive security from code to cloud. Other than the code security as part of this lab, Prisma Cloud is also able to detect misconfigurations on the cloud resources that are deployed. As part of this lab, you will need to onboard an AWS account. 


1. In the Prisma Cloud tenant, go to Settings > Cloud Accounts. Click Add Cloud Account and choose "Amazon Web Services".
2. Click on Accounts, untick on Agentless Workload Scanning, and then click Next.
![alt text](/resources/pc-onboarding-1.png?raw=true)
3. Input your AWS Account ID, and Account Name (put in your name/initial, such as *bechong*-AWS-Account). Untick Remediation by ticking the checkbox. Click “Create IAM Role”. This will prompt a new tab to create a CloudFormation stack for the IAM role.
![alt text](/resources/pc-onboarding-2.png?raw=true)

4. Tick on “I acknowledge that AWS CloudFormation might create IAM resources with custom names”, and click Create Stack.
![alt text](/resources/aws-onboarding-1.png?raw=true)

5. Once creation is completed, go to the Outputs tab, copy the value of PrismaCloudRoleARN, paste it into the Prisma Cloud onboarding window in the IAM Role ARN textbox. Click Next.
![alt text](/resources/aws-onboarding-2.png?raw=true)

6. Wait for the authentication check to be completed, you should see everything as green tick except those which are not enabled. Click Save and Close to proceed.
![alt text](/resources/pc-onboarding-3.png?raw=true)

Your AWS assets information will not be available in Prisma Cloud immediately. It will take up to 24 hours to be reflected, but for small environments, you should be able to see it in less than 1 hour. In the meantime, feel free to proceed to the next step [here](/07-ScanningwithTerraformCloud.md))