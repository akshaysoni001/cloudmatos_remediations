# Remediation - Enable Encryption In Transit (CloudFront)
Amazon CloudFront to require that viewers use HTTPS to request your files, so that connections are encrypted when CloudFront communicates with viewers. You also can configure CloudFront to use HTTPS to get files from your origin, so that connections are encrypted when CloudFront communicates with your origin.

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

| Parameter       | Comments              |
|-----------------|-----------------------|
| aws_access_key  | AWS Access key        |
| aws_secret_key  | AWS Secret key        |
| distribution_id | CloudFront Distribution ID |
| region          |Region Name            |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "region": "us-east-2",
  "distribution_id": "xxx",
}'
```