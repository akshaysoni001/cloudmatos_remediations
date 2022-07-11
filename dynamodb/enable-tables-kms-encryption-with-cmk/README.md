# Remediation - DynamoDB tables KMS-CMK encryption enabled
DynamoDB is a fully managed, multiregion, multimaster database that encrypts all your data at rest by default to help enhance the security of your DynamoDB data. Previously, DynamoDB gave you the option to use the AWS owned CMK or AWS managed CMK to encrypt your data. Now, you can use customer managed CMKs to help protect sensitive applications, adhere to your organization’s policies, meet compliance and regulatory requirements, and maintain an additional secure copy of your encryption keys outside of AWS.

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

| Parameter      | Comments            |
|----------------|---------------------|
| aws_account_id | AWS Account Id      |
| aws_access_key | AWS Access key      |
| aws_secret_key | AWS Secret key      |
| aws_region     | AWS Region Name     |
| table_name     | DynamoDB Table Name |
| kms_key        | KMS Key             |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_account_id": "xxxx",
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "table_name": "xxx",
  "kms_key": "xxx",
}'
```
