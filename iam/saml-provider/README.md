# Remediation - Check if there are SAML Providers then STS can be used - iam
An IAM SAML 2.0 identity provider is an entity in IAM that describes an external identity provider (IdP) service that supports the SAML 2.0 (Security Assertion Markup Language 2.0) standard. You use an IAM identity provider when you want to establish trust between a SAML-compatible IdP such as Shibboleth or Active Directory Federation Services and AWS, so that users in your organization can access AWS resources. IAM SAML identity providers are used as principals in an IAM trust policy.

Introduction To STS:
AWS Secure Token Service (STS) is a service provided by AWS that enables you to request temporary credentials with limited privilege for AWS IAM users. In this article, we will learn how to use the AWS CLI with STS to temporarily assume a different role.

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
# Reference ( Below task are required to do manually by user ( Download saml metadata & create iam role or user) )
1. How to assume a role using the AWS CLI and STS -> https://www.learnaws.org/2022/02/05/aws-cli-assume-role/
2. How to get saml metadata from external Identity provier, I use okta as external identity provider -> https://support.okta.com/help/s/question/0D51Y00008vdVyCSAU/how-to-obtain-okta-metadata?language=en_US
3. User Must have below policy assinged.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::{{aws_account_id}}:user/{{user}}"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```

## Remediation Parameters

| Parameter      | Comments                                                                        |
|----------------|---------------------------------------------------------------------------------|
| aws_access_key | AWS Access key                                                                  |
| aws_secret_key | AWS Secret key                                                                  |
| aws_region         | AWS Region Name                                                                 |
| unique_session_name         | Unique Session Name                                                             |
| role_type         | Role Tye, Which type of access your required, for ex - s3-read-only-assume-role |
| idp_exists         | Boolean (True if saml idp provider already exists                               |



## Remediation Execution
Following command need to execute
```sh
ansible-playbook playbook.yml --extra-vars '{
  "aws_access_key": "xxxx",
  "aws_secret_key": "xxxx",
  "aws_region": "us-east-1",
  "unique_session_name": "xxxx",
  "role_type": "s3-read-only-assume-role",
  "idp_exists": "False | True",
}'
```


# Output
Returns a set of temporary security credentials for users who have been authenticated via a SAML authentication response. This operation provides a mechanism for tying an enterprise identity store or directory to role-based AWS access without user-specific credentials or configuration