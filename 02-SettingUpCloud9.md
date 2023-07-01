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
![alt text](/resources/aws-create-cloud9.png?raw=true)
    Leave the rest as default and click Create.
4. On the Environment page, click the environment that you have just created, and click Open in Cloud9.
5. Understanding the IDE you have created. We have file tab on top where you can make changes to your code and we have a terminal at the bottom to run CLI commands.
![alt text](/resources/cloud9-intro.png?raw=true)

7. Install jq - jq is a command-line tool for parsing JSON. On the Cloud9 terminal, input the following command and Enter. 
```
sudo yum install jq -y
```
8. Start a python environment with the following command
```
python3 -m venv env
source ./env/bin/activate 
```

### Checkov
In this tutorial, we will be using [Checkov](https://www.checkov.io/). Install Checkov in your Cloud9 CLI with pip:
```
pip3 install checkov
```

Once you are done setting up your Cloud9 IDE, you can move on to the next section [here](/03-PreparingTerraformCloud.md)