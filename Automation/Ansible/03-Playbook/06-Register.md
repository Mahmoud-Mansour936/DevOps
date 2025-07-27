# 06-Register

Registers are used to save the output of task and use it in different ways

- `stdout`: Standard output (what you see in terminal)
- `stderr`: Error output
- `rc`: Return code (0 = success)
- `stdout_lines`: List of lines (splits stdout by newline)

Are used to call the register → ex. {{ var.stdout }}

```yaml
# at the same level of name of module 
register: var

# the output is saved in var and to call it {{ var.[one of above variables] }}
```