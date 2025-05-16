# How to Create an Amazon EC2 Key Pair

## Prerequisites
- An AWS account
- Access to AWS Management Console
- IAM permissions to create and manage EC2 key pairs

## Steps to Create an EC2 Key Pair

### Method 1: Using AWS Management Console

1. Sign in to the AWS Management Console
2. Navigate to the EC2 Dashboard:
   - Click on "Services" at the top
   - Select "EC2" under Compute

3. Find Key Pairs:
   - In the left navigation pane
   - Click "Key Pairs" under "Network & Security"

4. Create New Key Pair:
   - Click "Create key pair" button
   - Enter a name for your key pair
   - Select key pair type:
     - RSA (default, recommended)
     - ED25519 (for Linux instances only)
   - Choose private key file format:
     - .pem (for OpenSSH)
     - .ppk (for PuTTY)
   - Click "Create key pair"

5. Save the Private Key:
   - The private key file will automatically download
   - Store it in a secure location
   - Change permissions if needed (Linux/Mac):
     ```bash
     chmod 400 your-key-pair-name.pem
     ```

### Method 2: Using AWS CLI

1. Create key pair and save to file:
```bash
aws ec2 create-key-pair \
    --key-name "your-key-pair-name" \
    --query 'KeyMaterial' \
    --output text > your-key-pair-name.pem
