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

| Parameter      | Comments        |
|----------------|-----------------|
| aws_access_key | AWS Access key  |
| aws_secret_key | AWS Secret key  |
| aws_region         | AWS Region Name |
| sns_topic      | SNS Topic Name  |



## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "vpc_id":"xxx",
  "security_group_id":"xx",
  "from_port":"from_port",
  "to_port":"XX",
  "cidr_range":"XX"
}'
```


# Introduction

Remediate Prowler Security Group specific compliance using Ansible Playbook

# Features

The main playbook is defined in ./playbook.yaml which essentially calls the different remediation tasks in ./tasks/* folder. Currently, the following remediation's are supported:

 * [Prowler.1] Ensure No Security Groups without ingress filtering being used


# Usage
 
 * Update ./inventory.yaml with system specific python location
    localhost ansible_python_interpreter=<location of python>

Manually update ./vars/variables.yaml.
    aws_region: <aws_region>
    vpc_id: <vpc_id>
    security_group_name: <security_group_name>
    security_group_description: <security_group_description>
    security_group_id: <security_group_id>
    from_port: <from_port>
    to_port: <to_port>
    cidr_range: <cidr_range>

Run playbook
    ansible-playbook playbook.yaml --extra-vars '{"aws_access_key":"<aws_access_key>","aws_secret_key":"<aws_secret_key>"}'

