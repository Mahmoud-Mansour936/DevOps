# Variables

## Local variables

```bash
name="VAR" # string must be between double quotes and no spaces around equal sign 
num=5 # numbers shouldn't be bwtween double quotes but it's recommended to put it 

to use the variable we but **$** before the name of variable  

# if u want to print $name as a string --> **write \ before it** 

echo $name 

echo="${num} linux" --> to concatenate string with variables we put variable between 
**curly brackets**

to increment variable --> i=$((i++))
to sum 2 variables --> sum=$(( num1 + num2 )) # no problem with spaces 

```

## Environment Variables

they are reserved variables in system 

```bash
city , date , PWD 

to get them use **env** command

to make ur own reserved variable in system --> 
1 - open ~/.bashrc file 
2 - write export variable_name=variable
3 - source ~/.bashrc --> to read the file again and export the variable
```

## Predefined Variables

they are variables that takes argument during runtime or from shell beside running the file 

```bash
echo $0     # Script name
echo $1     # First argument , **$2** is second and so on .. 
echo $@     # All arguments
echo $*	    # All arguments (as a single string)
echo $#     # Number of arguments
echo $$     # PID of the script
echo $?     # Exit status of last command
```