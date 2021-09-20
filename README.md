Ansible Playbooks

1. Printing messages using Playbooks

```
#Debug Module 
1a. msg
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

```
1b. Debug var
```

# Printing a variable value using a debug module
#!/usr/bin/ansible-playbook
 - Name : Usage of Debug Module
   hosts: databases
   tasks: 
   - name: Printing values using debug module
     debug:
       var: inventory_hostname

#Provide x permmissions
chmod +x debug_var_playbook.yml

#run it like this because of the #!/usr/bin/...
./debug_var_playbook.yml
        
   
```

1c. verbosity

```
#vi verbosity_debug.yml

---
 - name: usage of verbosity debug module
 hosts:
 tasks:
 - name: verbosity as default
   debug:
    msg: "this is default"
 - name: verbosity 2
    msg : "this is msg 2" 
    verbosity: 2

#run it  
ansible-playbook verbosity_debug.yml -vv
     
```

1d. prompting var playbook

```
---
 - hosts: databases
   vars:
    x: 45
    my_name: "Jon"
   vars_prompt:
    - name: user_name
      prompt: Enter your use name
      private: no
    - name: password
      prompt: Enter your password
      private: yes
   gather_facts: false
   tasks:
   - debug:
      msg: "The username is :{{user_name}} and the password is {{password}}"

```

1e. Passing cmdline args as scala.
```
x:34
ansible-playbook cmd_line.yml --extra-var "x=34"

# Or

ansible-playbook cmd_line.yml -e "x=34" or ansible-playbook cmd_line.yml -e x=34

# Or

ansible-playbook cmd_line.yml -e "{'x':34}"

# Or Passing multiple variables

ansible-playbook cmd_line.yml -e "x=34 y=89"

ansible-playbook cmd_line.yml -e "{'x':34, 'y':56}

```

1f. Passing your values as data,

```

---
 - hosts: databases
   gather_facts:
   tasks:
   - debug: 
       msg: 
       - "the x value is: {{x}}"

#runit
ansible-playbook cmd_line_args.yml -e "@variable _values.json"

```