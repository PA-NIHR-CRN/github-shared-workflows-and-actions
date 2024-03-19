A collection of reusable workflows and actions that can be consumed by GitHub Actions in other repositories within the organisation.

  

## Usage

  

Workflows can be called from other workflows, whether within the same or a different repository. Given this repository is public, other repositories within the NIHR GitHub organisation will be able to call these workflows.

  

To call then, in the workflow file in your repository, add the following:


```yml

name: My Workflow
on: push

jobs:
run-workflow:
- name: Run a shared workflow
  uses: PA-NIHR-CRN/github-shared-workflows-and-actions/.github/workflows/validate-terraform.yml@v1.0.0

```

  

> Be sure to check if the workflow requires any inputs, environment variables, or secrets.

  

## Workflows

 

[Validate Terraform](.github/workflows/validate-terraform.yml) : Runs a series of validation steps on Terraform files to check adherence to formatting standards, linting rules, and security best practices. 

Example usage:


```yml

name: My Workflow
on: push

jobs:
  validate-terraform:
	uses: PA-NIHR-CRN/github-shared-workflows-and-actions/.github/workflows/validate-terraform.yml@v1.0.0
	secrets: inherit
	with:
	  path: terraform

```