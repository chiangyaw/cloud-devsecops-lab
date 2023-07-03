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

### Install Yor.io
We will also be using Yor, an open-srouce tool from Prisma Cloud (formally bridgecrew) that helps add informative and consistent tags across infrastructure as code (IaC) frameworks.
```
wget -q -O - https://github.com/bridgecrewio/yor/releases/download/0.1.62/yor-0.1.62-linux-amd64.tar.gz | sudo tar -xvz -C /usr/bin
```

### Connecting your Cloud9 IDE to GitHub
In the following lab, we will need to be able to update your GitHub repository later through the Cloud9 IDE. Create a personal GitHub account and login to the account before proceeding on this section. Click [here](https://github.com/signup)
1. Generate a RSA Key Pair with the following command. just keep everything else as default by click "Enter" throughout the process.
```
ssh-keygen -t rsa
```
![alt text](/resources/cloud9-generate-key.png?raw=true)

2. Copy the Public Key from the file:
```
cat /home/ec2-user/.ssh/id_rsa.pub
```

3. Navigate to the GitHub portal, click the top right icon > Settings.
![alt text](/resources/github-settings.png?raw=true)

4. Click on "SSH and GPG Keys" and "New SSH keys".
![alt text](/resources/github-create-ssh-keys.png?raw=true)

5. Input a title (such as "cloud9-key") and paste in the Public Key. Click "Add SSH Key". You might be prompted to type in your password again, just type and proceed.
![alt text](/resources/github-create-ssh-key-2.png?raw=true)

6. Go back to the Cloud9 IDE terminal, start your ssh-agent in the background and add the ssh key into your ssh-agent:
```
eval $(ssh-agent -s)
ssh-add /home/ec2-user/.ssh/id_rsa
```

7. Input your GitHub username & email address as part of the git config:
```
git config --global user.name <Your Username>
git config --global user.email <you@example.com>
```

Once you are done setting up your Cloud9 IDE, you can move on to the next section [here](/03-PreparingTerraformCloud.md)