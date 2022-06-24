Remediation - Enable Logging in CloudFront
CloudFront to create log files that contain detailed information about every user request that CloudFront receives

Remediation Tool - Ansible

Remediation Script - playbook.yml

Remediation Requirements
The below requirements are needed to execute remediation script

pip packages

python >= 3.6
boto3 >= 1.15.0
botocore >= 1.18.0
Ansible Collection

This remedaition required the community.aws collection (version 2.4.0).

To install it, use:

ansible-galaxy collection install community.aws

Remediation Parameters
Parameter	Comments
aws_access_key	AWS Access key
aws_secret_key	AWS Secret key
region	                AWS Region
distribution_id     CloudFront Distribution Id
logging_s3_bucket_name S3 Bucket Name

Remediation Execution
Following command need to execute

ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "region": "us-east-1",
  "distribution_id": "xxxxxxx",
  "logging_s3_bucket_name": "xxxxxx""
}'