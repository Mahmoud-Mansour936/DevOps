# CMDs

## Docker basics

```bash
docker --version --> Shows the installed Docker version.

docker info --> Displays system-wide information about Docker.

docker help --> Lists available Docker commands or helps with a specific command.

docker ps --> Lists running containers.
-a --> Lists all containers, including stopped ones.
-q --> shows only IDs of containers 

docker logs <container_name> --> show logs of container
-f --> show live logs   
```

## Docker image

```bash
docker images --> Lists all Docker images on your system.

docker pull <image_name> --> Downloads an image from Docker Hub.
docker pull <acc>/<image_name> --> if the image is unofficial
docker pull <repo_name>:latest --> pull latest version
 # latest is the latest tag or version
 
docker rmi <image_name> --> Deletes a Docker image.
-f --> force remove

docker image prune -> delete all unused images 

docker save <image_name> -> make an archived file of an image 

docker load <archived_image_file> -> turn this file to image 
# we can use this way to transfer the images using disks or ssh as we want 

```

## Docker Container

### Running containers

- network and volume options in their note

```bash
docker container run <image_name> --> Runs a command in a new container based on an image.

-it <image_name> <shell> --> create a container and enter the terminal or 
( start the terminal only not other package -> bash :  pid=1 ) .

-d <image_name> --> Runs a container in the background (deatached mode).

-dit --> run in background and run a process to not be exited after creation

--rm --> to remove contianer when it exits

--name <name we need> <image name> --> change name of container

-h <needed host_name> --> change hostname of container

-c <cmd> --> to execute command inside the container

-p <host_port>:<container_port> -> flag maps a port on your host machine to a port
inside the container.

-p <ip>:<host_port>:<container_port> -> only this ip will reach container using port

--ip --> static ip 

--entrypoint <cmd> <image-name> --> cmd will override the entrypoint instruction
 and will be the main process 
 
 -e --> make environment variable or override what in docker file , even of the system
 
 --env-file <file> --> take needed environment variables from file 
 
 
 

```

### Copy

```bash
docker container cp <source_file> <container_ID:destination file> -> copy file from
host to container

docker container cp <container_ID:destination file> <destination_file>  -> copy file 
from container to host 
```

### list

```bash
docker container ls --> show running containers 
-a --> show all containers
```

### Service

```bash
docker stop <container_id> --> Stops a running container.

docker start <container_id> --> Starts a stopped container.

docker restart <container_id> --> Restarts a container.

docker rm <container_id> --> Deletes a container. # it must be stopped 
-f --> force remove
```

### exec

```bash
docker exec  <container_id> <cmd> --> excute command for container

docker exec -it <container_id> <shell> --> enter the container and excute what i want 
inside it.

# it was like u give container process to do 
# container must be running 
```

### info

```bash
docker inspect <container_id> --> all data about container

docker stats <container_id> -->  gives live metrics about how much CPU, memory, network,
and disk I/O each container is using.

docker top <container_id> --> shows the processes running inside a container
```