# Pulse Workflow Templates

This repository holds reusable GitHub workflow templates that can be referenced by repositories to build your Docker image, tag it appropriately, push it to GitHub Container Registry, and trigger a deployment in AWS.

To reference and use templates, create a `.yml` file in your `/.github/workflows` folder and copy the example below, and replace `<service_name>` and `<aws_account_id>`. 

This template assumes your `develop` branch is destined for staging, and your `main` branch is destined for production.

```yml
name: Build and Deploy

on:
  push:
    branches:
      - develop
      - main

jobs:
  from-template:
    name: Pulse Template
    uses: pulse-analytics/workflow-templates/.github/workflows/template.yml@main
    with:
      SERVICE_NAME: <service_name>
      AWS_ACCOUNT_ID: <aws_account_id>
```