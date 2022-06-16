# Introduction

Remediate Prowler CloudWatch specific compliance using Ansible Playbook

# Features

The main playbook is defined in ./playbook.yaml which essentially calls the different remediation tasks in ./tasks/* folder. Currently, the following remediation's are supported:

 * [PCI-CloudWatch.1] It's a pre-requisite, it creates required policies, logs group, role and S3 bucket to push logs.
 * [PCI-CloudWatch.2] Create metric filter and alarm for unauthorized API calls
 * [PCI-CloudWatch.3] Create metric filter and alarm for Config configuration changes
 * [PCI-CloudWatch.4] Create metric filter and alarm for AWS Organizations changes 
 * [PCI-CloudWatch.5] Create metric filter and alarm for CloudTrail configuration changes should be configured 
 * [PCI-CloudWatch.6] Create metric filter and alarm for disabling or scheduled deletion of customer managed KMS keys  
 * [PCI-CloudWatch.7] Create metric filter and alarm for IAM policy changes should be configured 
 * [PCI-CloudWatch.8] Create metric filter and alarm for Management Console authentication failures 
 * [PCI-CloudWatch.9] Create metric filter and alarm for root account usage
 * [PCI-CloudWatch.10] Create metric filter and alarm for S3 bucket policy changes
 * [PCI-CloudWatch.11] Create metric filter and alarm for Management Console sign-in without MFA


# Usage
 
 * Update ./inventory.yaml with system specific python location
    localhost ansible_python_interpreter=<location of python>

Manually update ./vars/variables.yaml.
Note: For Every service mark that api alarm exists status as "False", it will skip task if it was "True"
    ##
    aws_region: <aws_region>
    unauthorized_api_metric_filter_alarm_exists: "False"
    config_configuration_changes_metric_filter_alarm_exists: "False"
    aws_organization_changes_filter_exists: "False"
    cloudtrail_configuration_changes_metric_filter_alarm_exists: "False"
    delete_kms_activity_metric_filter_alarm_exists: "False"
    iam_policy_changes_metric_filter_alarm_exists: "False"
    console_sign_failure_metric_filter_alarm_exists: "False"
    root_account_signin_usage_metric_filter_alarm_exists: "False"
    s3_bucket_policy_change_metric_filter_alarm_exists: "False"
    signin_without_mfa_metric_filter_alarm_exists: "False"

Run playbook
    ansible-playbook playbook.yaml --extra-vars '{"aws_account_id":"<aws_account_id>", "aws_access_key":"<aws_access_key>","aws_secret_key":"<aws_secret_key>"}'

