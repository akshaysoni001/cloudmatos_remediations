# Remediation - Check if any of the Elastic or Public IP are in Shodan (requires Shodan API KEY) - ec2 
Shodan is a search engine for Internet connected devices, ranging from internet connected cameras to cloud servers.


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
## Prerequistic

Execute mannual.yaml, it provides the list of public instance id, Check these instance, and figure out, it is required to be private or not, If it is 
not supposed to be public then pass these instance id in the ansible command, it will make them private.


## Remediation Parameters

| Parameter      | Comments        |
|----------------|-----------------|
| aws_access_key | AWS Access key  |
| aws_secret_key | AWS Secret key  |
| aws_region         | AWS Region Name |
| instance_id    | EC2 Instance Id |
| subnet_id      | Subnet Id       |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "instance_id": "xxx",
  "subnet_id": "xxx"
}'
```
