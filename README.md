## AWS CLI Installation Commands

    sudo apt update
    
    sudo apt install unzip
    
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
    
    unzip awscliv2.zip
    
    sudo ./aws/install


## DAY-5 Commands

    VPC=$(aws ec2 describe-vpcs \
      --filters Name=tag:Name,Values=project-vpc \
      --query "Vpcs[0].VpcId" \
      --output text)
    echo $VPC


    SUBNET=$(aws ec2 describe-subnets \
      --filters Name=tag:Name,Values=project-subnet-public1-us-east-1a \
      --query "Subnets[0].SubnetId" \
      --output text)
    echo $SUBNET

## EC2- Command

    INSTANCE=$(aws ec2 run-instances \
      --image-id $AMI \
      --instance-type t2.micro \
      --key-name hitesh-lab-key \
      --security-group-ids $SG \
      --subnet-id $SUBNET \
      --associate-public-ip-address \
      --iam-instance-profile Name=EC2-S3-Profile \
      --tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=Ubuntu-S3-Lab}]' \
      --query "Instances[0].InstanceId" \
      --output text)
    
    echo $INSTANCE

