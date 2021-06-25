# ansible_cisco_dnac_fabric_site_creation

In Cisco's DNA Center, and SD-Access, a site hierarchy is created, and used for mapping to a fabric, eventually allowing for fabric enabled sites. This is a fairly repetitive task, something that can be easily automated. 

This is particularly helpful for partners, or engineers that often build many proof of concept labs and quickly want to spin up a site hierarchy and fabric sites in DNAC. 

This ansible playbook uses variables that define the following (these variables are under the 'vars' folder):

```
1. A site hierarchy, that includes areas, buildings and floors. 
2. Fabric structure that includes fabric names
3. Fabric site information, that includes a fabric name and at what site hierarchy the fabric should be created.
```

This playbook uses the dnac ansible module, which can be found here (https://galaxy.ansible.com/cisco/dnac) and can be installed via Ansible Galaxy. 

Note: it feels extremely inefficient to include common variables like DNACs IP address, username, password for every task in this playbook. However, this is a limitation of how the dnac ansible module is built and moving these variables to something like group_vars/ does not work. You will continue to see the following error:

```
(python3.8) aninchat@aninchat-ubuntu:~/Automation/Ansible/dnac$ ansible-playbook -i hosts.yml test_playbook.yml

PLAY [dnac1] ********************************************************************************************************************************************************************

TASK [Get configured discovery jobs on DNAC] ************************************************************************************************************************************
fatal: [dnac1]: FAILED! => {"changed": false, "msg": "missing required arguments: dnac_host"}

PLAY RECAP **********************************************************************************************************************************************************************
dnac1 : ok=0 changed=0 unreachable=0 failed=1 skipped=0 rescued=0 ignored=0
```

Thus, for now, please make sure that you include 'dnac_host' and all necessary information that is required, under every task.
