# How to Create an Amazon EC2 Instance

## Prerequisites
- An AWS account
- Access to AWS Management Console
- IAM permissions to create EC2 instances
- Key pair (for SSH access)
- Security group
- VPC and subnet information

## Steps to Create an EC2 Instance

### Method 1: Using AWS Management Console

1. Sign in to the AWS Management Console
2. Navigate to EC2:
   - Click on "Services"
   - Select "EC2" under Compute

3. Launch Instance:
   - Click "Launch Instance"
   - Click "Launch Instance" (from the dropdown)

4. Name and Tags:
   - Enter a name for your instance
   - Add additional tags if needed

5. Choose AMI (Amazon Machine Image):
   - Select an operating system
   - Common options:
     - Amazon Linux 2023
     - Ubuntu
     - Windows Server
   - Choose between:
     - Quick Start
     - My AMIs
     - AWS Marketplace
     - Community AMIs

6. Choose Instance Type:
   - Select based on needs:
     - t2.micro (free tier eligible)
     - t3.small
     - etc.
   - Consider:
     - vCPUs
     - Memory
     - Network Performance

7. Key Pair:
   - Select existing key pair
   - Create new key pair
   - Proceed without key pair (not recommended)

8. Network Settings:
   - Select VPC
   - Choose subnet
   - Auto-assign public IP
   - Select security group(s)

9. Configure Storage:
   - Set root volume size
   - Add additional volumes if needed
   - Choose volume type:
     - gp2/gp3 (General Purpose SSD)
     - io1/io2 (Provisioned IOPS SSD)
     - st1 (Throughput Optimized HDD)
     - sc1 (Cold HDD)

10. Advanced Details (Optional):
    - IAM role
    - User data
    - Monitoring options
    - Shutdown behavior
    - Termination protection

11. Review and Launch:
    - Verify all settings
    - Click "Launch instance"

### Method 2: Using AWS CLI

1. Basic instance launch:
```bash
aws ec2 run-instances \
    --image-id ami-xxxxx \
    --count 1 \
    --instance-type t2.micro \
    --key-name your-key-pair \
    --security-group-ids sg-xxxxx \
    --subnet-id subnet-xxxxx   
```

2. Launch with additional options   
```bash
aws ec2 run-instances \
    --image-id ami-xxxxx \
    --count 1 \
    --instance-type t2.micro \
    --key-name your-key-pair \
    --security-group-ids sg-xxxxx \
    --subnet-id subnet-xxxxx \
    --block-device-mappings "[{\"DeviceName\":\"/dev/xvda\",\"Ebs\":{\"VolumeSize\":30,\"VolumeType\":\"gp3\"}}]" \
    --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=my-instance}]' \
    --user-data file://user-data.sh
