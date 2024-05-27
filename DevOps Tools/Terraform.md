## Basic Concepts

- **Provider**: A plugin that interacts with cloud providers (like AWS, Azure, Google Cloud).
- **Resource**: A component of your infrastructure (like an EC2 instance, S3 bucket).
- **Module**: A container for multiple resources used together.
- **State**: The information about your infrastructure managed by Terraform.
- **Plan**: The execution plan created by Terraform showing what actions will be taken.

## Common Commands

### Terraform Installation

#### On Ubuntu
```
sudo apt-get update
sudo apt-get install -y gnupg software-properties-common curl
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
sudo apt-get update
sudo apt-get install terraform
```

## Terraform Version
```
terraform version
```

## Terraform Help
```
terraform --help
```

# Working with Terraform

## Initialize a Terraform Working Directory
```
terraform init
```

## Validate the Configuration Files
```
terraform validate
```

## Format the Configuration Files
```
terraform fmt
```

## Create an Execution Plan
```
terraform plan
```

## Apply the Changes Required to Reach the Desired State of the Configuration
```
terraform apply
```

## Destroy the Terraform-managed Infrastructure
```
terraform destroy
```

## Show the Current State
```
terraform show
```

## List All Resources in the State
```
terraform state list
```

## Refresh the State
```
terraform refresh
```

# Configuration Files

## Main Configuration File
```
provider "aws" {
  region = "us-west-2"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```

## Variables
```
variable "instance_type" {
  description = "Type of instance to use"
  default     = "t2.micro"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = var.instance_type
}
```

## Outputs
```
output "instance_id" {
  description = "The ID of the EC2 instance"
  value       = aws_instance.example.id
}
```

## Local Values
```
locals {
  instance_name = "example-instance"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
  tags = {
    Name = local.instance_name
  }
}
```

# State Management

## Move a Resource to a Different State
```
terraform state mv <source> <destination>
# Example:
terraform state mv aws_instance.example aws_instance.new_example
```

## Remove a Resource from the State
```
terraform state rm <resource>
# Example:
terraform state rm aws_instance.example
```

## Import an Existing Resource into the State
```
terraform import <resource> <id>
# Example:
terraform import aws_instance.example i-1234567890abcdef0
```

# Terraform Modules

## Create a Module

1. Create a directory for the module (e.g., modules/my_module).
2. Add configuration files to the module directory (e.g., main.tf, variables.tf, outputs.tf).

## Use a Module
```
module "my_module" {
  source = "./modules/my_module"

  # Module-specific variables
  instance_type = "t2.micro"
}
```

# Terraform Backend

## Configure a Backend
```
terraform {
  backend "s3" {
    bucket = "my-terraform-state"
    key    = "path/to/my/key"
    region = "us-west-2"
  }
}
```

## Initialize the Backend
```
terraform init
```

# Useful Terraform CLI Commands

## Taint a Resource
```
terraform taint <resource>
# Example:
terraform taint aws_instance.example
```

## Untaint a Resource
```
terraform untaint <resource>
# Example:
terraform untaint aws_instance.example
```

## Graph the Dependency Tree
```
terraform graph | dot -Tpng > graph.png
```

# Resources

[Terraform Documentation](https://developer.hashicorp.com/terraform/docs)

This cheat sheet provides a comprehensive overview of Terraform, covering basic concepts, common commands, configuration files, state management, modules, backend configuration, and useful CLI commands. 
