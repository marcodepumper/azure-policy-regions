# Azure Policies Repository

This repository stores and manages Azure Policy definitions for controlling resource deployments across your Azure environment. Policies are applied automatically using GitHub Actions workflows.

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