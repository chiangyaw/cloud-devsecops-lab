# Cloud DevSecOps Lab
## Fork the TerraGoat repository on GitHub
To set up your demo environment, we will need the TerraGoat repository. Make sure you have logged into your GitHub personal account before the following action.
1. Head over to the [TerraGoat](https://github.com/bridgecrewio/terragoat) repository and fork it using the button in the upper right corner.
![alt text](/resources/github-fork-terragoat.png?raw=true)

2. Create a local copy of TerraGoat repo in your Cloud9 environment, simply clone your fork. You might need to type "yes" after the first command, since it is the first time you are connecting to this fork via Cloud9.
```
git clone https://github.com/<your-organization>/terragoat.git
cd terragoat
git status
```
Sample output:
```
git clone https://github.com/bcworkshop/terragoat.git
cd terragoat
git status
Cloning into 'terragoat'...
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 581 (delta 2), reused 0 (delta 0), pack-reused 571
Receiving objects: 100% (581/581), 221.43 KiB | 4.26 MiB/s, done.
Resolving deltas: 100% (269/269), done.

On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

## Run Checkov locally
To demonstrate what kinds of security and compliance errors Prisma Cloud can identify in Terraform templates, start by using Checkov and send the results to the Prisma Cloud platform. 
1. You will first need to add in your API keys you have gotten from Prisma Cloud in earlier section. export it as a variable with the following command (replace the prismaaccesskey & prismasecretkey):
```
export PRISMA_API_URL=https://api.sg.prismacloud.io
export BC_API_KEY=<prismaaccesskey>::<prismasecretkey>
```


1. scan the `s3.tf` in the `aws` directory:
```
checkov -f terraform/aws/s3.tf --repo-id <your-org>/terragoat
```
Check out the findings as part of the scan. The results will show all the failed policies and link to guides explaining the rationale behind each misconfiguration and steps to fix them. Note the output also includes the filename and snippet of code that is misconfigured
![alt text](/resources/checkov_terragoat.png?raw=true)

# Congratulations!
You have now completed the IaC code scanning locally via Checkov! You can now move on to the next section [here](/06-OnboardAWStoPrismaCloud.md)