# system shutdown and reboot

- Only root has its permisson

System is down in some cases 

- Add or remove hardware
- upgrade my kernel
- upgrade new version of OS

## Shut-Down

```bash
init 0 --> shutdowm

poweroff --> shutdown

shutdown -h [time] --> shutdown after specific time and sends broadcast to users
                       that server will shutdown after this time

shutdown -k [time] --> it will just send the broadcast without shutting down
                       and disable the logins if anyone want to try login within time

```

## Reboot

```bash
init 6 --> to reboot

reboot

shutdown -r

or ctrl-alt-del
```