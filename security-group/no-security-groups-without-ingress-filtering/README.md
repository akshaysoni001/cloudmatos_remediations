# Remediation - Ensure No Security Groups without ingress filtering being used
Ensure there are no Security Groups without ingress filtering being used. Security groups provide stateful filtering of ingress/egress network traffic to AWS resources. It is recommended that no security group allows unrestricted ingress access.

Remediation remove all the rules that you passed in this ansible command from security group
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

| Parameter       | Comments                                 |
|-----------------|------------------------------------------|
| aws_access_key  | AWS Access key                           |
| aws_secret_key  | AWS Secret key                           |
| aws_region      | AWS Region Name                          |
| security_groups | List of security groups                  |
        | GroupName       | Security Group Name                      |
        | FromPort        | From Port     (Integer)                  |
        | ToPort          | To Port            (Integer)             |
        | IpProtocol      | Ip Protocoals                            |
        | IpRanges.CidrIp       | Cidr Range                               |



## Remediation Execution
Following command need to execute
```sh
  ansible-playbook playbook.yaml --extra-vars '{
  "aws_access_key": "xxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "security_groups":[{"GroupName":"akshay-testing","FromPort":0,"ToPort":65535,"IpProtocol":"TCP", "IpRanges":[{"CidrIp":"::/0"}]}]
}'
```
