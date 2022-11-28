# Pulse Workflow Templates

This repository holds reusable GitHub workflow templates that can be referenced by repositories to build your Docker image, tag it appropriately, push it to GitHub Container Registry, and trigger a deployment in AWS.

To reference and use templates, create a `.yml` file in your `/.github/workflows` folder. You can copy the examples below -- be sure to replace `<service_name>` and `<aws_account_id>`. 

### Staging
```yml
name: Build, Deploy Staging

on:
  push:
    branches:
      - develop

jobs:
  from-template:
    name: Staging Template
    uses: pulse-analytics/workflow-templates/.github/workflows/staging.yml@main
    with:
      SERVICE_NAME: <service_name>
      AWS_ACCOUNT_ID: <aws_account_id>
```

### Production
```yml
name: Build, Deploy Production

on:
  release:
    types: 
      - published

jobs:
  from-template:
    name: Production Template
    uses: pulse-analytics/workflow-templates/.github/workflows/production.yml@main
    with:
      SERVICE_NAME: <service_name>
      AWS_ACCOUNT_ID: <aws_account_id>
```