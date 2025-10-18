# Explain

## Docker storage concept

- Each image has constant layers **(read-only)** these layers can’t be deleted or edited
- When container is run image make an additional layer **(read-write)** this will be the storage of container
- But if container is deleted all data in this layer will be lost  **(non-pesistent)**
- Image layers are saved in **/var/lib/docker/overlay2** in docker host, each container has its own dir. including the (r-w) container layer
- Everything about containers like run, resume and logs in **/var/lib/docker/containers**
- Metadata of images not files are in **/var/lib/docker/image**
- So if we need persistent data and not be deleted after deletion of container we need to know about **volumes**

## Volumes

- The location where we can save the data of container **(persistent)**
- Volumes are not in /overlay2 dir.
- so we should know about its types

## Volume types

### Bind-mount

- The file created in the host and we mount it to a file in container
- Each change in host → same change in container
- If  we mount to an existing file in container → it will override this

### Named volumes

- Volumes are created in **/var/lib/docker/volumes**
- It was managed by docker
- It’s more secured , usable than bind mounting

### Anonymous volumes

- Volumes but without names → Docker manages their names
- Are deleted after removing the container 