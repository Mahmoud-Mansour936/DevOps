# 02-Vault (for encryption)

- We use encryption because if there are usernames or passwords files and we will upload it to GitHub, we don’t want GitHub to see them just ansible will see them during running the playbook
- Vault password files are used for automation, but it must be hidden or encrypted too, so in pipeline we put these files in credentials

```bash
ansible-vault encrypt [file] -> to encrypt the file 
# if there are variables in the file we can call it by using {{  }} like any variable
# and ansible will see it in running the playbook

ansible-vault decrypt [file] -> to decrypt the file 

ansible-vault view [file] --> to view the file without decryption

ansible-vault edit [file] -> to edit the file without decryption

```