# Introduction

Remediate Prowler SNS specific compliance using Ansible Playbook

# Features

The main playbook is defined in ./playbook.yaml which essentially calls the different remediation tasks in ./tasks/* folder. Currently, the following remediation's are supported:

 * [Prowler.1/2] Check if SNS topics have policy set as Public


# Usage
 
 * Update ./inventory.yaml with system specific python location
    localhost ansible_python_interpreter=<location of python>

Manually update ./vars/variables.yaml.
    aws_region: <aws_region>
    sns_topic:  <sns_topic_name>

Run playbook
    ansible-playbook playbook.yaml --extra-vars '{"aws_account_id":"<aws_account_id>", "aws_access_key":"<aws_access_key>","aws_secret_key":"<aws_secret_key>"}'

