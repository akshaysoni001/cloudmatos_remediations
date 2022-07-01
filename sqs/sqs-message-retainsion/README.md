# Remediation - AWS SQS messages not older than 80 percent of message retention
Messages in Amazon SQS have a limited amount of time to be received and processed before they are automatically deleted by SQS. If a message is not processed before the message retention period has passed, it will be permanently deleted> Remediation Tool   - [Ansible](https://www.ansible.com/)

> Remediation Script - [playbook.yml](playbook.yml)

## Remediation Requirements
The below requirements are needed to execute remediation script

> pip packages
- python >= 3.6
- boto3 >= 1.15.0
- botocore >= 1.18.0

> Ansible Collection

This remedaition required the [community.aws collection](https://galaxy.ansible.com/community/aws) (version 2.4.0).

To install it, use: 
```sh
ansible-galaxy collection install community.aws
```

## Remediation Parameters

| Parameter      | Comments        |
|----------------|-----------------|
| aws_account_id | AWS Account Id  |
| aws_access_key | AWS Access key  |
| aws_secret_key | AWS Secret key  |
| aws_region     | AWS Region Name |
| queue_name     | SQS Queue Name  |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_account_id":"xxx"
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "queue_name:"xx",
}'
```