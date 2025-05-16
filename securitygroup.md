# How to Create an Amazon EC2 Security Group

## Prerequisites
- An AWS account
- Access to AWS Management Console
- IAM permissions to create and manage security groups
- VPC ID (if not using default VPC)

## Steps to Create a Security Group

### Method 1: Using AWS Management Console

1. Sign in to the AWS Management Console
2. Navigate to the EC2 Dashboard:
   - Click on "Services" at the top
   - Select "EC2" under Compute

3. Find Security Groups:
   - In the left navigation pane
   - Click "Security Groups" under "Network & Security"

4. Create New Security Group:
   - Click "Create security group"
   - Enter basic details:
     - Security group name
     - Description (mandatory)
     - VPC selection

5. Configure Inbound Rules:
   - Click "Add rule"
   - Select the protocol (TCP, UDP, etc.)
   - Choose port range
   - Specify source:
     - Custom IP
     - Anywhere (0.0.0.0/0)
     - My IP
     - Security group
   - Add description (recommended)

6. Configure Outbound Rules:
   - Default: Allow all outbound traffic
   - Modify if needed for your use case

7. Add Tags (Optional):
   - Click "Add tag"
   - Enter key-value pairs

8. Click "Create security group"

### Method 2: Using AWS CLI

1. Create basic security group:
```bash
aws ec2 create-security-group \
    --group-name "your-security-group-name" \
    --description "Your security group description" \
    --vpc-id vpc-xxxxxxxx
```

### Add Inbound Rule

1. Create basic security group:
```bash
aws ec2 authorize-security-group-ingress \
    --group-id sg-xxxxxxxx \
    --protocol tcp \
    --port 80 \
    --cidr 0.0.0.0/0
