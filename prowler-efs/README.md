# Introduction

Remediate Prowler EFS specific compliance using Ansible Playbook

# Features

The main playbook is defined in ./playbook.yaml which essentially calls the different remediation tasks in ./tasks/* folder. Currently, the following remediation's are supported:

 * [Prowler.1] Check if EFS have policies which allow access to everyone


# Usage
 
 * Update ./inventory.yaml with system specific python location
    localhost ansible_python_interpreter=<location of python>

Manually update ./vars/variables.yaml.
    aws_region: <aws_region>
    efs_id:  <efs_id>

Run playbook
    ansible-playbook playbook.yaml --extra-vars '{"aws_access_key":"<aws_access_key>","aws_secret_key":"<aws_secret_key>"}'

