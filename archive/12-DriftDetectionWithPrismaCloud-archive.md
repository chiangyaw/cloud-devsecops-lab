# Cloud DevSecOps Lab
## Drift Detection with Prisma Cloud
In this final section, you'll switch gears and detect drift. Drift occurs when the infrastructure deployed in the cloud is different from what was defined in the IaC template. You call what the infrastructure should be the “state” saved in files locally or in Terraform Cloud. For example, if the infrastructure in AWS may have different configurations than the Terraform template defined.

This usually occurs during a major incident, where DevOps and SRE teams make manual changes to quickly solve the problem, such as opening up ports to larger CIDR blocks or turning off HTTPS to find the problem, or if there are knowledge or access control gaps that make fixing an issue in the cloud directly the easier option. If these aren’t reverted, they present security issues and it weakens the benefits of using IaC.

### Build a new repository for drift detection
1. Head over to your [GitHub dashboard](https://github.com/dashboard), and click "New".
![alt text](/resources/github-new-repo.png?raw=true)

2. Give your new repository a name (to keep it simple, you can call this ```simpleenv```). Change the repository to "Private", tick "Add a README file, and click "Create repository".
![alt text](/resources/github-new-repo-2.png?raw=true)

### Setting Up GitHub Action with Yor
Yor is an open-source tool that automatically tags infrastructure as code (IaC) templates with attribution and ownership details, unique IDs that get carried across to cloud resources, and any other need-to-know information. It can run locally, as a pre-commit hook, or in a CI/CD pipeline.

For drift detection, the important tag is yor_trace. It’s a unique identifier that helps us trace from a cloud runtime configuration back to the IaC that provisioned it. To do that we need 3 elements:
- Yor automated tagging (this page)
- Integration with the VCS that stores the IaC (Adding Repository to Prisma Cloud, done in the previous section)
- Cloud integration (Onboarding your AWS account to Prisma Cloud, done in the previous section)

### Adding the Yor GitHub Action
1. In your GitHub repository, click "Add file" > "Create new file". 
![alt text](/resources/github-new-file.png?raw=true)

2. Set the path to ```.github/workflows/yor.yaml```. Add the following code:
```
name: IaC trace

on:
  push:
  pull_request:
  workflow_dispatch:

jobs:
  yor:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        name: Checkout repo
        with:
          fetch-depth: 0
          ref: ${{ github.head_ref }}
      - name: Run yor action and commit
        uses: bridgecrewio/yor-action@main
```
Click "Commit Changes", tick on "Commit directly to the ```main``` branch, and click "Commit changes". 

3. Navigate to Settings > Actions > General, under Workflow permissions, change to "Read and write permissions" and click "Save".
![alt text](/resources/github-actions-permission.png?raw=true)


This will run Yor to automatically tag your IaC resources every time you perform a push or pull request. The result will look something like this:

![alt text](/resources/github-yor-tags.png?raw=true)

The ```yor_trace``` tag will be used to track drift in your resources. 

4. Go back to the repository main page, click "Add file" to create another file.

5. Set the path to ```simpleenv/vpc.tf```. Add the following code:
```
resource "aws_rds_cluster" "app1-rds-cluster" {
  cluster_identifier      = "app1-rds-cluster"
  allocated_storage       = 10
  backup_retention_period = 0
  tags = {
    Name = "app1-rds-cluster"
    Environment = "prod"
  }
}
```
Click "Commit changes". On the popped up window, click "Commit changes". 
![alt text](/resources/github-new-repo-4.png?raw=true)
![alt text](/resources/github-new-repo-5.png?raw=true)
Now you have created a terraform file in your GitHub repository!

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
