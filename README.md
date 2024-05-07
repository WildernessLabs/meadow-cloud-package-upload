# Build and Upload Meadow MPAK Action

This GitHub Action is designed for the complete process of building, testing, and uploading Meadow MPAK files to the cloud. It provides an integrated solution for managing the deployment pipeline of Meadow-based applications.

## Description

The "Deploy and Upload Meadow MPAK" action combines building, testing, packaging, and uploading processes into a single workflow. This ensures that your Meadow applications are compiled, tested, and deployed efficiently and consistently across your development team.

## Inputs

### `organization_id`
**Required** The identifier for your organization within Meadow's cloud services.

### `api_key`
**Required** The API key for authenticating with Meadow's cloud services.

### `os_version`
Optional. Specifies the operating system version for the Meadow device, allowing specific firmware versions to be targeted.

### `cli_version`
Optional. Specifies the version of the Meadow Command Line Interface (CLI) tool to use.

### `configs`
Optional. A JSON string of key-value pairs for replacing placeholders in `*.yaml` configuration files. Defaults to an empty object (`{}`).

### `host`
Optional. The API URL for the Meadow cloud services. Allows the action to interface with different Meadow cloud environments.

## How to Use

Below is an example of how to implement this action in a GitHub workflow:

```yaml
name: Continuous Deployment of Meadow MPAK

on:
  push:
    branches:
      - main

jobs:
    upload:
    runs-on: ubuntu-latest
    steps:
      - name: Build and Upload Meadow MPAK Action
        uses: WildernessLabs/meadow-cloud-package-upload@main
        with:
          organization_id: '123456789'
          api_key: ${{ secrets.API_KEY }}
          host: 'https://staging.meadowcloud.dev' # Optional, set this to the host url if required
          cli_version: "2.0.30" # Optional, set this to the CLI version if required
          os_version: "1.10.0.0" # Optional, set this to the OS version if required        
          configs : '{"CONFIG_SSID": "${{ secrets.CONFIG_SSID }}", "CONFIG_PASSWORD": "${{ secrets.CONFIG_PASSWORD }}"}' # Optional, set this to a matching token to replaced within your *.yaml files if required
