# Cloud DevSecOps Lab
## Investigating with Prisma Cloud
Providing feedback in IDEs and CI/CD pipelines provides valuable insights into the posture of your code. Prisma Cloud provides a centralized view for tracking misconfigurations across your code scans and runtime environments. We’ll start with the view across code scans.

1. In Prisma Cloud, navigate to Code Security > Projects. Click on IaC Misconfiguration tab, filter to your repository under Repositories. You can run through all the different misconfiguration identified by Prisma Cloud. For this section, we will just take one of the misconfiguration and perform a fix via Pull Request. Click on the search icon, and search for "RDS". 
![alt text](/resources/pc-projects-filter.png?raw=true)


2. Click on the policy "Not all the data stored in Aurora is securely encrypted at rest". Review the issue on the right panel. You can click on Details & Issues tab to understand further on the misconfiguration itself and the recommended fix. 
![alt text](/resources/pc-code-review.png?raw=true)

3. To trigger a fix through Prisma Cloud, click the "+" icon on the chosen policy, and click "Submit".
![alt text](/resources/pc-code-submit.png?raw=true)
![alt text](/resources/pc-code-submit-2.png?raw=true)

4. Navigate back to the GitHub repository, click on Pull Request, you will see a new pull request by prisma-cloud-devsecops. Click on the Files changed tab to understand what are the changes are proposed for this PR.
![alt text](/resources/github-pc-pr.png?raw=true)

5. To complete the fix, navigate back to the conversation tab, click on "merge pull request", and click "confirm merge".
![alt text](/resources/github-pr-merge.png?raw=true)

# Congratulations!
You have now built an automated IaC scanning workflow in a live environment and automated the fixing of an IaC template! Move on to the next section [here](/12-DriftDetectionWithPrismaCloud.md)

