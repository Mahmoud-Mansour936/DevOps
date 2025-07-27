# 01-Basic structure

```yaml
- name: Install and Start Apache Web Server # value of list of play that one play is list of playbook
  hosts: webservers # group or all in inventory file 
  remote_host: ubuntu # for one machine if more than one -> write it as vars in inventory
	become: true # to give sudo permission if task need sudo   
	

  tasks:
    - name: Install apache2 package
      apt:
        name: apache2
        state: present
        update_cache: yes

    - name: Ensure apache2 is running
      service:
        name: apache2
        state: started
        enabled: yes

				 
```