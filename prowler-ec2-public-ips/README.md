# Introduction

Remediate Prowler Public Ips specific compliance using Ansible Playbook

# Features

The main playbook is defined in ./playbook.yaml which essentially calls the different remediation tasks in ./tasks/* folder. Currently, the following remediation's are supported:

 * [Prowler.1] Check if any of the Elastic or Public IP are in Shodan (requires Shodan API KEY) - ec2 [High]


# Usage
 
 * Update ./inventory.yaml with system specific python location
    localhost ansible_python_interpreter=<location of python>

Manually update ./vars/variables.yaml.
    aws_region: <aws_region>
    instance_id:  <instance_id>
    subnet_id: <subnet_id>

Run playbooks:
1. First Run Playbook get_public_instance_ids_playbook.yaml to get list of public ips, Then it required human intervention to check whihc ips should be private.
    Command: ansible-playbook get_public_instance_ids_playbook.yaml --extra-vars '{"aws_access_key":"<aws_access_key>","aws_secret_key":"<aws_secret_key>"}'
    After finding instances, Then define instance_id & subnet_id in variable.yaml.
    Then Execute below command to make them from public to private. 
    
2. ansible-playbook playbook.yaml --extra-vars '{"aws_access_key":"<aws_access_key>","aws_secret_key":"<aws_secret_key>"}'

