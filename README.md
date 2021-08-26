Ansible Playbooks

1. Printing messages using Playbooks

```
#Debug Module

---
 - hosts: databases
   tasks: 
   - debug: msg="Welcome to Ansible" 

   
   
#run playbook   
ansible-playbook print_msg.yml

#check syntax on cmd before running Playbook
ansible-playbook print_msg.yml --syntax-check

#Adding Name section and multiple messages

---
 - Name : This a Debug Module Name
   hosts: databases
   tasks: 
   - name: 
     debug:
       msg: msg="Welcome to Ansible" 
        - "More messages"
        - "Basic comcepts"


# Printing a variable value using a debug module
#!/usr/bin/ansible-playbook
 - Name : Usage of Debug Module
   hosts: databases
   tasks: 
   - name: Printing values using debug module
     debug:
       var: inventory_hostname

#Provide x permmissions
chmod +x debug_var_playbook 

#run it
debug_var_playbook
        
   


```