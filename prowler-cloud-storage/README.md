# Introduction

Remediate PCI Glue(S3 Encryption) specific compliance using Ansible Playbook

# Features

The main playbook is defined in ./playbook.yaml which essentially calls the different remediation tasks in ./tasks/* folder. Currently, the following remediation's are supported:

 * [Prowler.1]  7.114 [extra7114] Check if Glue development endpoints have S3 encryption enabled. - glue [Medium]
*  [Prowler.2]  7.118 [extra7118] Check if Glue ETL Jobs have S3 encryption enabled. - glue [Medium]


# Usage
 
 * Update ./inventory.yaml with system specific python location
    localhost ansible_python_interpreter=<location of python>

Manually update ./vars/variables.yaml.
    aws_region: <aws_region>
    kms_key:  <kms_key>

Run playbooks:
1.  ansible-playbook playbook.yaml --extra-vars '{"aws_account_id":<aws_account_id>,"aws_access_key":"<aws_access_key>","aws_secret_key":"<aws_secret_key>"}'

