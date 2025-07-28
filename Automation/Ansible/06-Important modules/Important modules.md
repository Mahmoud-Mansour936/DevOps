# 06-Important modules

builtin collection

- file
- copy  → override
    - in dest we should write full path not shortcuts like ~ or .
- lineinfile → add line
- replace → regxp
- user
    - absent → delete user
    - remove → delete home dir
- apt
    - purge: yes → delete all conf files related to package
- service
- command vs shell
    - Command: used to write one command if not exists in any module
    - Shell: like command but use shell powers like ( pipeline , redirecting , env variables .. )
    - Command is safer than shell because of shell injections so if it doesn’t need to use shell use command
    - Both of them are not idempotent
- get_url → like curl command Downloads files from HTTP, HTTPS, or FTP to node
- apt_repository → Add and remove APT repositories