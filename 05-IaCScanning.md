# Cloud DevSecOps Lab
## Create a new repository
To set up a small demo environment for this workshop, you will need prepare a Terraform repository, which will provision a RDS. Make sure you have logged into your GitHub personal account before the following action.
1. Head over to your [GitHub dashboard](https://github.com/dashboard), and click "New".
![alt text](/resources/github-new-repo.png?raw=true)

2. Give your new repository a name ```simpleenv```. Tick "Add a README file" and click "Create repository".
![alt text](/resources/github-new-repo-6.png?raw=true)

3. Click "creating a new file" to create a new file.
![alt text](/resources/github-new-file.png?raw=true)

4. Set the path to ```simpleenv/terraform/rds.tf```. Add the following code:
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
![alt text](/resources/github-new-file-2.png?raw=true)
![alt text](/resources/github-new-file-3.png?raw=true)
Now you have created a terraform file in your GitHub repository!

5. Create a local copy of ```simpleenv``` repo in your Cloud9 environment. You might need to type "yes" after the first command, since it is the first time you are connecting to this fork via Cloud9.
```
git clone https://github.com/<your-organization>/simpleenv.git
cd simpleenv
git status
```
Sample output:
```
git clone https://github.com/chiangyaw8/simpleenv.git
cd simpleenv
git status
Cloning into 'simpleenv'...
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 7 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (7/7), done.

On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

## Run Checkov locally
To demonstrate what kinds of security and compliance errors Prisma Cloud can identify in Terraform templates, start by using Checkov and send the results to the Prisma Cloud platform. You are able to run this locally to have a quick scan on the templates, and this can be a form of integration to your CI/CD tools as well if your CI/CD tool is not supported by Prisma Cloud natively. 
1. You will first need to add in your API keys you have gotten from Prisma Cloud in earlier section. export it as a variable with the following command (replace the prismaaccesskey & prismasecretkey):
```
export PRISMA_API_URL=https://api.sg.prismacloud.io
export BC_API_KEY=<prismaaccesskey>::<prismasecretkey>
```


1. scan the `rds.tf` in the `terraform` directory:
```
checkov -f terraform/rds.tf --repo-id <your-org>/simpleenv
```
Check out the findings as part of the scan. The results will show all the failed policies and link to guides explaining the rationale behind each misconfiguration and steps to fix them. Note the output also includes the filename and snippet of code that is misconfigured
![alt text](/resources/checkov-simpleenv-rds.png?raw=true)

# Congratulations!
You have now completed the IaC code scanning locally via Checkov! You can now move on to the next section [here](/06-OnboardAWStoPrismaCloud.md)