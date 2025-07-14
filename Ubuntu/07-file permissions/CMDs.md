# CMDs

```bash
chown [user] [file] --> to change ownership of file
chown [user]:[group][file] --> to change user and group of file
chown :[group] [file] --> to change group only #owner of file can use this cmd

chmod [options] [filename] --> modify permission of file
( u,g,o,a = rwx ) or give permessions we need , 
or sum of their octal representation --> [u][g][o]
u+s --> set user id # give this user permission as a root for this file 
# if there is 'S' in permissions --> has no effect
a+x --> give all users permission for this file
# we can use ',' to seperate from user and group and others

-R [options] [dirname] --> change permessions for all files in dir

umask --> give the default permissions that i choose # its default "0002"
# any number i write or symbol it will be deleted not performed 

# for example : umask 137 
# it will -rw-r-----
# and it will be the default for any file is been created
```