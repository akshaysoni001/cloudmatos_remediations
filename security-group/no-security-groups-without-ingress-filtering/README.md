# Remediation - Ensure No Security Groups without ingress filtering being used
Ensure there are no Security Groups without ingress filtering being used. Security groups provide stateful filtering of ingress/egress network traffic to AWS resources. It is recommended that no security group allows unrestricted ingress access.

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

| Parameter | Comments                                 |
|---------|------------------------------------------|
| aws_access_key | AWS Access key                           |
| aws_secret_key | AWS Secret key                           |
| aws_region | AWS Region Name                          |
| new_cidr_ip        | CIDR Ip Type : Valid Values ( ipv4/ipv6) |
| security_groups | List of security groups                  |
        | group_name | Security Group Name                      |
        | group_description | Security Group Description               |
        | vpc_id  | vpc_id                                   |
        | from_port | Starting Of Port Range                   |
        | to_port | End Port of Port range                   |
        | cidr_range | CIDR Range                               |



## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yaml --extra-vars '{
  "aws_access_key": "xxx",
  "aws_secret_key": "xxx",
  "aws_region": "us-east-1",
  "new_cidr_ip":"ipv4"
  "security_groups":[{"group_name":"xxx","group_description":"xx","vpc_id":"vpc_id","from_port":"xxx",
  "to_port":"to_port","cidr_range":"xxx"}]
}'
```
