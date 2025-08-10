# CMDs

## Hostname

It will show the name if no argument 

If i give it name ,  it will be changed 

It will be temporarily until shutdown device if i want it along time
i must change "**/etc/hosts file**" 

```bash
hostname --> show or change the name of device
```

## Ping

ping uses ICMP protocol and it’s different from connecting via ports 

ping connection can be established but the access to ports could be denied  

```bash
ping --> test the connection 
-c [num] --> num of packets to be sent
```

## IP

```bash
ip a --> list all interface names of nic 
# or i can list the " /sys/class/net "
 
ip addr add [ip] dev [cable] --> to add ip 
# it will be removed after restart if i want it permenantly --> edit in /etc/netplan file 

ip addr del [ip] dev [cable] --> delete ip 
```

## SSH

### Step 1 : generate the public and private keys

```bash
ssh-keygen -t [type] -b [bytes] --> to generate the public and private keys

# the " type " must be the same type of system ( usually use **rsa** )

# it will ask for file to save the keys --> make file in **~/.ssh** dir

# it will ask for passphrase that if the key is leaked it required password 
# not recommended for automation to not stop the pipeline
```

### Step 2

```bash
mkdir ~/.ssh
chmod 700 ~/.shh
cd /.ssh
touch authorized_keys 
chmod 600 authorized_keys
# this file will be in target machine 
```

### Step 3

we take this public key and copy it in **~/.ssh/authorized_keys** file to save it in machine 
we want to connect to 

### Step 4: connect to the machine

```bash
ssh -i [private key file] [username]@[remote_host ip] --> to connect via ssh
```

### ##important notes

```bash
# make sure that port 22 is enabled by 
sudo ufw allow 22
sudo ufw enable

# make sure that u install all updated packages of ssh
sudo apt update
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh

```

### To make ssh doesn’t require password or ( yes, no ) checking for pipeline

 

```bash
# 1st method 
# make a file in ansible dir with **.cfg** extension and write
host-key-checking= false 
# Skips SSH fingerprint verification.
# Possible **security risk** in production unless controlled tightly.
# can be used for ( test - demo - temp ) VMs

# 2nd method 
ssh-copy-id user@remote_host[IP]
# Command used to copy your public SSH key to a remote server,
# so you can log in without a password.
# can be used for long-live VM

# 3rd method
ssh-keyscan [IP] >> ~/.ssh/known_hosts
# This tool fetches the public host key of a remote server,
# and outputs it in known_hosts format.
# can be used in **Pipelines**
```

## Another CMDs

```bash
nslookup [url] --> server and ip of this site 
dig [url] --> more info than nslookup

traceroute [url , ip ] --> see all hobs or layers to connect this url 

curl [url] --> check the api of webserver by HTTP/HTTPS protocols /* it will show the 
raw HTML code */
-o [page.html] --> saves the output to a file named page.html

```
