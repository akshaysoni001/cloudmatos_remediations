# Remediation - DynamoDB Accelerator (DAX) clusters should be encrypted at rest
Amazon DynamoDB Accelerator (DAX) encryption at rest provides an additional layer of data protection by helping secure your data from unauthorized access to the underlying storage.
With encryption at rest the data persisted by DAX on disk is encrypted using 256-bit Advanced Encryption Standard (AES-256). DAX writes data to disk as part of propagating changes from the primary node to read replicas. DAX encryption at rest automatically integrates with AWS KMS for managing the single service default key used to encrypt cluster

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

| Parameter      | Comments             |
|----------------|----------------------|
| aws_access_key | AWS Access key       |
| aws_secret_key | AWS Secret key       |
| region         | Region Name          |
| dax_cluster_name        | DAX Cluster Name     |
| node_type        | DAX Cluster Type     |
| iam_arn        | IAM Role for Cluster |


# Create Prerequistic
## To create IAM Role for DAX Cluster
-   step 1. Go to IAM Console and select ROLES
-   step 2. click on create role
-   step 3. select Trusted entity type as AWS_SERVICE
-   step 4. In Use case, type Dynamodb
-   step 5. select DynamoDB Accelerator (DAX) - Cluster management and click next
-   step 6. DAXServiceRolePolicy is showing their as policy, click next.
-   step 7. verify detail and click on create role.
-   step 8. search created role in ROLES and copy arn from that and put it as iam_arn in ansible command.


# Node Types
-   Find the supported node type of dax cluster and select according to requirement and pass its type to command.

## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "region": "us-east-1",
  "dax_cluster_name": "xxx",
  "node_type":"xxx",
  "iam_arn":"xx"
}'
```
