# Remediation - Amazon SQS queues not publicly accessible
AWS SQS is a hosted queue service that lets you integrate distributed software systems and components. It provides a generic web services API and it can be accessed by any programming language supported by AWS SDK.
Public SQS queues potentially expose existing interfaces to unwanted 3rd parties that can tap into an existing data stream, resulting in data leak to an unwanted party.
> Remediation Tool   - [Ansible](https://www.ansible.com/)

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
  "queue_name:"xx"
}'
```