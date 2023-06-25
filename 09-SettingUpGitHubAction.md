# Cloud DevSecOps Lab
## Setting Up GitHub Action with Yor
Yor is an open-source tool that automatically tags infrastructure as code (IaC) templates with attribution and ownership details, unique IDs that get carried across to cloud resources, and any other need-to-know information. It can run locally, as a pre-commit hook, or in a CI/CD pipeline.

For drift detection, the important tag is yor_trace. It’s a unique identifier that helps us trace from a cloud runtime configuration back to the IaC that provisioned it. To do that we need 3 elements:
- Yor automated tagging (this page)
- Integration with the VCS that stores the IaC (Adding Repository to PRisma Cloud, done in the previous section)
- Cloud integration (Onboarding your AWS account to Prisma Cloud, done in the previous section)

### Adding the Yor GitHub Action
1. In your GitHub repository, click "Add file" > "Create new file". 
![alt text](/resources/github-create-action-1.png?raw=true)

2. Set the path to ```.github/workflows/yor.yaml```. Add the following code:
```
name: IaC trace

on:
  push:
  pull_request:
  workflow_dispatch:

jobs:
  yor:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        name: Checkout repo
        with:
          fetch-depth: 0
          ref: ${{ github.head_ref }}
      - name: Run yor action and commit
        uses: bridgecrewio/yor-action@main
```
Click "Commit Changes" and Save. 

3. Navigate to Settings > Actions > General, under Workflow permissions, change to "Read and write permissions" and click "Save".
![alt text](/resources/github-actions-permission.png?raw=true)


This will run Yor to automatically tag your IaC resources every time you perform a push or pull request. The result will look something like this:

![alt text](/resources/github-yor-tags.png?raw=true)

The ```yor_trace``` tag will be used to track drift in your resources. 

Once completed, move on to the next section [here](/10-TestingPullRequest.md)