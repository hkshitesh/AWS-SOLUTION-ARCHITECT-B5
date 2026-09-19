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


