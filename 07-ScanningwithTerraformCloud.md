# Cloud DevSecOps Lab
## Integrating Terraform Cloud & Prisma Cloud 
Prisma Cloud has a native integration with Terraform Cloud that leverages Run Task for security controls. This means any commit that is pushed to Terraform Cloud will run through a Prisma Cloud Code Security scan, identifying policy violations, blocking misconfigured builds through hard-fail, and detecting drift, all from the same place that you collaborate on Terraform templates, automate deployments, and store state. As part of this lab, we have pre-configured the policy to soft-fail, which means it will still pass through even though there is a violation of policy.

1. Go to Terraform Cloud portal. If this is your first time on Terraform Cloud, you will see the First Time Wizard, where you need to click "Start from Scratch", input a organization name (any name will do), email address and click "Create Organization".
![alt text](/resources/tc-create-org.png?raw=true)

2. Once done, click New > Workspace.
![alt text](/resources/terraform-cloud-workspace.png?raw=true)
3. Choose version control workflow, and click Github.
![alt text](/resources/tc-vc-workflow.png?raw=true)
![alt text](/resources/tc-vc-github.png?raw=true)
4. You will be prompted with a pop up window to install Terraform Cloud to your GitHub account, choose the correct organization, click Only select repositories, and choose the ```simpleenv``` repository that you have just created, and then click Install.
![alt text](/resources/github-install-tc.png?raw=true)
5. Back to the Terraform Cloud page, choose the repository, and click Create workspace.
![alt text](/resources/tc-create-workspace.png?raw=true)
6. Once the workspace is created, click continue to workspace overview, and click Configure variables.
![alt text](/resources/tc-configure-variables.png?raw=true)
7. You will need to add your AWS Account details as environment variables called 'AWS_ACCESS_KEY_ID' and 'AWS_SECRET_ACCESS_KEY'. If you got the account from AWS event using AWS Event Engine, include the 'AWS_SESSION_TOKEN'. If you are not sure where to obtain these information, refer to [this guide](https://docs.aws.amazon.com/powershell/latest/userguide/pstools-appendix-sign-up.html)
![alt text](/resources/terraform_cloud_env_variables.png?raw=true)
For Event Engine, it will look like this:
![alt text](/resources/terraform_cloud_env_variables_ee.png?raw=true)

**Note: Please make sure you are adding them as Environment variable, not Terraform variable.**
![alt text](/resources/tc-workspace-env-var.png?raw=true)

8. Go to workspace Settings > General, under Terraform Working Directory, add the directory ```/terraform/simple_instance/```

9. Create an API token from Terraform Cloud for the integration with Prisma Cloud. Go to the API token menu (User > Settings > Tokens) and select "Create an API token". Input a description such as, "Prisma Cloud Integration" and click "Generate Token". Copy the API token for the next step.
![alt text](/resources/tc-generate-token.png?raw=true)

10. Head back to Prisma Cloud portal, go to Settings > Repositories > Add Repositories.
![alt text](/resources/pc-add-repo-tc.png?raw=true)

11. Choose Terraform Cloud (Run Tasks). In the Configure Account window, add the API token generated in the previous step. Click Next.
![alt text](/resources/pc-add-tc-token.png?raw=true)

12. In the Select Organization window, choose your organization created, click Next. In the Workspace window, select the workspace you have created, choose "Post-plan, After Terraform creates the plan", and then click Next. On the status window, just click Done.
![alt text](/resources/pc-add-tc-workspace-2.png?raw=true)

13. To verify the integration on Terraform Cloud side, go back to your created Workspace > Settings > Run Tasks, you should be able to see "prisma-cloud" added into your Terraform Cloud workspace.
![alt text](/resources/tc-verify-pc-integration-2.png?raw=true)

14. Once verified, go back to the workspace main page, and click "Start new plan" OR you can click "Actions" > "Start new run" > choose "Plan only" as run type > click "Start run". 
![alt text](/resources/tc-plan-only.png?raw=true)
Don't worry if it fails, this is just to make sure the runs to be automated with future GitHub pull requests.

Once completed, move on to the next section [here](/08-AddingRepoToPrismaCloud.md)