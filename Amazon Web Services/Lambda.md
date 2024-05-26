# Introduction

AWS Lambda is a serverless compute service that lets you run code without provisioning or managing servers. You pay only for the compute time you consume.

# Basic Concepts

1. Function: A piece of code that runs in AWS Lambda.
2. Event Source: An AWS service or a custom application that publishes events to trigger the Lambda function.
3. Trigger: A resource or configuration that causes a Lambda function to execute.
4. Execution Role: An AWS Identity and Access Management (IAM) role that grants the Lambda function permissions to use other AWS services.
5. Environment Variables: Configuration settings that can be passed to your Lambda function.

# Creating a Lambda Function

1. Using the AWS Management Console:

- Navigate to the Lambda service.
- Click "Create function".
- Choose "Author from scratch", "Use a blueprint", or "Browse serverless app repository".
- Configure the function name, runtime (e.g., Python, Node.js), and execution role.
- Click "Create function".

2. Using AWS CLI:
```
aws lambda create-function --function-name my-function \
  --runtime python3.8 \
  --role arn:aws:iam::account-id:role/execution-role \
  --handler lambda_function.lambda_handler \
  --zip-file fileb://function.zip
```

# Writing a Lambda Function

1. Basic Lambda Function in Python:
```
def lambda_handler(event, context):
    return {
        'statusCode': 200,
        'body': 'Hello, World!'
    }
```

2. Basic Lambda Function in Node.js:

```
exports.handler = async (event) => {
    return {
        statusCode: 200,
        body: 'Hello, World!'
    };
};
```

# Deploying Code Updates

1. Update Function Code Using AWS CLI:
```
aws lambda update-function-code --function-name my-function --zip-file fileb://function.zip
```
2.Update Function Code Using AWS Management Console:

- Navigate to the Lambda function.
- Click "Upload from" and select ".zip file" or "Amazon S3".
- Upload the new code and click "Save".

# Configuring Triggers

1. S3 Trigger:

- Navigate to the Lambda function.
- Click "Add trigger".
- Select "S3".
- Configure the bucket and event type (e.g., object created).
- Click "Add".

2. API Gateway Trigger:

- Navigate to the Lambda function.
- Click "Add trigger".
- Select "API Gateway".
- Configure the API Gateway details (e.g., new or existing API).
- Click "Add".

3. CloudWatch Events Trigger:

- Navigate to the Lambda function.
- Click "Add trigger".
- Select "CloudWatch Events".
- Configure the rule details (e.g., schedule expression).
- Click "Add".

# Managing Permissions

1. Creating an Execution Role:

- AWS Management Console:

- Navigate to the IAM service.
- Click "Roles" > "Create role".
- Select "AWS service" and "Lambda".
- Attach policies (e.g., AWSLambdaBasicExecutionRole).
- Click "Next" and provide a role name.
- Click "Create role".

- AWS CLI:
```
aws iam create-role --role-name lambda-execution-role --assume-role-policy-document file://trust-policy.json
aws iam attach-role-policy --role-name lambda-execution-role --policy-arn arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole
```

2. Policy Document Example (trust-policy.json):
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "lambda.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```

# Environment Variables

- Setting Environment Variables:
```
aws lambda update-function-configuration --function-name my-function --environment Variables={KEY1=VALUE1,KEY2=VALUE2}
```

- Accessing Environment Variables in Code:

- Python:
```
import os
def lambda_handler(event, context):
    value1 = os.getenv('KEY1')
```
- Node.js:
```
exports.handler = async (event) => {
    const value1 = process.env.KEY1;
};
```

# Monitoring and Logging

1. CloudWatch Logs:

- Lambda automatically integrates with CloudWatch Logs.
- View logs in the CloudWatch console under "Log groups".

2. Custom Metrics:

- Publish custom metrics from within your Lambda function using the AWS SDK.
- Python example:
```
import boto3
cloudwatch = boto3.client('cloudwatch')

def lambda_handler(event, context):
    cloudwatch.put_metric_data(
        Namespace='MyNamespace',
        MetricData=[
            {
                'MetricName': 'MyMetric',
                'Value': 1.0
            }
        ]
    )
```

3. AWS X-Ray:

- Enable AWS X-Ray for tracing Lambda functions.
- Add the AWSXRayDaemonWriteAccess policy to your Lambda execution role.
- Use the AWS X-Ray SDK to instrument your Lambda function.

# Best Practices

1. Security:

- Use IAM roles with the least privilege.
- Encrypt environment variables.
- Use VPC for Lambda functions that need to access private resources.

2. Performance:

- Optimize function code and dependencies.
- Use appropriate memory and timeout settings.
- Enable provisioned concurrency for latency-sensitive applications.

3. Cost Management:

- Monitor function usage and set CloudWatch alarms for anomalies.
- Use Lambda@Edge for latency-sensitive content delivery.
- Avoid infinite loops in code to prevent excessive billing.

# Resources

[AWS Lambda Documentation](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)

This cheat sheet provides a comprehensive overview of AWS Lambda, covering basic concepts, creating and deploying functions, configuring triggers, managing permissions, environment variables, monitoring, logging, and best practices. 
