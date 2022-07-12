# Remediation - DynamoDB tables in the backup plan
 The backup plans include schedules and retention policies for your DynamoDB tables. AWS Backup creates the backups and deletes prior backups based on your retention schedule. AWS Backup also includes advanced DynamoDB backup options that aren’t available in the DynamoDB service, including lower-cost tiered storage, and cross-account and cross-Region copy. 
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

## Pre-Requisite
1. Backup plan should already be created and pass its backup_plan_id.
2. need to create iam role, which has access to perform backup & restore operation of aws resources

Reference Link to create iam role & its permissions:
https://docs.aws.amazon.com/aws-backup/latest/devguide/iam-service-roles.html#:~:text=Managed%20policies.-,Default%20service%20role%20for%20AWS%20Backup,-When%20using%20the

## Remediation Parameters

| Parameter      | Comments        |
|----------------|-----------------|
| aws_account_id | AWS Account Id  |
| aws_access_key | AWS Access key  |
| aws_secret_key | AWS Secret key  |
| aws_region     | AWS Region Name |
| backup_plan_id | Backup Plan Id  |
| iam_role_name  | IAM Role        |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_account_id": "xxxx",
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "backup_plan_id": "xxx",
  "iam_role_name": "xxx",
}'
```
