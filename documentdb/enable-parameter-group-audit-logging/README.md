# Remediation - Amazon DocumentDB parameter group audit logging enabled
# Id - MS-1634
Amazon DocumentDB provides 3.6 and 4.0 versioned cluster parameter groups. You can create a default cluster parameter group based on the docdb4.0 family named default.docdb4.0. In either version, you cannot modify the default.docdb4.0 or default.docdb3.6 cluster parameter group directly. To customize the parameters within a cluster parameter group and associate it to your Amazon DocumentDB cluster, you must first create a new, non-default cluster parameter group. Then you can modify the parameters within that new, custom parameter group and associate it to your Amazon DocumentDB cluster.

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

| Parameter      | Comments                         |
|----------------|----------------------------------|
| aws_access_key | AWS Access key                   |
| aws_secret_key | AWS Secret key                   |
| aws_region         | AWS Region Name                  |
| parameter_group_name        | Document DB Parameter Group Name |

## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "parameter_group_name": "xxx",
}'
```
