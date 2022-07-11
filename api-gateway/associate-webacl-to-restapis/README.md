# Remediation - API Gateway should be associated with an AWS WAF web ACL
WS WAF is a web application firewall that helps protect web applications and APIs from attacks. It enables you to configure a set of rules (called a web access control list (web ACL)) that allow, block, or count web requests based on customizable web security rules and conditions that you define. For more information, see How AWS WAF Works.
You can use AWS WAF to protect your API Gateway API from common web exploits, such as SQL injection and cross-site scripting (XSS) attacks. These could affect API availability and performance, compromise security, or consume excessive resources. For example, you can create rules to allow or block requests from specified IP address ranges, requests from CIDR blocks, requests that originate from a specific country or region, requests that contain malicious SQL code, or requests that contain malicious script.

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
## Pre-Requisite
1. WAF ACL Certificate should be present. Provide it's name & id in ansible command.


## Remediation Parameters

| Parameter      | Comments             |
|----------------|----------------------|
| aws_access_key | AWS Access key       |
| aws_secret_key | AWS Secret key       |
| aws_region         | AWS Region Name      |
| api_id         | Rest API Id          |
| stage_name     | Rest API Stage Name  |
| web_acl_name   | WAF Certificate Name |
| web_acl_id     | WAF Certificate Id   |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "api_id": "xxx",
  "stage_name":"xx",
  "web_acl_name":"xx",
  "web_acl_id":"xxx"
}'
```