# Remediation - Ensure CloudWatch Metrics & Alarm is configured
Amazon CloudWatch is a monitoring and management service built for developers, system operators, site reliability engineers (SRE), and IT managers. AWS CloudWatch provides data and actionable insights to monitor applications, understand and respond to system-wide performance changes, optimize resource utilization, and get a unified view of operational health. AWS CloudWatch uses logs, metrics, and events to provide a unified view of AWS resources, applications and services.

> Remediation Tool   - [Ansible](https://www.ansible.com/)

> Remediation Script - [playbook.yml](playbook.yml)
> Remediation Details -
> The main playbook is defined in ./playbook.yaml which essentially calls the different remediation tasks in ./tasks/* folder. Currently, the following remediation's are supported:

 * [PCI-CloudWatch] It's a pre-requisite, it creates required policies, logs group, role and S3 bucket to push logs.
 * [PCI-CloudWatch] Create metric filter and alarm for unauthorized API calls
 * [PCI-CloudWatch] Create metric filter and alarm for Config configuration changes
 * [PCI-CloudWatch] Create metric filter and alarm for AWS Organizations changes 
 * [PCI-CloudWatch] Create metric filter and alarm for CloudTrail configuration changes should be configured 
 * [PCI-CloudWatch] Create metric filter and alarm for disabling or scheduled deletion of customer managed KMS keys  
 * [PCI-CloudWatch] Create metric filter and alarm for IAM policy changes should be configured 
 * [PCI-CloudWatch] Create metric filter and alarm for Management Console authentication failures 
 * [PCI-CloudWatch] Create metric filter and alarm for root account usage
 * [PCI-CloudWatch] Create metric filter and alarm for S3 bucket policy changes
 * [PCI-CloudWatch] Create metric filter and alarm for Management Console sign-in without MFA


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
| unauthorized_api_metric_filter_alarm_exists          | Boolean(True! False)            |
| config_configuration_changes_metric_filter_alarm_exists          | Boolean(True! False)            |
| aws_organization_changes_filter_exists          | Boolean(True! False)            |
| cloudtrail_configuration_changes_metric_filter_alarm_exists          | Boolean(True! False)            |
| delete_kms_activity_metric_filter_alarm_exists          | Boolean(True! False)            |
| iam_policy_changes_metric_filter_alarm_exists          | Boolean(True! False)            |
| console_sign_failure_metric_filter_alarm_exists          | Boolean(True! False)            |
| root_account_signin_usage_metric_filter_alarm_exists          | Boolean(True! False)            |
| s3_bucket_policy_change_metric_filter_alarm_exists          | Boolean(True! False)            |
| signin_without_mfa_metric_filter_alarm_exists          | Boolean(True! False)            |
    



## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "unauthorized_api_metric_filter_alarm_exists": "True"
  "config_configuration_changes_metric_filter_alarm_exists": "True"
  "aws_organization_changes_filter_exists": "True"
  "cloudtrail_configuration_changes_metric_filter_alarm_exists": "True"
  "delete_kms_activity_metric_filter_alarm_exists": "True"
  "iam_policy_changes_metric_filter_alarm_exists": "True"
  "console_sign_failure_metric_filter_alarm_exists": "True"
  "root_account_signin_usage_metric_filter_alarm_exists": "True"
  "s3_bucket_policy_change_metric_filter_alarm_exists": "True"
  "signin_without_mfa_metric_filter_alarm_exists": "True"
}'
```
# Note:
For parameter like <alarm_exists> passed it as "False", if alarm is not present.
