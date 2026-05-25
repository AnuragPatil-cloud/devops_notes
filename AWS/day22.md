## AWS CLI installation and use 
```bash
sudo apt update -y
apt install unzip
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

 - Configuring and using AWS CLI for S3 and EC2 Management
```bash
aws configure
``` 
    - Access Key ID: YOUR_ACCESS_KEY
    - Secret Access Key: YOUR_SECRET_KEY
    - Default region name: us-east-1
    - Default output format:

```bash
aws s3 ls
aws s3 mb s3://your-bucket-name
aws s3 cp your-file.txt s3://your-bucket-name/
aws s3 cp s3://your-bucket-name/your-file.txt .
```

 - EC2 Management
```bash
aws ec2 describe-instances
aws ec2 start-instances --instance-ids <instanceid>
aws ec2 stop-instances --instance-ids <instanceid>
```
