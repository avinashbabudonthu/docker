# Docker Commands
* Check docker version
```
docker -v
docker --version
```
* Information of docker container environment
```
docker-machine env
```
* To see docker images
```
docker images
```
* To see all docker containers both started and stopped
```
docker ps
docker ps --all
docker container ls
docker container ls -a
docker container ls --all
```

* Start the container by running image
	* `-it` - Interactive terminal
	* `-p 9080:8080` - Does port mapping. 9080 == port number on the host system where container is running. 8080 == port number of application running in the container. We are mapping 8080 port of container to 9080 port on our system, so we can hit url with 9080
```
docker run -it -p 9080:8080 image-name
```
* Give name to docker container while starting the container
```
docker run -d --name applicationName -p 8080:8000 imageName
```
* Stop docker container
```
docker stop [container-id]
```
* Start docker container
```
docker start [container-id]
```
* Installed Docker information
```
docker info
```
* Docker installation path
```
where docker
```
* Run nginx using docker
```
docker run -p 80:80 nginx
```
* Pull image from docker central repository - docker hub
```
docker pull image-name
Ex: docker pull ubuntu
```
* Run the container as daemon. Means run the container in the background
```
-d
```
* Logging into and accessing the container
```
docker exec -it [container-id] bash
```
* Exit the container accessed using command `docker exec`
```
exit
```
* Kill docker container
```
docker kill [container-id]
```
* To remove a stopped container from system
```
docker rm [container-id]
```
* To remove image from system
```
docker rmi [image-name]
```
* To remove a running container from system
```
docker rm -f [container-id]
```
* Save container changes. New image is created which can be seen under 'docker images' with the same name passed in the command
```
docker commit [container-id] [name-for-new-image]
```
* Remove all the containers running or stopped present in the system
```
docker rm -f $(docker ps -a -q)
```
* Login to docker hub from cmd. Enter username and password
```
docker login
```
* Push local docker image to docker hub
```
docker push [image-name]
```
* Build docker image using Dockerfile. Run from directory where Dockerfile is present
```
docker build . -t [image-name]
```
* Bind mount C:/docker/dockerfile from local system to /app folder in container
```
docker run -it -v C:/docker/dockerfile:/app -d image-name
```
* Create docker volume
```
docker volume create [volume-name]
```
* To use the volume while running the container
```
docker run -it --mount source=[name-of-volume],target=[path-to-directory-in-container] -d [image-name]
```
* List docker volumes
```
docker volume ls
```
* Copy files to container
```
docker cp [file-path/file-name] [container-id:/path-in-side-container]
```
* Run docker commands in linux machine without running sudo every time
```
sudo usermod -aG docker $USER. Re login to session after running this command
```
* Check logs of container
```
docker logs [container name]
```

# Docker Compose
* Docker compose version
```
docker-compose --version
```
* Docker compose file name should be
```
docker-compose.yml
or
docker-compose.yaml
```
* Run docker compose
```
docker-compose up -d
```

# Docker Swarm Commands
* Start docker swarm and act as leader. This generates command for worker to join
```
docker swarm init --advertise-addr=[ip-address-of-master]
```
* List of docker nodes in docker swarm cluster
```
docker node ls
```
* Create service in docker swarm
```
docker service create --name [name-of-service] --replicas [number-of-replicas] -p 8083:8080 [image-name]
```
* Docker swarm services list
```
docker service ls
```
* Change number of replicas in docker swarm
```
docker service scale [service-name]=[new-number-of-replicas]
```
* Remove service from docker swarm
```
docker service rm [service-name]
```