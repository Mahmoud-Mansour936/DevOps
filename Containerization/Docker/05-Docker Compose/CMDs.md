# CMDs

## Download docker compose

### Download docker compose from GitHub

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/v2.38.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

### Make the file executable

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

## Run the file

- At the dir of docker-compose file

```bash
docker-compose up 
-d --> for background process
--build --> force building the images from scratch
```

## exec

```bash
docker-compose exec <name of service> <cmd> # don't need to write id or name of container
```

## Remove

```bash
docker-compose down
 # will delete containers and networks 
 # won't delete images and volumes
 
--rmi --> delete images 
 
 -v --> delete volumes 
 
```