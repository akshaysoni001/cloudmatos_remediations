# Remediation - Check if Glue development endpoints have S3 encryption enabled
A security configuration in Amazon Glue contains the properties that are needed when you write encrypted data. You create security configurations on the Amazon Glue console to provide the encryption properties that are used by crawlers, jobs, and development endpoints.

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

| Parameter                     | Comments                       |
|-------------------------------|--------------------------------|
| aws_access_key                | AWS Access key                 |
| aws_secret_key                | AWS Secret key                 |
| region                        | Region Name                    |
| kms_key                       | KMS Encryption key             |
| security_configuration_exists | Boolean(True if exist ! False) |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "region": "us-east-1",
  "kms_key": "xxx",
  "security_configuration_exists":"False",
}'
```







 * [Prowler.1]  7.114 [extra7114] Check if Glue development endpoints have S3 encryption enabled. - glue [Medium]
*  [Prowler.2]  7.118 [extra7118] Check if Glue ETL Jobs have S3 encryption enabled. - glue [Medium]
