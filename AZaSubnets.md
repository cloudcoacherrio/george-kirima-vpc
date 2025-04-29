# Public Subnet in AZ1
aws ec2 create-subnet \
    --vpc-id <vpc-id> \
    --cidr-block 10.0.0.0/24 \
    --availability-zone <region>a \
    --tag-specifications 'ResourceType=subnet,Tags=[{Key=Name,Value=Public-Subnet-AZ1}]'

# Private Subnet in AZ1
aws ec2 create-subnet \
    --vpc-id <vpc-id> \
    --cidr-block 10.0.1.0/24 \
    --availability-zone <region>a \
    --tag-specifications 'ResourceType=subnet,Tags=[{Key=Name,Value=Private-Subnet-AZ1}]'
