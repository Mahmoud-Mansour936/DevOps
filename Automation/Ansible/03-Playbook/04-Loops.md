# 04-Loops

```yaml
# at the same level of name of module 

loop: 
 - value1
 - vlaue2
 - vlaue3

# to call the value of loop --> {{ item }}

# to make more than loop in same module 

loop: 
  - { key1: value1 , key2: value2 ....}
  - { key1: value3 , key2: value4 ....}
  
 # to call the loop --> {{ item.key1 }} , {{ item.key2 }} , ....
 # the loop will iterate over the values 
```