# Azure Policies Repository

This repository stores and manages Azure Policy definitions for controlling resource deployments across your Azure environment. The policies are applied automatically using GitHub Actions workflows.

## Repository Structure

- **`policies/`**: Contains Azure Policy definition files in JSON format.
- **`.github/workflows/`**: Contains GitHub Actions workflows for applying policies.

## Adding New Policies

1. Create a new JSON file in the `policies/` directory.
2. Define your policy rules in the JSON file.
3. Commit and push your changes to the `main` branch.

The GitHub Actions workflow will automatically create and assign the new policy upon each push to the `main` branch.

## Policy JSON Format

Each policy JSON file should follow the Azure Policy definition schema. Here’s a basic example of a policy definition:

```json
{
  "properties": {
    "displayName": "Policy Display Name",
    "description": "Description of what this policy does.",
    "policyRule": {
      "if": {
        "field": "someField",
        "equals": "someValue"
      },
      "then": {
        "effect": "deny"
      }
    },
    "metadata": {
      "version": "1.0.0",
      "category": "General"
    }
  }
}
Example Policies
Deny Virtual Machine Deployments
This policy denies the creation of any virtual machines:

json
Copy code
{
  "properties": {
    "displayName": "Deny Virtual Machine Deployments",
    "description": "This policy denies the creation of any virtual machines.",
    "policyRule": {
      "if": {
        "field": "type",
        "equals": "Microsoft.Compute/virtualMachines"
      },
      "then": {
        "effect": "deny"
      }
    },
    "metadata": {
      "version": "1.0.0",
      "category": "Compute"
    }
  }
}

GitHub Actions Workflow
The workflow defined in .github/workflows/apply-policies.yml will:

Checkout the repository.
Login to Azure using credentials stored in GitHub Secrets.
Create and assign policies defined in the policies/ directory.
GitHub Secrets
Ensure the following secrets are configured in your GitHub repository settings:

AZURE_CREDENTIALS: JSON credentials for Azure Service Principal.
AZURE_SUBSCRIPTION_ID: Your Azure Subscription ID.
Contributing
To contribute to this repository, follow these steps:

Fork the repository.
Create a new branch.
Add or modify policy JSON files.
Create a pull request describing your changes.
License
This repository is licensed under the MIT License.

markdown
Copy code

### Key Sections in the README.md:

- **Overview**: A brief description of the repository and its purpose.
- **Repository Structure**: Explains the organization of files in the repository.
- **Adding New Policies**: Instructions for adding and applying new policies.
- **Policy JSON Format**: A template for creating policy definitions.
- **Example Policies**: Provides a specific example of a policy, in this case, one that denies VM deployments.
- **GitHub Actions Workflow**: Details on what the GitHub Actions workflow does.
- **GitHub Secrets**: Information on required secrets for the workflow.
- **Contributing**: Guidelines for contributing to the repository.
- **License**: Licensing information.