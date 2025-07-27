# 02-Inventory file

- Inventory file contains the description of servers we need to connect [ IPs - hostnames]
- The servers could be in groups to select from as we want
- One server could be in more than one group
- Inventory files end by **.ini** extension
- This file is created by default in **/etc/ansible/hosts** but it’s recommended to be in same directory of playbook file
- If there’s no ssh variable to put in it the file of private key → **id-rsa** file by default

## Basic stucture

```bash
[group1]
ip_1  ansible_ssh_private_key_file=[path of private key]  
ip_2

# To make constant variables for specific group
[group1:vars]
ansible_user=ubuntu  ansible_ssh_private_key_file=[path of private key]

# Variables for all users 
[all:vars] 
ansible_user=ubuntu 

```