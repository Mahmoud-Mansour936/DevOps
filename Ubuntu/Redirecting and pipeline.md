# Redirecting and pipeline

## Redirecting

```bash
cmd > [filename] --> it will put output of cmd in this file
# if file no exist it will be created
# if we make it again -> output will be overwritten on what in file

cmd >> [filename] --> output will be appended on what in file

cmd < [filename] --> take input from file
# if something changed in this file it won't be saved 
# so we  want to save it in another file by " cmd < [file1name] > [file2name] " 
# file 1 still like itself and 2 will change 
# if we write same file --> data will be deleted
 
 cmd 2>error --> will put errors in "error" file
 # if i want the file only without errors --> " **>2/dev/null** " null like recycle bin"
 
 

```

## Pipeline

```bash
 cmd1 | cmd2 | cmd3 
 
 # output from cmd1 will be saved in buffer then it will be sent as an input 
 # to next cmd and so on
```