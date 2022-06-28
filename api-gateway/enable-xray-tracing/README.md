# Remediation - Ensure API Gateway has X-Ray tracing enabled
When an API Gateway stage has the active tracing feature enabled, Amazon API Gateway service automatically samples API invocation requests based on the sampling algorithm specified by AWS X-Ray.
With tracing enabled X-Ray can provide an end-to-end view of an entire HTTP request. You can use this to analyze latencies in APIs and their backend services.

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

| Parameter      | Comments              |
|----------------|-----------------------|
| aws_access_key | AWS Access key        |
| aws_secret_key | AWS Secret key        |
| region         | Region Name           |
| api_id         | Rest API Id           |
| stage_name     | Rest API Stage Name   |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "region": "us-east-1",
  "api_id": "xxx",
  "stage_name":"xx",
}'
```

## Note:
This remediaion script automatically fetch swagger.json file from api_id & stage name, later it will be used to enable x-ray tracing.