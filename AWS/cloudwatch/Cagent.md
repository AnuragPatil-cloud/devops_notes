## cloudwatch 
- https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/manual-installation.html

## manual configuration 
## cloudwatch agent 
Step 1: Download and install the CloudWatch agent 
```bash
wget https://s3.amazonaws.com/amazoncloudwatch-agent/debian/amd64/latest/amazon-cloudwatch-agent.deb
```
step 2: install the package with dpkg:
```bash
sudo dpkg -i -E ./amazon-cloudwatch-agent.deb
```
step 3: Configure the agent
```bash
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
```
After wizard completes:(for logs) check in cloudwatch logs syslogs generated
```bash
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl \
-a fetch-config -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json -s
```

Verify the agent's status:
```bash
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -m ec2 -a status
```
## file based configuration 
step 4: install aws cli 
```bash
sudo apt install unzip 
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

step 5: aws configure 
```bash
aws configure
```
- create role and attached it to ec2 innstance 
```bash
aws sts get-caller-identity
```
step 6: install cloudwatch agent 
```bash
sudo apt-get update
sudo apt-get install -y amazon-cloudwatch-agent
```
check 
```bash
/opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a status
```
create file and insert data provided by devloper to set cloudwatch agent 
```bash
sudo nano /opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json
```
```jason
{
  "agent": {
    "metrics_collection_interval": 60,
    "run_as_user": "root"
  },
  "metrics": {
    "append_dimensions": {
      "InstanceId": "${aws:InstanceId}"
    },
    "metrics_collected": {
      "cpu": {
        "measurement": [
          "usage_system",
          "usage_user",
          "usage_idle"
        ],
        "totalcpu": true
      },
      "mem": {
        "measurement": [
          "mem_used_percent"
        ]
      },
      "disk": {
        "measurement": [
          "used_percent"
        ],
        "resources": [
          "*"
        ]
      }
    }
  },
  "logs": {
    "logs_collected": {
      "files": {
        "collect_list": [
          {
            "file_path": "/var/log/syslog",
            "log_group_name": "/ubuntu/syslog",
            "log_stream_name": "{instance_id}"
          }
        ]
      }
    }
  }
}
```

step 7: agent start and enable 
```bash
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl \
  -a fetch-config -m ec2 -s \
  -c file:/opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json
```
step 8: service start and enable 
```bash
sudo systemctl enable amazon-cloudwatch-agent
sudo systemctl status amazon-cloudwatch-agent
```
step 9: varify 
```bash
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -m ec2 -a status
```
