# CMD

## PS

```bash
ps --> get all processes that running of shell
-f --> full info of these processes
-l --> more info but the important [ piriorty and nice number ]
-e --> all processes running in sys whether i used it or not # '?' sign for daemons

ps aux --> daemons processes

pstree --> tree of processes and see the parent and its children
-p --> show more visualised with PID
```

## Kill

```bash
kill [PID] --> terminate the process after its done
kill -9 --> force kill
pkill [name of ps] --> kill processes with its name
```

## Top

```bash
top --> get all processes running or not  # like task manager
htop -> better visuals than top 
```

## Pgrep

```bash
pgrep --> search for process // using pattern 
-x --> then search for exact name 
-u [UID] --> search for running processes for user // give num not name 
-l --> to show name beside the num of process
```

## Extra CMDs

```bash
sleep --> to sleep the process
& --> to sleep it in background **or any cmd not just sleep** 

fg [num of job] --> to make it in fullground # to stop it " ctrl+z "

bg [num of job] --> to make it in background

jobs --> to see status of process in background
```