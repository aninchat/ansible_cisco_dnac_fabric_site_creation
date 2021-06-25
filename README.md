# ansible_cisco_dnac_fabric_site_creation

In Cisco's DNA Center, and SD-Access, a site hierarchy is created, and used for mapping to a fabric, eventually allowing for fabric enabled sites. This is a fairly repetitive task, something that can be easily automated. 

This is particularly helpful for partners, or engineers that often build many proof of concept labs and quickly want to spin up a site hierarchy and fabric sites in DNAC. 

This ansible playbook uses variables that define the following:

```
1. A site hierarchy, that includes areas, buildings and floors. 
2. Fabric structure that includes fabric names
3. Fabric site information, that includes a fabric name and at what site hierarchy the fabric should be created.
```

This playbook uses the dnac ansible module, which can be found here (https://galaxy.ansible.com/cisco/dnac) and can be installed via Ansible Galaxy. 
