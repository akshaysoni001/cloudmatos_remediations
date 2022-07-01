# Remediation - DynamoDB tables KMS encryption enabled
Although DynamoDB tables are encrypted at rest by default with AWS owned KMS keys, using AWS managed or customer managed KMS keys provides additional functionality, such as viewing key policies, auditing usage, and rotating cryptographic material.

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

| Parameter      | Comments             |
|----------------|----------------------|
| aws_access_key | AWS Access key       |
| aws_secret_key | AWS Secret key       |
| aws_region         | AWS Region Name      |
| table_name        | DynamoDB Table Name  |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "table_name": "xxx",
}'
```
