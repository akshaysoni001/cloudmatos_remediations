# Remediation - Amazon DocumentDB instance audit logging enabled
# id - MS-1631
The events recorded by the AWS DocumentDB audit logs include: successful and failed authentication attempts, creating indexes or dropping a collection in a database within the DocumentDB cluster.
AWS CloudWatch logs are a service that monitors, stores and accesses your log files from a variety of sources within your AWS account. When logging is enabled information such as Data Definition Language, authentication, authorization, and user management events are sent to AWS CloudWatch logs. This information can be used to analyze, monitor and archive your Amazon DocumentDB auditing events for security and compliance requirements.

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

| Parameter      | Comments                 |
|----------------|--------------------------|
| aws_access_key | AWS Access key           |
| aws_secret_key | AWS Secret key           |
| aws_region         | AWS Region Name          |
| cluster_name        | Document DB Cluster Name |

## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "cluster_name": "xxx",
}'
```
