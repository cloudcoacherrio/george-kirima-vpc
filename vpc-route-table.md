# Create public route table
aws ec2 create-route-table \
    --vpc-id <vpc-id> \
    --tag-specifications 'ResourceType=route-table,Tags=[{Key=Name,Value=Public-RT}]'

# Add route to Internet Gateway
aws ec2 create-route \
    --route-table-id <public-rt-id> \
    --destination-cidr-block 0.0.0.0/0 \
    --gateway-id <igw-id>

# Associate public subnets with public route table
aws ec2 associate-route-table \
    --subnet-id <public-subnet-1-id> \
    --route-table-id <public-rt-id>

aws ec2 associate-route-table \
    --subnet-id <public-subnet-2-id> \
    --route-table-id <public-rt-id>
