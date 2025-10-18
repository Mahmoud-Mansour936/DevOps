# Basic Structure

```yaml
# we write version of docker compose and this key is the only required key
version: "version of docker compose"

# create service , service = one or more container 
# attach image , networks and volumes
services:
	serv1:
		image: "image-name:tag"
		ports:
		 - "[host-port]:[container-port]"
		networks: 
			net1:
				internal: true 
				# make contaienrs connect to each other internally without internet
		volumes:
			- type: volume  # type of volume
				source: vol1  # which volume u choose
				target: /dir  # where this volume will be mounted in container
				
				# bind volume
			- "[Full path of dir in host]:[path in container]" 
			
		environments: 
		 - var1=value1
		
		env_file:
		 - ./env   # envrionments file 
		 - ./env2  # we can use more than one file
		
		restart: always # Always restart, no matter the exit status
		
				
	serv2:
		build: 
		 context: .  # this will use image was built from dockerfile in build context 
		 dockerfile: [dockerfile-name]
		 args:  # like ARG in dockerfile 
		  - arg1
		  - arg2
		  
		restart: on-failure # Restart only if the container exits with an error (non exit 0)

# create Networks 
networks:
	net1:
	
# create Volumes 
volumes:
	vol1:

```