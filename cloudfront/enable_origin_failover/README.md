# Remediation - CloudFront distributions should have origin failover configured
This control checks whether an Amazon CloudFront distribution is configured with an origin group that has two or more origins.
CloudFront origin failover can increase availability. Origin failover automatically redirects traffic to a secondary origin if the primary origin is unavailable or if it returns specific HTTP response status codes.


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

# Pre-Configuration
To configure origin fail over, Distribution must have atleast two origin Id.

## Remediation Parameters

| Parameter           | Comments                   |
|---------------------|----------------------------|
| aws_access_key      | AWS Access key             |
| aws_secret_key      | AWS Secret key             |
| aws_region          | Region Name                |
| distribution_id     | CloudFront Distribution ID |
| primary_origin_id   | Primary Origin ID          |
| secondary_origin_id | Secondary Origin ID        |




## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "distribution_id": "xxx",
  "primary_origin_id": "xxx",
  "secondary_origin_id": "xxx",
}'
```