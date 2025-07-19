# System Services

A **service** is a special kind of **background process** that usually:

- Starts at boot
- Keeps running quietly in the background
- Performs system tasks or handles user requests

```bash
 ## services ##

systemctl start httpd --> Start HTTPD service

systemctl stop httpd --> Stop HTTPD service 

systemctl status httpd --> Check HTTPD service Status

systemctl enable httpd --> Configure HTTPD to start now and at reboot 

systemctl disable --> Will not affect the service now but in reboot it 'll be inactive 

( enable and disable are used to start service automatically or to refresh if application
or machine crashes) 

```