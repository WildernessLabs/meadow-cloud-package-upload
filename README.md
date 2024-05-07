# Upload Meadow MPAK Action

This GitHub Action facilitates the uploading of Meadow MPAKs to the cloud, allowing for their storage and subsequent deployment. It is suitable for workflows that manage package distribution within an organization's Meadow cloud environment.

## Description

The "Upload Meadow MPAK" action streamlines the process of uploading Meadow MPAK files to the cloud directly from GitHub Actions. This can be integrated into CI/CD pipelines to automate package management as part of software development and deployment routines.

## Inputs

### `organization_id`
**Required** The identifier for your organization. This is used to associate the uploaded package with your specific organization in Meadow's cloud.

### `api_key`
**Required** The API key for authenticating with Meadow's cloud services. It is crucial to protect this key to maintain the security of your data.

### `host`
**Required** The API URL for the Meadow cloud services. This must be specified to direct the action to the correct Meadow cloud endpoint.

## How to Use

Here's an example of how to set up this action in your GitHub workflow:

```yaml
name: Upload Meadow MPAK Workflow

on:
  push:
    branches:
      - main

jobs:
  upload:
    runs-on: ubuntu-latest
    steps:
      - name: Upload Meadow MPAK
        uses: WildernessLabs/meadow-cloud-package-upload@main
        with:
          organization_id: '123456789'
          api_key: ${{ secrets.API_KEY }}
          host: 'https://staging.meadowcloud.dev'
