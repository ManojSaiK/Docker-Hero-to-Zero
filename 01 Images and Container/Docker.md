**Docker**

**How docker works**

-DockerHub -(docker pull)-> Docker image -> Docker Container

or we can also specify own dockerfile

-DockerFile -(docker build)-> Docker image -> Docker Container

**Setup ec2 instance**

install docker 

&nbsp;yum install docker -y

**start the docker** 

&nbsp;service docker start

&nbsp;service docker status

**Basic docker commands**

&nbsp;docker images(to check images created)

&nbsp;docker ps(to check running docker containers)

&nbsp;docker ps -a(to check all containers)

&nbsp;docker help(to view all docker commands)

**Get Docker image from Docker Hub**

&nbsp;hub.docker.com

-search for image and take the official one

&nbsp;docker pull tomcat

**Creating container out of image**

&nbsp;docker run --name tomcat-container -p 8081:8080 tomcat - runs container on forground

&nbsp;0044d29d7a35d06d286238c94d96a2ef310a8f3bb0fa2ee76c0dff2e25d2b261 (container id)

&nbsp;docker run -d --name tomcat-container -p 8081:8080 tomcat - runs container on background/detached mode

&nbsp;docker stop containerID/container name - to stop the container

&nbsp;docker rm containerID/container name - to delete the container

&nbsp;docker prune - deletes are unused containers

&nbsp;docker attach containerID - to run on foreground

&nbsp;docker start -f containerID - starts container on foreground

&nbsp;docker logs containerID - to get logs of the container, useful for trouble shoot container issues

&nbsp;docker run -it conatinerID - to interact with container

&nbsp;docker start -a containerID - starting container in attached mode

&nbsp;docker start -a -i containerID - starting container in attached mode and listens to response

**Deleting/removing Images \& Conatiner**

docker stop containerName - stops container

docker rm containerName - removes/deletes container

docker rmi imageID - removes/delete image (for removing image, no running or stopped container)

docker run -d --name tomcat-container -p 8081:8080 --rm tomcat - run container and removes it when it is stopped.

**Inspect image**

docker image inspect imageID - can view more details about image

Copying contents from \& Into Container

docker cp sourceFile/path conatinerName:/fileInsideConatiner - copies contents from outside to container

docker cp conatinerName:/fileInsideConatiner sourceFile/path - to get info from container

**Tagging Images**

docker build -t name:tag . - get name and tag for own images

**Login to Docker container**

&nbsp;docker exec -it tomcat-container /bin/bash

&nbsp;cp -R \* ../webapps

&nbsp;docker exit(to exit container)

**To stop container** 

&nbsp;docker stop tomcat-container

**Creating Docker file**

&nbsp;FROM - to pull base image

&nbsp;RUN - to execute cmnds

&nbsp;CMD - to provide defaults for an executing container

&nbsp;ENTRYPOINT - to configure a container that will run as an executable

&nbsp;WORKDIR - to sets the working dir

&nbsp;COPY - to copy a dir from ur local machine to the docker container

&nbsp;ADD - to copy file and folders from ur local machine to docker containers

&nbsp;EXPOSE - informs docker that the container listines on the specified network ports

&nbsp;ENV - to set environment variables

**Setting up tomcat server on rockylinux**

~ vi Dockerfile

FROM rockylinux:9

RUN yum install java -y

RUN mkdir /opt/tomcat

WORKDIR /opt/tomcat

ADD https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.105/bin/apache-tomcat-9.0.105.tar.gz .

RUN tar -xvzf apache-tomcat-9.0.105.tar.gz

RUN mv apache-tomcat-9.0.105/\* /opt/tomcat

EXPOSE 8080

CMD \["/opt/tomcat/bin/catalina.sh","run"]

Building docker image from docker file

&nbsp;docker build -t mytomcat .

--------------------------------------------------

dockeradmin

Mannu@123







