# Cloud DevSecOps Lab
## Test Pull Request
1. Check that all three integrations are working by kicking off a pull request. Go back to your ```simpleenv``` repo that you have created and select “Add file” -> “Create new file.” Set the path to ```terraform/simple_instance/s3.tf```. Add the following code:
```
provider "aws" {
  region = "ap-southeast-1"
}

resource "aws_s3_bucket" "prismaclouds3" {
  bucket_prefix = "prismacloud-s3"

  tags = {
    Name                 = "Prisma Cloud"
    Environment          = "Dev"
  }
}
```
![alt text](/resources/github-add-new-tf-2.png?raw=true)
Click "Commit changes", select "Create a new branch for this commit and start a pull request", and click "Propose changes".
![alt text](/resources/github-propose-changes.png?raw=true)

2. On the comparing changes page, click "Create pull request". On Open a pull request page, click Create pull request.
![alt text](/resources/github-create-pr.png?raw=true)

3. On the pull request page, you should see a few scans running and prisma-cloud-devsecops providing comments on the misconfigured items. 
![alt text](/resources/github-pc-scan-2.png?raw=true)
![alt text](/resources/github-scan-passed.png?raw=true)
As part of this lab, you won't be required to fix all the violations if there is any. As for now, scroll to the bottom, click "Merge pull request" and "Confirm Merge". 
![alt text](/resources/github-confirm-merge-2.png?raw=true)

By merging the pull request, you are merging your changes to your main code branch. This is a very standard or common activity in developers world where pull request is constantly generated, and it might requires a manager or senior developers to approve the changes. By having Prisma Cloud Code Security (prisma-cloud-devsecops) commenting on code change, Prisma Cloud is providing insights to the approver the security risks that are added to the main code branch. The approver can choose to disapprove the pull request if any misconfiguration is identified.

## Deploying cloud resources through Terraform Cloud
Now you have merged the pull request, a new resource (S3 bucket in this scenario) is required to be added as part of the update. With Terraform Cloud, the changes are automatically picked up, and requires confirmation to be deployed into the cloud environment. With Prisma Cloud Code Security integration as Run Task, Prisma Cloud is able to stop the deployment if any misconfiguration or policy violation is found.

1. Go back to Terraform Cloud, go to the workspace that you have created, and under Overview, you should see the details on the Latest Run. Click on "See Details".
![alt text](/resources/tc-latest-run-see-details-2.png?raw=true)

2. On the details, you should see "Pre-plan passed" and if you click into it, click on "Details", it will open a new tab on Prisma Cloud, which give you the details on the scan.
![alt text](/resources/tc-details-pre-plan.png?raw=true)
![alt text](/resources/pc-post-plan-result.png?raw=true)
Currently, these open issues are configured as **Soft Fail**, therefore it is still possible to proceed to apply.

3. Scroll down on Terraform Cloud, click on "Confirm & Apply". Add a comment such as "creating new s3 bucket" and Click "Confirm Plan".
![alt text](/resources/tc-confirm-apply.png?raw=true)
![alt text](/resources/tc-confirm-plan.png?raw=true)
The S3 bucket will be provisioned as per the Terraform plan. Once completed, you will be able to see the S3 bucket resource in your AWS account by searching for "s3" on the search bar on top.
![alt text](/resources/aws-s3-created.png?raw=true)

# Congratulations!
You have now completed mering a pull request in a GitHub repository, with Terraform Cloud & Prisma Cloud integration, and automated the security checks with configurable **Hard Fail** (if require) when a misconfiguration is identified. Head over to the next lab to investigate and fix the issues arising from the automated scans, as well as providing more tips for integrating security into the developer workflow without causing friction. Move on to the next section [here](/11-InvestigatingWithPrismaCloud.md)