# Basic structure

## Single stage

```docker
FROM [image]:[tag]
# Define the image we need
# If tag doens't exist -> the latest version by default
FROM scratch 
# Build the image from scratch , just has the kernel of docker host

WORKDIR [dir] 
# Like cd to go to dir if exist , if not it will be created 
# It's recommeneded to give the full path

COPY [file] . 
# It's preferred to type full path from build context of file we need to copy
# We can give more than one file 
# It will copy files from build context to dir in container , using "dot" sign 
# the dot sign referred the current dir in image 
# if we need specific dir we write it like /dir/ to know that was a dir not renamed file
COPY *.txt /dir/ 
# It copies all files end with .txt to /dir  
COPY . /dir/ 
# It copies all files to /dir 
COPY ["name with spcaes.txt" , "/app/"]
# If file name contains spaces , it's called exec_mode 

ADD [file] 
# Copy files don't exist in machine like from internet or github ..
# If u copy .tar file -> will be copied unziped 

SHELL ["needed shell","-c"] 
# Changes using shell in build_time

ENTRYPOINT ["cmd","arg1"] 
# Used to execute the main process of container and it was fixed 
# We can give it the arguments by this way or by CMD instruction
# We can put needed shell in it to be as a main process 
# It can be overrided by using --entrypoint while running container 
# Arguments can be given at the last of run command 

  

RUN [cmd] 
# Executes commands at build time of image 
# It doesn't take any inputs , take care of commands you will use with RUN
# All commands will be terminated after the intermediate containers are terminated 
RUN ["cmd","arg1","arg2"] 
# It has also exec mode and it's recommended 

CMD [cmd] 
# Executes command during running the container " run time "
# If you write more than one CMD instruction,
# only the last one will take effect , all previous CMD instructions are ignored.
# So if we need more than one -> make bash script has all commands u need and run it
# We can use it as arguments of entrypoint 
# It can be overrided while running container without --entrypoint

EXPOSE [port] 
# Exposing the needed port 
# in run time 

ENV [name]=[value] 
# To give value to variable 
# Note : we can do it by "export" cmd but during the build time the shell will be exited 
# and all its variables will be deleted so we use ENV to keep it safe 
# We can use environment variables of base image 
ENV [name1]=[value1] [name2]=[value2]
# To make more than one variable 

ARG [name]=[value] 
# define variables that are passed at build time
# Not available inside the container at runtime
# Can be overridden with --build-arg when running docker build

USER [user] 
# Switches the current used user like 'su' cmd 
# 'su' cmd doesn't exist in all images so we use 'USER' instruction

HEALTHCHECK CMD ["cmd"]
# HEALTHCHECK in a Dockerfile tells Docker how to check if the container is still healthy (e.g., the app inside it is running properly).
# The container could be unhealthy :
# - Port is undefined 
# - wrong command 
# - App doesn't start 

```

Difference between RUN and CMD 

| Feature | `RUN` | `CMD` |
| --- | --- | --- |
| 🕒 When it runs | **During image build** (`docker build`) | **When the container starts** (`docker run`) |
| 🧱 Purpose | To modify the image (e.g., install software) | To define what the container **does** |
| 🧠 Result saved? | ✅ Yes, image is changed | ❌ No, just sets default behavior |
| 🔄 Overridable? | ❌ No | ✅ Yes — can override with `docker run` |

## Multi-stage

- Multi-stage uses more than one image in same docker-file
- It deletes the used image to work on the next image → Optimize the space of machine and more secure

```docker
From [image] 

# instructions

From [image] 

#########################################################################################

From [image] AS [name]
# That gives a nickname to image to call it if we need 

# instructions

From [image] 

COPY --from=[name] [src] [dist]
# Used to take files from previous image 
# Note that if the source is dir has some files -> will copy the content only not 
# whole dir.

```