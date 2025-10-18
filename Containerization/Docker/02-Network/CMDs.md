# CMDs

```bash
docker network ls --> list all docker networks

docker network inspect <network> --> show detailed info about a specific network

docker network create <name> --> create a new bridge network with default settings

docker network create --driver <driver> <name> 
--> create network with a specific driver (bridge, host, none, overlay)

docker network create --subnet <subnet> --gateway <gateway> <name>
 --> create network with custom subnet & gateway
 
 docker network create <name> --internal --> act as a private LAN between contaienrs
 no internet access ( inbound , outbound )
 
docker network rm <network> --> remove a specific docker network

docker network prune --> remove all unused networks

docker network connect <network> <container> 
--> connect a running container to a network

docker network disconnect <network> <container>
--> disconnect a running container from a network

docker run -it --network <network> <image> <command>
 --> run a container attached to a specific network # Bridge is default
```