# Remediation - Ensure no Network ACLs allow ingress from 0.0.0.0/0 to any port - ec2
The Network Access Control List (NACL) function provide stateless filtering of ingress and egress network traffic to AWS resources. It is recommended that no NACL allows unrestricted ingress access to remote server administration ports, such as SSH to port 22 and RDP to port 3389.


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

| Parameter      | Comments       |
|----------------|----------------|
| aws_access_key | AWS Access key |
| aws_secret_key | AWS Secret key |
| region         | Region Name    |
| nacl_id        | Network ACL Id |
| vpc_id         | VPC Id         |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "region": "us-east-1",
  "vpc_id": "xxx",
  "nacl_id": "xxx"
}'
```