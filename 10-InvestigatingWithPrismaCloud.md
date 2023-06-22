# Cloud DevSecOps Lab
## Investigating with Prisma Cloud
Providing feedback in IDEs and CI/CD pipelines provides valuable insights into the posture of your code. Prisma Cloud provides a centralized view for tracking misconfigurations across your code scans and runtime environments. We’ll start with the view across code scans.

1. In Prisma Cloud, navigate to Code Security > Projects. Click on IaC Misconfiguration tab, filter to your repository under Repositories. You can run through all the different misconfiguration identified by Prisma Cloud. For this section, we will just take one of the misconfiguration and perform a fix via Pull Request. Click on the search icon, and search for "RDS". 
![alt text](/resources/pc-projects-filter.png?raw=true)


2. Click on the policy "Not all the data stored in Aurora is securely encrypted at rest". Click on the 
