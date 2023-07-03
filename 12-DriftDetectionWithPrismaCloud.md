# Cloud DevSecOps Lab
## Drift Detection with Prisma Cloud
In this final section, you'll switch gears and detect drift. Drift occurs when the infrastructure deployed in the cloud is different from what was defined in the IaC template. You call what the infrastructure should be the “state” saved in files locally or in Terraform Cloud. For example, if the infrastructure in AWS may have different configurations than the Terraform template defined.

This usually occurs during a major incident, where DevOps and SRE teams make manual changes to quickly solve the problem, such as opening up ports to larger CIDR blocks or turning off HTTPS to find the problem, or if there are knowledge or access control gaps that make fixing an issue in the cloud directly the easier option. If these aren’t reverted, they present security issues and it weakens the benefits of using IaC.

### Change your repository to Private
1. In GitHub, navigate to your repository, click on Settings. 
![alt text](/resources/github-settings-1.png?raw=true)

2. Scroll down to the Danger Zone, click on "Change visibility", click "Change to private", click "I want to make this repository private", "I have read and understand these effects", and "Make this repository private". You might need to key in your password to change this. 
![alt text](/resources/github-danger-zone.png?raw=true)

3. Once you are done, ensure that the repository is now private.
![alt text](/resources/github-danger-zone-private.png?raw=true)


### Create Alert Rule to detect drift
1. In Prisma Cloud, navigate to Alerts > Alert Rules, and click "Add Alert Rule".
![alt text](/resources/pc-create-alert-rule.png?raw=true)

2. Input an alert rule name (put in your name/initial, such as *bechong*-drift-detection). Enable Alert Notification, and click Next.
![alt text](/resources/pc-add-alert-rule-2.png?raw=true)

3. Select your Account Group and click Next.
![alt text](/resources/pc-add-alert-rule-3.png?raw=true)

4.  In the Assign Policies window, in the search bar, type "aws traced" and you should see the policy show up in the list, select the "AWS traced resources are manually modified", and click Next.
![alt text](/resources/pc-add-alert-rule-4.png?raw=true)

5. Enable email notification by clicking Emails, input your email address and click Next.
![alt text](/resources/pc-add-alert-rule-5.png?raw=true)

6. In the Summary window, just Click Save.

### Create Drift
Make sure that you have applied the Terraform resources from the Pull Request section, and confirm in your AWS console that your new S3 bucket is up. Go to the [S3 console](https://s3.console.aws.amazon.com/s3/home) and confirm that there is a new bucket running. 
![alt text](/resources/aws-s3-created.png?raw=true)

1. In the S3 AWS Console, click on the newly created S3 bucket, and click on "Properties" tab. 
![alt text](/resources/aws-s3-properties.png?raw=true)

2. Scroll down to "Tags" and click Edit.
![alt text](/resources/aws-s3-properties-2.png?raw=true)

3. Click "Add tag", type in "Drift for key, and "ThisisTheDrift" for value. Click Save changes.
![alt text](/resources/aws-s3-properties-3.png?raw=true)

# Congratulations!
You have now created a simple drift in your s3 bucket. Now, time to wait until Prisma Cloud notices the change and generate the alert. This can take anywhere from 15 minutes to an hour, depending on the scan cycle. Once the drift is detected, you can either run ```terraform apply``` again in Terraform Cloud to fix the drift by matching it back to the IaC configuration. If the cloud configuration is correct, the changes on the IaC template can be made by submitting a PR through Prisma Cloud. In the Projects page, you will be able to find the drift by filtering IaC Categories to "Drift". Click on the policy and the "+" icon, and click Submit.

We have another bonus stage where you can try it out by clicking [here](/13-IntegratingPrismaCloudtoIDE.md))