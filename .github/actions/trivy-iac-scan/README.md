# Scan IaC Code Action

This GitHub Action scans Infrastructure as Code (IaC) using Trivy, a comprehensive security scanner. It helps identify vulnerabilities and misconfigurations in your IaC files.

## Usage

To use this action in your workflow, add the following step:

```yaml
- name: Scan IaC Code
  uses: PA-NIHR-CRN/github-shared-workflows-and-actions/.github/actions/trivy-iac-scan@v1.0.0
  with:
    # Optional inputs
    scan-type: 'config'
    hide-progress: 'false'
    format: 'table'
    exit-code: '0'
    ignore-unfixed: 'true'
    severity: 'CRITICAL,HIGH'
```

## Example Workflow
Here's an example of how to use this action in a complete workflow:
```yaml
name: Scan IaC code
on:
  push:
    branches:
      - main
  pull_request:

jobs:
  scan-iac:
    name: Scan IaC
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Scan IaC Code
        uses: PA-NIHR-CRN/github-shared-workflows-and-actions/.github/actions/trivy-iac-scan@v1.0.0
        with:
          severity: 'CRITICAL,HIGH,MEDIUM'
```

## Notes

- This action uses Trivy under the hood. For more detailed information about Trivy's capabilities and options, please refer to the [Trivy documentation](https://aquasecurity.github.io/trivy/v0.53/docs/coverage/iac/).
- Make sure you have the necessary permissions to run this action in your repository.
- The action currently uses Trivy version 0.20.0. If you need a different version, please open an issue or submit a pull request.

## Contributing
Contributions to improve this action are welcome. Please feel free to submit a Pull Request.