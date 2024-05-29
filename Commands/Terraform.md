# Terraform Commands

## Initialization and Setup

- terraform init: Initialize a new or existing Terraform configuration.
- terraform validate: Validate the configuration files.
- terraform fmt: Format the configuration files to a canonical format.
- terraform version: Show the current Terraform version.

## Planning and Applying

- terraform plan: Create an execution plan, showing what actions Terraform will take.
- terraform apply: Apply the changes required to reach the desired state of the configuration.
- terraform apply -auto-approve: Apply changes without asking for confirmation.

## State Management

- terraform show: Show the current state or a saved plan.
- terraform state list: List resources in the Terraform state.
- terraform state show [resource]: Show detailed state information about a resource.
- terraform state rm [resource]: Remove a resource from the state.
- terraform state mv [source] [destination]: Move a resource from one location to another within the state.

## Destroying

- terraform destroy: Destroy the Terraform-managed infrastructure.
- terraform destroy -auto-approve: Destroy infrastructure without asking for confirmation.
