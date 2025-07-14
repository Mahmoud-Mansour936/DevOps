# Explain

## Configuration Files

### **/etc/passwd** file

-  Every user has line contains its info 

- The file in Ubuntu contains 7 fields separated by colons:

                                                     x:x:x:x:x:x:x:x

- **Username** : The name used when logging into the system
- **Password** : An 'x' indicating that the encrypted password is stored in /etc/shadow
- **User ID (UID)** : A unique number assigned to each user

   0:100 → for OS               100:1000 → for APPs                     1000:∞ → for users 

- **Group ID (GID)** : The primary group ID for the user
- **User Info** : Optional field for additional user information (full name, contact info)
- **Home Directory** : The absolute path to the user's home directory
- **Login Shell** : The program that launches when the user logs in (e.g., /bin/bash)
- **Example entry** : username:x:1000:1000:Full Name,,,:/home/username:/bin/bash

** Every software in linux has a user so it’s more secured

### **/etc/shadow** file :

 - This file contains the actual password information and is accessible only by the root user for        security.

 - Like /etc/passwd, it also contains fields separated by colons:

                                                              x:x:x:x:x:x:x:x:x

- **Username**: The login name of the user
- **Encrypted Password**: The user's password in an encrypted format
- **Last Password Change**: Days since Jan 1, 1970 that the password was last changed
- **Minimum Days**: Minimum days required between password changes
- **Maximum Days**: Maximum days the password is valid before requiring change
- **Warning Period**: Days before password expiration that the user is warned
- **Inactivity Period**: Days after password expiration until the account is disabled
- **Expiration Date**: Days since Jan 1, 1970 that account will be disabled
- **Reserved Field**: Reserved for future use
- **Example entry**: username:$6$hash...hash:18678:0:99999:7:::

** The encrypted password field starts with $id$salt$hashed, where $id indicates the encryption algorithm used.

### **/etc/group** File :

- This file stores group information, containing the following fields separated by colons:

x:x:x:x

- **Group Name**: The name of the group
- **Group Password**: Usually just an 'x' indicating the password is stored elsewhere
- **Group ID (GID)**: The unique numeric identifier for the group
- **Group Members**: A comma-separated list of users who are members of this group
- **Example entry**: developers:x:1001:user1,user2,user3

** Users can belong to multiple groups, which determines their file access permissions

### **/etc/gshadow** File :

Like shadow file but for groups not users 

## Notes :

- Each user should be in at least one group
- There are 16 groups can be secondary groups for user
- When deleting user with its home dir , but he created files in another home dir for another user → these files have no user and can be deleted
- It’s recommended to make the name of group in **small letters**
- We can give specific group limited permissions as a root → by editing **/etc/sudoers** file