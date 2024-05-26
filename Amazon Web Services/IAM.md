# Introduction

AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS services and resources. Using IAM, you can create and manage AWS users and groups and use permissions to allow and deny their access to AWS resources.

# Basic Concepts

1. User: An entity that represents a person or service that interacts with AWS.
2. Group: A collection of users managed as a single entity.
3. Policy: A document that defines permissions, written in JSON format.
4. Role: An IAM identity with permissions policies that can be assumed by trusted entities, such as an AWS service or an external user.
5. Identity Provider: A service that manages user identities outside of AWS (e.g., corporate directory, web identity provider).

# Creating IAM Users

1. Using the AWS Management Console:

    - Navigate to the IAM service.
    - Click "Users" > "Add user".
    - Enter a username.
    - Select the type of access: "Programmatic access" for CLI/SDK, "AWS Management Console access" for web access.
    - Set permissions by attaching policies directly, adding the user to a group, or copying permissions from another user.
    - Optionally add tags to the user.
    - Review and create the user.

2. Using AWS CLI:
```
aws iam create-user --user-name myuser
aws iam create-login-profile --user-name myuser --password MySecurePassword123!
```

# Managing Permissions with Policies

1. Inline Policy Example:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Resource": "arn:aws:s3:::example_bucket"
        }
    ]
}
```

2. Attaching Managed Policies to a User:

- AWS Management Console:
  - Navigate to the IAM service.
  - Click "Users", select the user, and then "Add permissions".
  - Attach an existing policy or create a new policy.

- AWS CLI:
```
aws iam attach-user-policy --user-name myuser --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

3. Creating and Attaching Custom Policies:

- AWS Management Console:
  - Navigate to the IAM service.
  - Click "Policies" > "Create policy".
  - Use the visual editor or JSON editor to create the policy.
  - Review and create the policy.
  - Attach the policy to users, groups, or roles.
- AWS CLI:
```
aws iam create-policy --policy-name MyCustomPolicy --policy-document file://policy.json
aws iam attach-user-policy --user-name myuser --policy-arn arn:aws:iam::account-id:policy/MyCustomPolicy
```

# Creating IAM Groups

1. Using the AWS Management Console:

   - Navigate to the IAM service.
   - Click "Groups" > "Create New Group".
   - Enter a group name.
   - Attach policies to the group.
   - Add users to the group.

2. Using AWS CLI:
```
aws iam create-group --group-name mygroup
aws iam add-user-to-group --user-name myuser --group-name mygroup
```

# Creating IAM Roles

1. Using the AWS Management Console:

   - Navigate to the IAM service.
   - Click "Roles" > "Create role".
   - Select the trusted entity (e.g., AWS service, another AWS account).
   - Attach policies to the role.
   - Optionally add tags to the role.
   - Review and create the role.

2. Using AWS CLI:
```
aws iam create-role --role-name myrole --assume-role-policy-document file://trust-policy.json
aws iam attach-role-policy --role-name myrole --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

# Assume Role Policy Document Example

1. Trust Policy for an AWS Service:
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "ec2.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```

2. Assuming a Role Using AWS CLI:
```
aws sts assume-role --role-arn arn:aws:iam::account-id:role/myrole --role-session-name MySession
```

# Identity Providers

1. Adding an Identity Provider:

- AWS Management Console:
  - Navigate to the IAM service.
  - Click "Identity providers" > "Add provider".
  - Select the provider type (e.g., SAML, OIDC).
  - Configure the provider details.

- AWS CLI:
```
aws iam create-saml-provider --name MyProvider --saml-metadata-document file://saml-metadata.xml
```

# Security Best Practices

1. Enable MFA (Multi-Factor Authentication):

- Require MFA for users and roles to enhance security.
- AWS Management Console:
  - Navigate to the IAM service.
  - Click "Users", select the user, and then "Security credentials".
  - Click "Manage MFA" and follow the setup steps.

- AWS CLI:
```
aws iam create-virtual-mfa-device --virtual-mfa-device-name mymfa --outfile /path/to/mfa-qrcode.png
aws iam enable-mfa-device --user-name myuser --serial-number arn:aws:iam::account-id:mfa/myuser --authentication-code-1 123456 --authentication-code-2 654321
```

2. Rotate Credentials Regularly:

- Regularly rotate passwords and access keys for enhanced security.

3. Use Least Privilege Principle:

- Grant only the permissions necessary for users and roles to perform their tasks.

4. Monitor and Audit IAM Activity:

- Use AWS CloudTrail to monitor and log IAM activity.
- Regularly review IAM policies and permissions.


# Monitoring and Logging

1. CloudTrail:
- AWS CloudTrail provides logging and monitoring for AWS account activity, including actions taken through the IAM service.
- AWS Management Console:
  - Navigate to the CloudTrail service.
  - Enable CloudTrail for your account.
  - Configure trail settings and create the trail.
- AWS CLI:
```
aws cloudtrail create-trail --name mytrail --s3-bucket-name mytrailbucket
aws cloudtrail start-logging --name mytrail
```

# Resources

[AWS IAM Documentation](https://docs.aws.amazon.com/iam/)

This cheat sheet provides a comprehensive overview of AWS IAM, covering basic concepts, creating and managing users, groups, roles, policies, security best practices, and monitoring.
