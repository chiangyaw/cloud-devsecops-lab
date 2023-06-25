# Cloud DevSecOps Lab
## Integrating PrismaCloud with GitHub
In this section, you'll add a GitHub integration to automatically generate pull request comments and set up for automated fix pull requests (PRs) in the next section. This integration also provides native and automated scanning of incoming commits and pull requests

1. In Prisma Cloud, go to Settings > Repositories.
![alt text](/resources/pc-add-repo.png?raw=true)
2. Click GitHub, and on the popped up window, click Previous.
![alt text](/resources/pc-add-previous.png?raw=true)
3. On the Configure Account window, click Authorize. You will be redirected to your GitHub page to install Prisma Cloud DevSecOps integration, choose the organization, choose Only select repositories, and select the forked terragoat, and click Install & Authorize.
![alt text](/resources/pc-configure-account.png?raw=true)
![alt text](/resources/github-install-pc.png?raw=true)
4. Once redirected back to Prisma Cloud, on the Select Repositories page, click Choose from repository list, tick your forked terragoat repository (Do not untick the other repositories) and click Next. On the status window, just click Done. 
![alt text](/resources/pc-enable-repo.png?raw=true)
**Note: Prisma Cloud will take some time to scan your newly added repository. Prisma cloud will scan your Terraform templates directly from GitHub and bring the results into Prisma Cloud. Once done, you will be able to see in Code Security > Projects.
![alt text](/resources/pc-codesec-projects.png?raw=true)

Once completed, move on to the next section [here](/09-SettingUpGitHubAction.md)