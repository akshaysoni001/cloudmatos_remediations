# Remediation - AWS SQS server side encryption is enabled
Amazon Simple Queue Service (SQS) provides the ability to encrypt queues so sensitive data is passed securely. It uses server-side-encrypyion (SSE) and supports AWS-managed Customer Master Key (CMK), as well as self-created/self-managed keys. SSE encrypts only the body of the message, with queue metadata and message metadata out of scope, and backlogged messages not encrypted.
If you operate in a regulated market, such as HIPAA for healthcare, PCI DSS for finance, or FedRAMP for government, you need to ensure sensitive data messages passed in this service are encrypted at rest.
We recommend you encrypt Data Queued using SQS.
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
  "queue_name:"xx",
}'
```