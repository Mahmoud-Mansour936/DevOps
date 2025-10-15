# CMDs

## Bind-mount

```bash
 docker container run -v <Full path of dir in host>:<path in container> -->
 to make dir mounting in container from host 
 # it's like a shortcut any edit in host the container will be updated 
```

## Named volumes

```bash
 docker volume create <name of volume>--> to create volume 
 # then use -v in run cmd to mount this volume
 
 docker run -v <name of volume>:<path in container> -> mount the volume 
```

## Anonymous volume

```bash
docker run -v <path in container> -> mount the anonymous volume 
# Docker gives name to this volume 
```