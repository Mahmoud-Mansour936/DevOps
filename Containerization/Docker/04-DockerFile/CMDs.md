# CMDs

```bash
docker commit [container_name,id] [image-name] #image name we need with tag 
 -> to build the image from current container and saved it locally 

docker build -t [image name] [docker file directory , dockerfile in github ,..]
-> build image using docker file 

-f [dockerfile] --> we use this option if there are more than one dockerfile  

--build-arg [varaible]=[value] --> to override arg variable while building image 

```