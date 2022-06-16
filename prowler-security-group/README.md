# Introduction

Remediate Prowler Security Group specific compliance using Ansible Playbook

# Features

The main playbook is defined in ./playbook.yaml which essentially calls the different remediation tasks in ./tasks/* folder. Currently, the following remediation's are supported:

 * [Prowler.1] Ensure No Security Groups without ingress filtering being used


# Usage
 
 * Update ./inventory.yaml with system specific python location
    localhost ansible_python_interpreter=<location of python>

Manually update ./vars/variables.yaml.
    aws_region: <aws_region>
    vpc_id: <vpc_id>
    security_group_name: <security_group_name>
    security_group_description: <security_group_description>
    security_group_id: <security_group_id>
    from_port: <from_port>
    to_port: <to_port>
    cidr_range: <cidr_range>

Run playbook
    ansible-playbook playbook.yaml --extra-vars '{"aws_access_key":"<aws_access_key>","aws_secret_key":"<aws_secret_key>"}'

