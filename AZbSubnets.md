# Public Subnet in AZb
aws ec2 create-subnet \
    --vpc-id <vpc-id> \
    --cidr-block 10.0.2.0/24 \
    --availability-zone <region>b \
    --tag-specifications 'ResourceType=subnet,Tags=[{Key=Name,Value=Public-Subnet-AZ2}]'

# Private Subnet in AZb
aws ec2 create-subnet \
    --vpc-id <vpc-id> \
    --cidr-block 10.0.3.0/24 \
    --availability-zone <region>b \
    --tag-specifications 'ResourceType=subnet,Tags=[{Key=Name,Value=Private-Subnet-AZ2}]'
