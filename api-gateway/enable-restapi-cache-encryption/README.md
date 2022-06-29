# Remediation -  API Gateway REST API cache data should be encrypted at rest
API Gateway REST API stage is configured to cache and the cache is not encrypted. Encrypting data at rest reduces the risk of data stored on disk being accessed by a user not authenticated to AWS. It adds another set of access controls to limit unauthorized users ability access the data.

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
| aws_access_key | AWS Access key      |
| aws_secret_key | AWS Secret key      |
| aws_region         | AWS Region Name     |
| api_id         | Rest API Id         |
| stage_name     | Rest API Stage Name |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "api_id": "xxx",
  "stage_name":"xx",
}'
```