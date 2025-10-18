# 01-Introduction

## Why automation is important

- Repeatability and Consistency
- Saves Time and Effort
- Testing and Validation
- **Scalability**
- Security and Compliance

## What is Ansible?

- Ansible is a configuration management tool that automate the configuration tasks
- It’s considered as one of types of IAC tools
- Make the repetitive tasks → execute tasks from own machine ( contol_machine )

## Advantages

- Uses simple syntax of Yaml files
    - Declarative: Using modules that make one simple task (simpler than bash)
- Agentless: Target machines (Hosts) shouldn’t have ansible be installed on them to connect (just python)
- Connect via ssh → High security level
- Idempotency: checks that tasks were executed before or not → to not make the same commands again