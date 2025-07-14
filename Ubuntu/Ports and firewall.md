# Ports and firewall

```bash
ss -tuln --> show info of ports in machine

ufw status --> show status of firewall
ufw enable --> to enable firewall # take care it can override the security group on cloud
ufw disable -->  to disable firewall # allow everything 
ufw allow [port] --> to open the port  #default is deny 
ufw deny [port] --> to close the port
```