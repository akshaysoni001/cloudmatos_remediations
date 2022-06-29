# Remediation - Enable Logging in CloudFront
CloudFront to create log files that contain detailed information about every user request that CloudFront receives

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

| Parameter       | Comments                   |
|-----------------|----------------------------|
| aws_access_key  | AWS Access key             |
| aws_secret_key  | AWS Secret key             |
| aws_region          | AWS Region Name            |
| distribution_id | CloudFront Distribution ID |
| logging_s3_bucket_name          | S3 Logging Bucket Name     |



## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-2",
  "distribution_id": "xxx",
  "logging_s3_bucket_name": "xxx"
}'
```