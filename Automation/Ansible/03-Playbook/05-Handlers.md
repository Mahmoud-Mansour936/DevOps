# 05-Handlers

Handlers are used when we need to run a task depending on running of another task 

when task == changed → handler run 

```yaml

# after tasks and in the same level of it 
  
handlers: 
 - # module we need 
 
 # then in task we need to apply handler on it 
 # at the same level of name of module 
 notify: [name of handler] 
```