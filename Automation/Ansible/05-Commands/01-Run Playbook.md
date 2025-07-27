# 01-Run Playbook

```bash
ansible-playbook -i [inventory_file] [playbook_file] --> to run the playbook

ansible-playbook -i [inventory_file] [playbook_file] --ask-vault-pass 
--> will ask for vault pass if there are encrypted files 

ansible-playbook -i [inventory_file] [playbook_file] --vault-password-file [pass_file]
--> to see the vault password from file # for automation

ansible -i [inventory_file] -m [module] -a "[arguments of modules]" # between ""
 --> run module without playbook for simple commands
 -b --> for sudo # like become in playbook
 
 
```