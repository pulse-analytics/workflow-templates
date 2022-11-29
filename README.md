# Pulse Workflow Templates

This repository holds reusable GitHub workflow templates that can be referenced by repositories to build your Docker image, tag it appropriately, push it to GitHub Container Registry, and trigger a deployment in AWS.

To reference and use templates, create a `.yml` file in your `/.github/workflows` folder. You can copy/reference the examples below, just be sure to modify the required inputs under "with" to what is appropriate for your repository. 

### Demo Example
```yml
name: Build, Deploy Demo

on:
  push:
    branches:
      - demo

jobs:
  from-template:
    name: Main Template
    uses: pulse-analytics/workflow-templates/.github/workflows/production.yml@main
    with:
      SERVICE_NAME: <service_name>
      AWS_ACCOUNT_ID: <aws_account_id>
      IMAGE_TAG: demo
      ENVIRONMENT: demo
    secrets:
      NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
```

### Staging Example
```yml
name: Build, Deploy Staging

on:
  push:
    branches:
      - develop

jobs:
  from-template:
    name: Main Template
    uses: pulse-analytics/workflow-templates/.github/workflows/production.yml@main
    with:
      SERVICE_NAME: <service_name>
      AWS_ACCOUNT_ID: <aws_account_id>
      IMAGE_TAG: latest
      ENVIRONMENT: staging
    secrets:
      NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
```

### Production Example
```yml
name: Build, Deploy Production

on:
  release:
    types: 
      - published

jobs:
  from-template:
    name: Main Template
    uses: pulse-analytics/workflow-templates/.github/workflows/production.yml@main
    with:
      SERVICE_NAME: <service_name>
      AWS_ACCOUNT_ID: <aws_account_id>
      IMAGE_TAG: production
      ENVIRONMENT: production
    secrets:
      NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
```