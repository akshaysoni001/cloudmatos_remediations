# Remediation - API Gateway REST API stages configuration to use SSL certificates for backend authentication
API Management allows you to secure access to the backend service of an API using client certificates. This guide shows how to manage certificates in an Azure API Management service instance using the Azure portal. It also explains how to configure an API to use a certificate to access a backend service.

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

| Parameter      | Comments              |
|----------------|-----------------------|
| aws_access_key | AWS Access key        |
| aws_secret_key | AWS Secret key        |
| aws_region         | AWS Region Name       |
| api_id         | Rest API Id           |
| stage_name     | Rest API Stage Name   |
| certificate_id | Client Certificate Id |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "api_id": "xxx",
  "stage_name":"xx",
  "certificate_id":"xx"
}'
```