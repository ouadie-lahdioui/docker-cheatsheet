# Docker cheat sheet ❯ https://goo.gl/uRWLFS
> Useful tips & tricks to learn build and deploy your distributed applications easily to the cloud with Docker !

- Want to improve this cheat sheet ? your PRs are welcome
- With :heart: by [Ouadie LAHDIOUI](http://www.twitter.com/lahdiouiouadie)

<p align="center">
	<img src="assets/docker-logo.png">
</p>

## Install Docker
- Check the [installation guide](http://docs.docker.com/engine/installation) for your platform

## Try It Out
```
docker version
docker -v
```

## Docker CLI basics
- ```docker images``` : See a list of all images on your system
- ```docker ps``` Shows all containers that are currently running
- ```docker ps -a``` Shows all containers
- ```docker rm <CONTAINER_ID> <CONTAINER_ID>``` Remove containers by id
- ```docker rmi``` Remove images

## Launching a container
- ```docker run [options] [image] [process]```
- ```docker pull busybox``` : Fetches the busybox image from the Docker registry and saves it to your system
- ```docker run busybox``` : Run a Docker container based on an image
- ```docker run busybox echo "hello from busybox``` : Run an empty command and then exit

## Run the container in interactive mode
- ```docker run -it busybox sh``` Run a container in interactive mode (type exit to close)
- ```docker run -t -i ubuntu /bin/bash``` launch an Ubuntu container and install what you want inside (Ex: apt-get update && apt-get install apache2) 

## Run the container in foreground
- ```docker run -D ouadie/busybox [process]```

## Committing a container
- ```docker commit <CONTAINER_ID> ouadie/busybox```   

## Cleaning Up
- ```docker rm <CONTAINER_ID>``` Remove a container
- ```docker rmi <IMAGE_ID>``` Remove images
- ```docker rm $(docker ps -a -q)``` Remove all containers
- ```docker rmi $(docker ps -a -q)``` Remove all images

## Network access to 80
- ```docker run -d -p 80:80 coreos/apache /usr/sbin/apache2ctl -D FOREGROUND```

## Using the Docker registry
- ```docker push coreos/apache``` Push to the public registry    
- ```docker push registry.example.com:5000/apache``` Push to a private registry    

## Linking Containers
- TODO

## Using the Docker registry
- TODO

## Dockerfile
- TODO

## Webapps with Docker
- TODO   

## ChatBots with Docker
- TODO   

