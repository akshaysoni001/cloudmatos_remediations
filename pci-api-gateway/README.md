# Introduction

Remediate Api Gateway specific compliance using Ansible Playbook

# Features

The main playbook is defined in ./playbook.yaml which essentially calls the different remediation tasks in ./tasks/* folder. Currently, the following remediation's are supported:

 * [PCI.3] API Gateway REST API stages should have AWS X-Ray tracing enabled
 * [PCI.2] API Gateway REST API stages should be configured to use SSL certificates for backend authentication


# Usage
 
 * Update ./inventory.yaml with system specific python location
    localhost ansible_python_interpreter=<location of python>

Manually update ./vars/variables.yaml.
    aws_region: <aws_region>
    api_id: <api_id>
    stage_name: <stasge_name>
    certificate_id: <certificate_id>

Run playbook
    ansible-playbook playbook.yaml --extra-vars '{"aws_account_id":"<aws_account_id>",aws_access_key":"<aws_access_key>","aws_secret_key":"<aws_secret_key>"}'

Note: Other tasks are still pending of different use case. Please don't uncomment the task commented in playbook.