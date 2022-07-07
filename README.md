Create/Update Subnets in Azure
=========

A role used to create a subnet in an existing VNET in Azure

Requirements
------------

While not dependent on another role. It requires that the VNET exists and the subnet address prefix is a valid entry for the VNET.

ansible >=2.8

<https://docs.ansible.com/ansible/latest/modules/azure_rm_subnet_module.html>

Role Variables
--------------

``` yaml
# Global Vars always required:
resource_group:
# Role specific Var required:

vnet_name:
subnet_name:
subnet_address_prefix:

#optional settings
nsg_name: #This is used to refer to an NSG in the same resource group as the subnet
route_table: #referencing a route table in the same resource group

```

Dependencies
------------

Example Playbook
----------------

```yaml
---
- name: Azure Playbook to Create a Subnet
  hosts: localhost
  pre_tasks:
    - name: Setting desired state
      set_fact:  
        subnet_name: "AnsibleSubnet"
        subnet_address_prefix: "172.16.87.0/24"
        nsg_name: "security"
        route_table: "exitroute"

  connection: local
  roles:
    - azure-subnets
```

License
-------

MIT

Author Information
------------------

Adam Brassard: Abrass on IRC
