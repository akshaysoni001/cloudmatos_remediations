# Remediation - Create metric filter and alarm for disabling or scheduled deletion of customer managed KMS keys
Amazon CloudWatch is a monitoring and management service built for developers, system operators, site reliability engineers (SRE), and IT managers. AWS CloudWatch provides data and actionable insights to monitor applications, understand and respond to system-wide performance changes, optimize resource utilization, and get a unified view of operational health. AWS CloudWatch uses logs, metrics, and events to provide a unified view of AWS resources, applications and services.

> Remediation Tool   - [Ansible](https://www.ansible.com/)

> Remediation Script - [playbook.yml](playbook.yml)
> Remediation Details -
> The main playbook is defined in ./playbook.yaml which essentially calls the different remediation tasks in ./tasks/* folder. Currently, the following remediation's are supported:

 * [PCI-CloudWatch] It's a pre-requisite, it creates required policies, logs group, role and S3 bucket to push logs.
 * [PCI-CloudWatch] Create metric filter and alarm for disabling or scheduled deletion of customer managed KMS keys


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

| Parameter       | Comments                   |
|-----------------|----------------------------|
| aws_access_key  | AWS Access key             |
| aws_secret_key  | AWS Secret key             |
| aws_region          | AWS Region Name         |
| delete_kms_activity_metric_filter_alarm_exists          | Boolean(True! False)            |



## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "delete_kms_activity_metric_filter_alarm_exists": "False"
}'
```