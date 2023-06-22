# Cloud DevSecOps Lab
## Preparing Terraform Cloud
Terraform Cloud (TFC) is a self-service SaaS platform that extends the capabilities of the open source Terraform CLI. It’s free for basic usage, but we’ll be leveraging advanced features, such as Sentinel, that will require a paid subscription or trial. Sign up for Terraform Cloud [here](https://app.terraform.io/signup) and log in using the Cloud9 CLI.
1. Once you have created the Terraform Cloud account, stay logged in on the browser. Login to Terraform Cloud on the Cloud9 CLI:
```
terraform login
```
2. Upon logging in to Terraform Cloud on the Cloud9 CLI, you will be prompted to create a token via the web link below. Click on the web link, and you will be redirected to the browser to create a user token. Leave everything as default and click Generate token.
```
https://app.terraform.io/app/settings/tokens?source=terraform-login
```

![Alt text](/resources/create-user-token-terraform.png?raw=true)

3. Copy the token generated on the Terraform Cloud portal, and paste it into the Cloud9 CLI. Once done, you should be logged into the Terraform Cloud on the Cloud9 CLI:

![Alt text](/resources/terraform-login-cli.png?raw=true)

Once you are done setting up your Terraform Cloud environment, you can move on to the next section [here](/04-SettingUpPrismaCloud.md)