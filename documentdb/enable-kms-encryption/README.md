# Remediation - Amazon DocumentDB snapshot encryption enabled
Amazon DocumentDB uses the 256-bit Advanced Encryption Standard (AES-256) to encrypt your data using encryption keys stored in AWS Key Management Service (AWS KMS). When using an Amazon DocumentDB cluster with encryption at rest enabled, you don't need to modify your application logic or client connection. Amazon DocumentDB handles encryption and decryption of your data transparently, with minimal impact on performance.

Amazon DocumentDB integrates with AWS KMS and uses a method known as envelope encryption to protect your data. When an Amazon DocumentDB cluster is encrypted with an AWS KMS, Amazon DocumentDB asks AWS KMS to use your KMS key to generate a ciphertext data key to encrypt the storage volume. The ciphertext data key is encrypted using the KMS key that you define, and is stored along with the encrypted data and storage metadata. When Amazon DocumentDB needs to access your encrypted data, it requests AWS KMS to decrypt the ciphertext data key using your KMS key and caches the plaintext data key in memory to efficiently encrypt and decrypt data in the storage volume.

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
## Pre-requistic
1. Make sure deletion protection is disble for the cluster you want to encrypt
2. Provide instance name & its class, Remediation script will create one instace of that class, if user want more isntance then he has do create them mannualy.

## Remediation Parameters

| Parameter      | Comments                        |
|----------------|---------------------------------|
| aws_account_id | AWS Account Id                  |
| aws_access_key | AWS Access key                  |
| aws_secret_key | AWS Secret key                  |
| aws_region     | AWS Region Name                 |
| cluster_name   | DynamoDB Cluster Name           |
| instance_name  | DynamoDB Cluster Instance Name  |
| instance_class | DynamoDB Cluster Instance Class |
| kms_key        | AWS KMS Key                     |


## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_account_id": "xxxx",
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "cluster_name": "xxx",
  "instance_name": "xxx",
  "instance_class": "xxx",
  "kms_key": "xxx",
}'
```
