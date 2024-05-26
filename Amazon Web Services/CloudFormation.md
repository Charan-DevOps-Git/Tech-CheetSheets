# Introduction

AWS CloudFormation provides a common language for you to describe and provision all the infrastructure resources in your cloud environment. It allows you to use a simple text file to model and provision, in an automated and secure manner, all the resources needed for your applications across all regions and accounts.

# Basic Concepts

1. Stack: A collection of AWS resources that you can manage as a single unit.
2. Template: A JSON or YAML text file that describes the resources you need.
3. Change Set: A summary of proposed changes CloudFormation will make to a stack, allowing you to review changes before executing them.
4. Resource: An AWS service or application component included in a CloudFormation template.
5. Parameter: Inputs provided to customize resource properties within the template.
6. Output: Values returned after the stack is created, which can be used as inputs to other stacks or displayed for informational purposes.

# Creating a Stack

1. Using the AWS Management Console:

   - Navigate to the CloudFormation service.
   - Click "Create stack".
   - Choose a template by specifying a template URL or uploading a local file.
   - Configure stack details, including stack name and parameters.
   - Optionally configure stack options (e.g., tags, permissions, rollback configurations).
   - Review the details and click "Create stack".

2. Using AWS CLI:
```
aws cloudformation create-stack --stack-name my-stack --template-body file://template.yaml --parameters ParameterKey=KeyName,ParameterValue=my-key
```

# Updating a Stack

1. Using the AWS Management Console:

   - Navigate to the CloudFormation service.
   - Select the stack to update.
   - Click "Update".
   - Choose a template by specifying a template URL or uploading a new file.
   - Modify parameters as needed.
   - Review the changes and click "Update stack".

2. Using AWS CLI:
```
aws cloudformation update-stack --stack-name my-stack --template-body file://updated-template.yaml --parameters ParameterKey=KeyName,ParameterValue=my-new-key
```

# Deleting a Stack

1. Using the AWS Management Console:

   - Navigate to the CloudFormation service.
   - Select the stack to delete.
   - Click "Delete".
   - Confirm the deletion.

2. Using AWS CLI:
```
aws cloudformation delete-stack --stack-name my-stack
```

# Template Structure

1. YAML Template Example:

```
AWSTemplateFormatVersion: '2010-09-09'
Description: A simple EC2 instance
Parameters:
  InstanceType:
    Description: EC2 instance type
    Type: String
    Default: t2.micro
Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: !Ref InstanceType
      ImageId: ami-0abcdef1234567890
Outputs:
  InstanceId:
    Description: The Instance ID
    Value: !Ref MyEC2Instance
```

2. JSON Template Example:
```
{
    "AWSTemplateFormatVersion": "2010-09-09",
    "Description": "A simple EC2 instance",
    "Parameters": {
        "InstanceType": {
            "Description": "EC2 instance type",
            "Type": "String",
            "Default": "t2.micro"
        }
    },
    "Resources": {
        "MyEC2Instance": {
            "Type": "AWS::EC2::Instance",
            "Properties": {
                "InstanceType": {
                    "Ref": "InstanceType"
                },
                "ImageId": "ami-0abcdef1234567890"
            }
        }
    },
    "Outputs": {
        "InstanceId": {
            "Description": "The Instance ID",
            "Value": {
                "Ref": "MyEC2Instance"
            }
        }
    }
}
```

# Key Elements

1. Parameters: Define values to pass to your template at runtime.
```
Parameters:
  KeyName:
    Description: Name of an existing EC2 KeyPair
    Type: AWS::EC2::KeyPair::KeyName
    ConstraintDescription: must be the name of an existing EC2 KeyPair.
```

2. Mappings: Create fixed values based on region, account, or other keys.
```
Mappings:
  RegionMap:
    us-east-1:
      "32": "ami-6411e20d"
      "64": "ami-7a11e213"
    us-west-1:
      "32": "ami-c9c7978c"
      "64": "ami-cfc7978a"
```

3. Resources: Declare the AWS resources you want to create.
```
Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.micro
      ImageId: ami-0abcdef1234567890
```

4. Outputs: Return values from your stack.
```
Outputs:
  InstanceId:
    Description: The Instance ID
    Value: !Ref MyEC2Instance
```

5. Conditions: Control the creation of resources and outputs based on conditions.
```
Conditions:
  CreateProdResources: !Equals [!Ref EnvironmentType, prod]
```

# Stack Operations

1. Creating a Change Set:

- AWS Management Console:
  - Navigate to the CloudFormation service.
  - Select the stack.
  - Click "Create change set".

- AWS CLI:
```
aws cloudformation create-change-set --stack-name my-stack --template-body file://template.yaml --change-set-name my-change-set
```

2. Executing a Change Set:

- AWS Management Console:
  - Navigate to the CloudFormation service.
  - Select the stack and the change set.
  - Click "Execute".

- AWS CLI:
```
aws cloudformation execute-change-set --change-set-name my-change-set --stack-name my-stack
```

3. Viewing Stack Events:

- AWS Management Console:
  - Navigate to the CloudFormation service.
  - Select the stack.
  - Click "Events".

- AWS CLI:
```
aws cloudformation describe-stack-events --stack-name my-stack
```

# Best Practices

1. Modular Templates:

- Break down complex templates into smaller, reusable templates.
- Use the AWS::CloudFormation::Stack resource to reference other templates.

2. Version Control:

- Store your templates in a version control system like Git.
- Use versioning to manage template changes.

3. Change Sets:

- Always use change sets to review changes before applying them.
- Helps prevent unintended modifications and disruptions.

4. Parameters and Metadata:

- Use parameters to customize your templates.
- Provide metadata and descriptions for clarity.

5. Outputs and Exports:

- Use outputs to export values from one stack and import them into another.
- Facilitates resource sharing across stacks.

6. Logging and Monitoring:

- Enable CloudTrail logging for CloudFormation.
- Use CloudWatch to monitor stack creation and updates.

# Resources

[AWS CloudFormation Documentation](https://docs.aws.amazon.com/cloudformation/)

This cheat sheet provides a comprehensive overview of AWS CloudFormation, covering basic concepts, creating and managing stacks, template structure, key elements, stack operations, best practices, and resources. 
