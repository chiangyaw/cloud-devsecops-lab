# Cloud DevSecOps Lab
## Integrating Prisma Cloud with VSCode
Integrating VScode (Visual Studio Code) with Prisma Cloud Code Security makes it possible for you to identify misconfigurations before you commit your code, and avoid pull requests that can potentially fail builds due to undetected misconfigurations. Using Checkov, a code analysis tool that scans Infrastructure-as-code (IaC) files from frameworks such as Terraform_plan, CloudFormation, Azure Resource Manager (ARM), Secrets, Serverless, Dockerfile (only code), and Kubernetes on VScode (Visual Studio Code) gives you immediate detection of misconfigurations and inline code fixes.

1. To integrate with Prisma Cloud, you will need the following:
    - Prisma Cloud Access Key & Secret Key generated in the previous steps
    - Python installation (version 3.7 and above)
    - Prisma Cloud API URL (https://app.sg.prismacloud.io)

2. On Prisma Cloud, navigate to Settings > Repositories > Add Repository. 
![alt text](/resources/pc-onboarding-vscode-1.png?raw=true)

3. Click on VScode and another tab should popped up for Checkov. Click Install.
![alt text](/resources/pc-onboarding-vscode-2.png?raw=true)

4. On VScode, click Install.
![alt text](/resources/pc-onboarding-vscode-3.png?raw=true)

5. Configure Checkov plugin on VScode by clicking the Settings icon, and click Extension Settings.
![alt text](/resources/pc-onboarding-vscode-5.png?raw=true)

6. Add the Prisma Cloud application API for Checkov: Prisma Cloud URL. The URL should be ```https://api.sg.prismacloud.io```.

7. Add your Prisma cloud access key and secret key as "<prismaaccesskey>::<prismasecretkey>" for Checkov:Token.
![alt text](/resources/pc-onboarding-vscode-4.png?raw=true)

Then you are done with the Prisma Cloud integration! A Checkov scan runs each time you access a file on VScode.

## Test it out with Terragoat repository
[TerraGoat](https://workshop.bridgecrew.io/terraform/30_module_one/www.github.com/bridgecrewio/terragoat), is a vulnerable-by-design Terraform project, so that you can scan and automate infrastructure code without the added friction of integrating your own code.

1. Create a local copy of the TerraGoat repo, simply by performing a git clone:
```
git clone https://github.com/bridgecrewio/terragoat.git
```

2. Open the ```terragoat``` folder in VSCode, open the file ```terragoat/terraform/aws/rds.tf```. You will notice that Checkov is scanning the file via the status at the bottom of VScode.
![alt text](/resources/pc-checkov-scanning.png?raw=true)

3. Once the scanning is done, you will able to see the highlighted policy misconfiguration inline.
![alt text](/resources/pc-checkov-scanning-2.png?raw=true)

4. To perform a quick fix, you can click on the Quick Fix button, and click on any of the proposed fix. Once you have done so, you will notice that the fix has either been added or removed to the Terraform resource block.
![alt text](/resources/pc-checkov-quickfix-1.png?raw=true)
![alt text](/resources/pc-checkov-quickfix-2.png?raw=true)

# Congratulations!
You have now successfully integrated Checkov and Prisma Cloud into your IDE. With the integration, you will be able to identify any misconfiguration based on the Build policy defined in Prisma Cloud, even before committing the IaC code to your repository. By Shifting Left on security, this helps organization to identify security issues early in the development lifecycle, reducing the overall cost & time for the entire delivery process.

Last but not least, it is always advisable to clean things up after a lab session! Click [here](/14-CleaningUp.md) to proceed.

