
## Lambda
### crete buccket
```py
import boto3
from botocore.exceptions import ClientError

def lambda_handler(event, context):
    bucket_name = 'uniq_buccket_name'
    region = 'us-east-1' # Change to your preferred region
    
    s3_client = boto3.client('s3')
    
    try:
        # Check if bucket exists
        s3_client.head_bucket(Bucket=bucket_name)
        message = f"Bucket '{bucket_name}' already exists and is owned by you."
    except ClientError as e:
        error_code = e.response['Error']['Code']
        if error_code == '404':
            # Bucket does not exist, create it
            if region == 'us-east-1':
                s3_client.create_bucket(Bucket=bucket_name)
            else:
                s3_client.create_bucket(
                    Bucket=bucket_name,
                    CreateBucketConfiguration={'LocationConstraint': region}
                )
            message = f"Bucket '{bucket_name}' created successfully."
        else:
            message = f"Error checking bucket: {str(e)}"

    return {
        'statusCode': 200,
        'body': message
    }
```
### copy data from instance to buccket 
- lambda function and ec2 must be in same region to copy the logs from instance to s3 buccket 

```py
import boto3
import time

def lambda_handler(event, context):
    ssm = boto3.client('ssm')
    instance_id = 'instance_id'
    bucket_name = 'uniq_buccket_name'
    
    # Define which logs you want to copy (e.g., /var/log/)
    log_path = "/root/" 
    
    # The shell command to run on the EC2 instance
    # It uses 'aws s3 sync' to only copy new/changed files
    command = f"aws s3 sync {log_path} s3://{bucket_name}/ec2-logs/{instance_id}/"

    try:
        # Send the command to the EC2 instance
        response = ssm.send_command(
            InstanceIds=[instance_id],
            DocumentName="AWS-RunShellScript",
            Parameters={'commands': [command]}
        )
        
        command_id = response['Command']['CommandId']
        return {
            'statusCode': 200,
            'body': f"Log copy initiated. Command ID: {command_id}"
        }

    except Exception as e:
        return {
            'statusCode': 500,
            'body': f"Error: {str(e)}"
        }

```
### lanch an Ec2 instance 
```py
import boto3

def lambda_handler(event, context):
    # 1. Connect to EC2 in Mumbai region
    ec2 = boto3.resource('ec2', region_name='ap-south-1')
    
    print("Finding the latest Ubuntu AMI...")
    
    # 2. Find the latest Ubuntu 24.04 LTS AMI
    images = list(ec2.images.filter(
        Owners=['099720109477'],
        Filters=[
            {'Name': 'name', 'Values': ['ubuntu/images/hvm-ssd-gp3/ubuntu-noble-24.04-amd64-server-*']},
            {'Name': 'state', 'Values': ['available']}
        ]
    ))
    
    # Sort images by date to get the newest one
    images.sort(key=lambda x: x.creation_date, reverse=True)
    latest_ami_id = images[0].id
    
    # 3. Launch the Instance
    try:
        instances = ec2.create_instances(
            ImageId=latest_ami_id,
            MinCount=1,
            MaxCount=1,
            InstanceType='t3.micro',
            TagSpecifications=[
                {
                    'ResourceType': 'instance',
                    'Tags': [{'Key': 'Name', 'Value': 'Ubuntu-Mumbai-Server'}]
                }
            ]
        )
        
        instance_id = instances[0].id
        print(f"Successfully launched instance: {instance_id}")
        
        return {
            'statusCode': 200,
            'body': f"Success! Launched {instance_id} using AMI {latest_ami_id}"
        }

    except Exception as e:
        print(f"Error: {str(e)}")
        return {
            'statusCode': 500,
            'body': str(e)
        }
```



