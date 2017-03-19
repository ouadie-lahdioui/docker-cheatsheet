# Docker cheat sheet ❯ https://goo.gl/uRWLFS
> Useful tips & tricks to learn build and deploy your distributed applications easily to the cloud with Docker !

- Want to improve this cheat sheet ? your PRs are welcome
- With :heart: by [Ouadie LAHDIOUI](http://www.twitter.com/lahdiouiouadie)

<p align="center">
	<a href="https://goo.gl/uRWLFS" target="_blank">
	    <img src="assets/talk-splash-screen.png">
	</a>
</p>

## Install Docker
- Check the [installation guide](http://docs.docker.com/engine/installation) for your platform

## Try It Out
```
docker version
docker -v
docker info
```

## Docker CLI basics
- ```docker ps``` Shows all containers that are currently running
- ```docker ps -a``` Shows all containers
- ```docker images``` : See a list of all images on your system
- ```docker rm <CONTAINER_ID> <CONTAINER_ID>``` Remove containers by id
- ```docker rmi <IMAGES_ID> <IMAGES_ID>``` Remove images

## Launching a container
- ```docker run [options] [image] [process]```
- ```docker run hello-world``` Verify your system
- ```docker run busybox``` Run a Docker container based on an image
- ```docker run busybox echo "hello from busybox"```  Run an empty command and then exit
- ```docker run --rm <CONTAINER_ID>``` Start a container automatically removed on stop
- ```docker pull <IMAGE_ID>``` Fetches the busybox image from the Docker registry and saves it to your system
- ```docker start <CONTAINER_ID>``` Restart a stopped container
- ```docker stop <CONTAINER_ID>``` Stop a container

## Run the container in interactive mode
- ```docker run -it busybox sh``` Run a container in interactive mode (type exit to close)
- ```docker run -t -i ubuntu /bin/bash``` launch an Ubuntu container and install what you want inside (Ex: apt-get update && apt-get install apache2) 

## Run the container in background 
- ```docker run -d <CONTAINER_ID>```

## Committing a container
- ```docker commit <CONTAINER_ID> ouadie/busybox```   

## Cleaning Up
- ```docker rm <CONTAINER_ID>``` Remove a container
- ```docker rmi <IMAGE_ID>``` Remove images
- ```docker rm $(docker ps -a -q)``` Remove all containers
- ```docker rmi $(docker ps -a -q)``` Remove all images

## Build Images
- ```docker build --tag myimage .``` Build an image from Dockerfile in current directory

## Network access to 80
- ```docker run -d -p 80:80 coreos/apache /usr/sbin/apache2ctl -D FOREGROUND```

## Using the Docker registry
- ```docker push coreos/apache``` Push to the public registry    
- ```docker push registry.example.com:5000/apache``` Push to a private registry    

## Linking Containers
- TODO

## Using Docker Hub
- [Sign up for an account](https://hub.docker.com/register/)
- Add a new repository, for example : https://hub.docker.com/r/ouadie/docker-cheatsheet
- ```docker tag <IMAGE_ID> ouadie/docker-cheatsheet:latest|v1.0``` Tag your docker image using
- ```docker login``` Log in 
- ```docker push ouadie/docker-cheatsheet``` Push your image 
- ```docker search tomcat``` Search for an image 
  
  
## Dockerfile
Dockerfile allows developers to build Docker images automatically. It contains a list of commands. 

It has the format : 
- ```INSTRUCTION arguments``` INSTRUCTION is not case-sensitive but convention says it ought to be uppercase to be easily distinguished from arguments. 

Main commands : 
- ```FROM imageName[:version]``` imageName is the name of the Docker Image in [docker hub](https://hub.docker.com/). If the version is not specified, Docker takes the latest. 
- ```MAINTAINER creator``` Information about the creator of the image. (deprecated)
- ```COPY <src> <dest>``` This command copies files or directories from ```src``` to the filesystem of the container at ```dest```. If all files should be copied, _src_ can be : "."
- ```RUN <command> ``` or ```RUN ["exec", "param1", "param2"]``` Commands are in shell form or exec form.
- ```CMD <command>``` Commands in RUN are also in shell and exec form. In a Dockerfile, only one CMD instruction should be written, otherwise, only the last one will taken into consideration. It is the process to execute. 
- ```EXPOSE <port> [<port> ...]``` At runtime, the container will listen on the specified ports. 
- ```ENV <key> <value>``` ENV sets the environement variable ```key``` to the value ```value```. 

Build : 
- ```docker build -t appName .``` Build Docker image using the Dockerfile in the root of the context. 
- ```docker build -f path/to/Dockerfile .``` Use ```-f``` to build a Docker image from anywhere in your file system.