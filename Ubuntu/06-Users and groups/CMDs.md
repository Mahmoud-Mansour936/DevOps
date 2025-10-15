# CMDs

## Users CMDs

```c
useradd --> to add user 
-u --> to add id to this user // by default it will be after the higher id 
-g --> write the user who want to make ur user to be in a group with
// useradd -g user1 user2 --> user2 will be in user1's group not the opposite
-G --> the secondary group
-aG --> to add secondary group
-c --> write comment // write it between ""
-m --> to make dir for user
-d --> to give name to dir of user
-s --> to give the path of shell 
-l -> change username
-L -> lock account
/* after configuration of user never forget to write name of user at the last because 
 it the argument of 'useradd' cmd
 */
 
 
 su --> switch to user 
 - <user> --> to enter the enviroment of this user 
 -c <cmd> --> to do a cmd with this user for one time
 
 
 usermod --> to modify the user // same options of add
 
 
 userdel --> delete user 
 -r --> to delete user with its home dir
```

## Password

```c
 passwd --> put the passwd of user 
 
 
 chage --> change password
 -m --> change min 
 -M --> change max
 -E date --> change expiration date
 -W --> change warn
 -i --> change inactive days
 
 
 gpasswd -d --> remove user from group
```

## Groups CMDs

```c
 groupadd --> to add group
 -g --> to make ID of the group not in the range of users group
 //we need this tif we make a group without primary user to make userid and gid the same
 
 
 groupmod --> modify group
 -n --> modify name
 
 
 groupdel --> delete group // if it's not primary group for any user
 
 
 chgrp <group> <file> --> change file's group 
 // owner of file can make this cmd and member in group which want to change into
 
 
 newgrp --> change primary group temporarily 
 // use it to not chnage group every time i want to make file in another group
 // and we can return to our primary group using "exit" cmd
 
 
 groups --> show all groups iam member in it // first is primary 
```
## To make system not to ask for sudo password

Open the sudoers file safely:

```bash
sudo visudo

```

Add this line at the end (replace `your_username` with your actual username):

```bash
your_username ALL=(ALL) NOPASSWD: ALL

```
=======
```

