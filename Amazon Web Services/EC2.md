# Introduction

Amazon Elastic Compute Cloud (EC2) is a web service that provides resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers.

# Basic Concepts

1. Instance: A virtual server in Amazon's Elastic Compute Cloud (EC2).
2. AMI (Amazon Machine Image): A template that contains a software configuration (OS, application server, applications).
3. Instance Types: Various configurations of CPU, memory, storage, and networking capacity.
4. Security Groups: Virtual firewalls to control inbound and outbound traffic to instances.
5. Key Pairs: Secure login information for your instances.

# EC2 Instance Lifecycle

1. Launch: Start an instance using a chosen AMI and instance type.
2. Running: The instance is active and can be accessed.
3. Stop: The instance is stopped, and you are not charged for the instance.
4. Terminate: The instance is permanently deleted.
   
# Common EC2 Operations

1. Launching an Instance:

- Navigate to the EC2 Dashboard.
- Click "Launch Instance".
- Choose an Amazon Machine Image (AMI).
- Select an Instance Type.
- Configure Instance Details.
- Add Storage.
- Add Tags (optional).
- Configure Security Group.
- Review and Launch.
- Create or select a key pair for SSH access.
  
2. Connecting to an Instance:
```
ssh -i /path/to/your-key-pair.pem ec2-user@your-instance-public-dns
```
3. Stopping an Instance:

- Navigate to the EC2 Dashboard.
- Select the instance.
- Click "Instance State" > "Stop".
  
4. Terminating an Instance:

- Navigate to the EC2 Dashboard.
- Select the instance.
- Click "Instance State" > "Terminate".
  
# Security Groups

- Create a Security Group:
```
aws ec2 create-security-group --group-name MySecurityGroup --description "My security group"
```

- Add Inbound Rule:
```
aws ec2 authorize-security-group-ingress --group-name MySecurityGroup --protocol tcp --port 22 --cidr 0.0.0.0/0
```

- Add Outbound Rule:
```
aws ec2 authorize-security-group-egress --group-id sg-123abc --protocol tcp --port 80 --cidr 0.0.0.0/0
```

# Key Pairs

- Create a Key Pair:
```
aws ec2 create-key-pair --key-name MyKeyPair --query 'KeyMaterial' --output text > MyKeyPair.pem
chmod 400 MyKeyPair.pem
```

- Import an Existing Key Pair:
```
aws ec2 import-key-pair --key-name MyKeyPair --public-key-material file://MyPublicKey.pub
```

# Instance Types

- General Purpose: Balanced CPU, memory, and networking (e.g., t2.micro, m5.large).
- Compute Optimized: High CPU performance (e.g., c5.large).
- Memory Optimized: High memory performance (e.g., r5.large).
- Storage Optimized: High, sequential read and write access to large datasets (e.g., i3.large).

# Monitoring and Scaling

- CloudWatch: Monitor and manage various metrics.
- Auto Scaling: Automatically adjust the number of instances based on demand.
- Create an Auto Scaling Group:
```
aws autoscaling create-auto-scaling-group --auto-scaling-group-name my-asg --launch-configuration-name my-lc --min-size 1 --max-size 5 --desired-capacity 2 --vpc-zone-identifier subnet-123abc
```

# Elastic IP Addresses

- Allocate an Elastic IP:
```
aws ec2 allocate-address --domain vpc
```

- Associate an Elastic IP:
```
aws ec2 associate-address --instance-id i-1234567890abcdef0 --allocation-id eipalloc-12345678
```

# IAM Roles for EC2

- Create a Role:
```
aws iam create-role --role-name MyEC2Role --assume-role-policy-document file://trust-policy.json
```

- Attach a Policy to a Role:
```
aws iam attach-role-policy --role-name MyEC2Role --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

- Associate an IAM Role with an EC2 Instance:
```
aws ec2 associate-iam-instance-profile --instance-id i-1234567890abcdef0 --iam-instance-profile Name=MyEC2Role
```

# Best Practices

1. Security:

- Use IAM roles instead of embedding access keys.
- Regularly update your security groups and key pairs.
- Use VPC to isolate your instances.
- Encrypt data in transit and at rest.

2. Cost Management:

- Use Auto Scaling to handle load variations.
- Use spot instances for non-critical workloads.
- Regularly review and terminate unused instances.
  
3.Monitoring:

- Set up CloudWatch alarms to monitor instance performance.
- Enable detailed monitoring for critical instances.
  
# Resources

[AWS EC2 Documentation](https://docs.aws.amazon.com/ec2/)

This cheat sheet provides a concise overview of AWS EC2, covering basic concepts, common operations, security, instance types, monitoring, scaling, and best practices. 
