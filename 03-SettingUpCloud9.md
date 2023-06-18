# Cloud DevSecOps Lab
## Setting Up AWS Cloud9
AWS Cloud9 is a cloud-based integrated development environment (IDE) that lets you write, run, and debug your code with just a browser.
1. Create a Cloud9 Environment with the following url:
https://ap-southeast-1.console.aws.amazon.com/cloud9control/home?region=ap-southeast-1#/product
2. Select Create environment.
3. Select the following on Create environment page:
    * Name: PrismaCloud-Workshop
    * Environment Type: New EC2 instance
    * Instance Type: t2.medium
    <Insert Image>
    Leave the rest as default and click Create.
4. On the Environment page, click the environment that you have just created, and click Open in Cloud9.
5. Customize the environment by closing the welcome tab and lower work area, and opening a new terminal tab in the main work area:
![Alt text](/resources/c9before.png?raw=true)
6. Your workspace should now look like this:
![Alt text](/resources/c9after.png?raw=true)
7. Install jq - jq is a command-line tool for parsing JSON. On the Cloud9 CLI, input the following command and Enter. 
```
sudo yum install jq -y
```
8. Start a python environment with the following command
```
python3 -m venv env
source ./env/bin/activate 
```