# 07-Roles hierarchy

- In bigger playbooks with a lot of modules and tasks we use the roles
- A **role** is a structured way to organize Ansible playbooks.
- Helps **reuse code**, keep things **modular**, and **clean**
- We make a directory called **roles,** then we name our roles as we want

## Directory Structure of a Role

```bash

 myrole/
 ├── tasks/
 │   └── main.yml
 ├── handlers/
 │   └── main.yml
 ├── templates/
 │   └── *.j2
 ├── files/
 │   └── *
 ├── vars/
 │   └── main.yml
 ├── defaults/ # it overrides the vars in playbook
 │   └── main.yml
 ├── vars/ # it doesn't override the vars in playbook
 │   └── main.yml
 ├── meta/
 │   └── main.yml
 ├── tests/
 │   ├── inventory
 │   └── test.yml

```

### 1. **tasks/**

- Contains the main tasks to execute.
- Entry point: **`tasks/main.yml`**.
- Can include other task files using `include_tasks` or `import_tasks`.

### 2. **handlers/**

- Stores handlers (triggered by `notify`).
- Entry point: **`handlers/main.yml`**.

### 3. **templates/**

- Jinja2 templates for configuration files.
- Example: `nginx.conf.j2`.

### 4. **files/**

- Static files to be copied to hosts.

### 5. **vars/**

- Variables with **higher precedence** than defaults.
- Entry point: **`vars/main.yml`**.

### 6. **defaults/**

- Default variables (lowest precedence).
- Entry point: **`defaults/main.yml`**.

### 7. **meta/**

- Role metadata:
    - Dependencies on other roles.
    - Author, license, etc.

### 8. **tests/**

- Test playbooks for the role.

## In playbook

```yaml
# Instead of tasks --> roles 

roles: 
 - role1
 - role2 
 - role3
```

## Important notes

*** The names of each directory or file can’t be changed , just the name of role can be changed

*** The role can be more than one task