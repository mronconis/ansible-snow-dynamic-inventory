# Ansible ServiceNow Dynamic Inventory

Demo showing how to configure Ansible Dynamic Inventory using the ServiceNow CMDB (servicenow.itsm collection). Includes sample configurations, CI filtering, and playbooks to automate infrastructure management using ServiceNow as a single source of truth.

## Pre-requisite

Start a ServiceNow demo instance and assign the `snc_basic_auth_api_access` role to the administrator user, which is used to call the API. 

Finally, configure your credentials via the `SN_USERNAME` and `SN_PASSWORD` environment variables and update the `inventory/demo/snow.yml` inventory file.

### Install python dependencies
```bash
python3 -m venv .venv
source .venv/bin/activate
pip3 install -r requirements.txt
```

### Install ansible dependencies
```bash
ansible-galaxy collection install -p ./collections -r requirements.yml
```

## Test Inventory
```bash
ansible-inventory -i inventory/demo/snow.yml --host lnux100
```

## Run test playbook
```bash
ansible-playbook -i inventory/demo/snow.yml test-inventory.yml --limit sn_group_Database
```

