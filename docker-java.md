C:\Users\Admin\AppData\Local\Programs\Python\Python38-32\python.exe E:/programing/language/python/python-docs/readfile.py
======== name dir ========
## 1. Important  Navigating through this course
### 1. How to navigate through this course

https://github.com/pictolearn/docker-tutorial

## 2. Docker Fundamentals and Introduction
### 1. What is Docker

```shell
# Once you install docker, try the following command
# This should output the version of docker
$ docker version


$docker info
```

Scripts

```shell

# Build an image
docker build -t <image-name> <location-of-Dockerfile>

# run an image or run a container directly from a specific image
docker run -it -d -p<host-port>:<container-port> --name <container-name> <image-name>:tag

-i (interactive)
-t (TTY)
-d (Detached) : Run it in detached mode or else the life time of the container will be only as long as you run the terminal.
-P : Docker assigned default ports which will access the required port in the container (meaning the host machine can get assigned 32769 : pointing to default port of the image)
--name : represents a default name, if it is not specified the docker daemon will allocate a unique name
image-name : specifies the image to download from the repostory
tag : defaults to latest, a version for the given image can be specified.
        

# allows you to view the logs in the container
docker logs <container-id>

# Allow you to tail logs
docker logs -ft <container-id>

# List all containers running and stopped
docker ps -a

# List all containers running
docker ps

# List all images available
docker images

# stop a specified container
docker stop <container-id>

# stop all containers
docker stop $(docker ps -a -q)

# remove image (note: no containers for this image should be running)
docker rmi <image-id>

# remove all images
docker rmi $(docker images -a)

#Remove a specific container
docker rm <container-id>

#Remove all containers
docker rm $(docker ps -a -q)

# log in to the shell of the container. Typically entry-point refers to /bin/bash
docker exec -it <container-name> <entry-point>


docker login 
docker tag <currentimage>:<tag> <repository-name>/<image-name>:<tag>
docker commit <container-id> <repository-name>/<image-name>:<tag>
docker push <repository-name>/<image-name>:<tag>
docker inspect <container-name>
docker inspect <image-name>


#Container volume is the logs directory for example or war directory
docker run -itd -P -v <host-volume-absolute-path>:<container-volume-path>  <container-name>


#docker-machine commands
docker-machine version

#Version of docker-machine
docker-machine ls

#Create a docker-machine
docker-machine create --driver virtualbox --virtualbox-disk-size "20000" <machine-name> 
docker-machine create --driver hyperv  <machine-name>
docker-machine create -d hyperv --hyperv-virtual-switch "<NameOfVirtualSwitch>" <nameOfNode> 

#docker-machine ip default provides the ip of the name of machine "default"
docker-machine ip default

# Telling docker to talk to the new machine
docker-machine env default

#Stop docker-machine
docker-machine stop default

#Start docker-machine
docker-machine start default

# Removing a docker machine
docker-machine rm <machine-name>

#remove all docker machines
docker-machine rm -f $(docker-machine ls -q);

# Runs the container
docker-compose up

# Runs in detached mode
docker-compose up -d

# Builds the image
docker-compose build

#Stops the container
docker-compose stop <service-name>

#Starts the container
docker-compose start <service-name>

# Equivalent to docker exec
docker-compose run <service-name> /bin/bash 

# Build a specific image.
docker-compose up --build

# View logs
docker-compose logs <service-name>

# Tail logs
docker-compose  logs -ft <service-name>

# Update specific container
docker-compose up -d --no-deps <service-name>

# Stop all containers
docker-compose down

#Remove errored out images
docker rmi $(docker images | grep "^<none>" | awk "{print $3}")


#Shut down containers, remove all images and rebuild images with docker-compose
docker-compose down
docker-compose rm -f
docker-compose pull
docker-compose up --build -d

# How to find the disk space used by docker
docker system df
du -sch /var/lib/docker/containers
du -c /var/lib/docker/ | head -15 | sort -rn

# cleaning up old containers and images from docker and release resources
docker rm $(docker ps -qa --no-trunc --filter "status=exited")
docker rmi $(docker images --filter "dangling=true" -q --no-trunc)
docker rmi $(docker images | grep "none" | awk '/ / { print $3 }')
docker volume rm $(docker volume ls -qf dangling=true)
docker volume ls -qf dangling=true | xargs -r docker volume rm
docker network rm $(docker network ls | grep "bridge" | awk '/ / { print $1 }')
docker network prune
docker system prune
docker system prune -af
```



### 2. Docker Engine
### 3. Real World Use case - The problem
### 4. Real World Use case - Docker to the rescue
## 3. Docker Installation on the MAC and Windows
### 1. Docker installation on the MAC
### 1.4 Installation on the MAC
### 2. Docker installation on Windows 10 Professional

![image-20200620112104403](docker-java.assets/image-20200620112104403.png)  

Cài extension docker

gg: windows hypervisor enable

https://techcommunity.microsoft.com/t5/itops-talk-blog/step-by-step-enabling-hyper-v-for-use-on-windows-10/ba-p/267945

![image-20200620113113966](docker-java.assets/image-20200620113113966.png)  

1.**Open up the power shell**

2.**Execute the following command in the terminal**

**docker** 

`run –it hello-world`

### 3. Docker Summary Break - 1

**What is the Docker platform?**

Docker provides the ability to **package** and **run** an application in a **loosely isolated environment called a container****.** The isolation and security allow you to run **many containers simultaneously on a given** **host**.

![image-20200620113325918](docker-java.assets/image-20200620113325918.png)  



## 4. Important-Note  Before you start the use cases
### 1. Windows only Before you start the use case

![image-20200620113514100](docker-java.assets/image-20200620113514100.png)  

![image-20200620113620272](docker-java.assets/image-20200620113620272.png)  



### 2. MAC only Before you start the use case

![image-20200620122911349](docker-java.assets/image-20200620122911349.png)

## 5. Use Case 1   Host a website on Apache httpd Server
### 1. What are we going to do
### 2. What is a Docker Image

![image-20200620123503330](docker-java.assets/image-20200620123503330.png)  

![image-20200620123524993](docker-java.assets/image-20200620123524993.png)  

![image-20200620123540542](docker-java.assets/image-20200620123540542.png)  

![image-20200620123657224](docker-java.assets/image-20200620123657224.png)

### 3. Building, Listing and Inspecting Images

Chạy lệnh ở cùng thư mục chứa file 

```shell

#Step 1: Building an image
#Syntax: docker build -t <image-name> <location of dockerfile>
-------------------------------------------------------------------
docker build -t my-httpd .

#Step 2: List all the images
#Syntax: docker images
-------------------------------------------------------------------
docker images

#Step 3: Inspect the Image
------------------------------------------------------------------
docker inspect <image-id>

#Step 4: Running a container from the image
#Syntax: docker run -itd --name <container-name> -p <host-port>:<port in container> image-name:tag
# note in the above syntax:
# -d : represents (detached mode), note that if you dont run this in detached mode, the life of the container will be the life of the terminal in which you are executing it.
# -p : represents the host-port to container-port mapping, if you substitute it with -P you will get a random port allocated by docker
# --name : represents the name of the container 
-------------------------------------------------------------------
docker run -itd --name my-http-container-1 -p 5555:80 my-httpd:latest
docker run -itd --name my-http-container-2 -p 5556:80 my-httpd:latest
docker run -itd --name my-http-container-with-random-port -P my-httpd:latest

#note if you run this it will NOT run in detached mode.
docker run -it --name my-http-container-not-detached-mode -p 5557:80 my-httpd:latest

Step 5: View all the containers
-------------------------------------------------------------------
# Shows all the containers which are running
docker ps 

#Shows all the containers stopped and running
docker ps -a

Step 6: Inspect the container and image
-------------------------------------------------------------------
docker inspect <container-id>

Step 7: View Container logs
-------------------------------------------------------------------

# View the logs of the container
docker logs <container-id>

# Tail the logs of the container
docker logs -ft <container-id>

Step 8: Stop the container
-------------------------------------------------------------------
docker stop <container-id>

Step 9: Stop the container
-------------------------------------------------------------------
docker start <container-id>

Step 10: Logging into the container
-------------------------------------------------------------------
#Note: The container must be started before we can do this.
docker exec -it <container-id> /bin/bash

Step 11: Remove all the containers and images
-------------------------------------------------------------------
#Note: To remove an image the corresponding container built from that image will need to be removed.

#Remove a specific container
docker rm <container-id>

#Remove all containers
docker rm $(docker ps -a -q)

# remove image (note: no containers for this image should be running)
docker rmi <image-id>

# remove all images
docker rmi $(docker images -q)

```

Dockerfile

```dockerfile
# Updated as of Aug 16, 2017
# FROM specified which image i want to download
# Needs to be provided before any other section of code.
FROM httpd:latest

#Author of the Docker File
# MAINTAINER Pictolearn Note: MAINTAINER has been deprecated for LABEL, 
# LABEL is a key value pair
LABEL "Maintainer"="Pictolearn"

# Copy the following directory
COPY pictolearn-sample/ /usr/local/apache2/htdocs/pictolearn

# Copy httpd.conf with changes to the root directory
COPY httpd.conf /usr/local/apache2/conf
```

![image-20200620131616573](docker-java.assets/image-20200620131616573.png)  

![image-20200620131644306](docker-java.assets/image-20200620131644306.png)  

![image-20200620131711500](docker-java.assets/image-20200620131711500.png)  

![image-20200620131830780](docker-java.assets/image-20200620131830780.png)  

-t: Just know that for now the thing is the output is the terminal.

![image-20200620132408772](docker-java.assets/image-20200620132408772.png)  

![image-20200620132649814](docker-java.assets/image-20200620132649814.png)  



### 4. Running Containers, listing, starting and stopping containers

![image-20200620133319555](docker-java.assets/image-20200620133319555.png)  

![image-20200620133448082](docker-java.assets/image-20200620133448082.png)

Nhược điểm của cách chạy cuối k có detach mode is if you CTRL C, you will cannot access this page

Nếu tham số -P được viết hoa thì random port

![image-20200620134447881](docker-java.assets/image-20200620134447881.png)  

http://localhost:32768



### 5. Logging into the container

![image-20200620134905532](docker-java.assets/image-20200620134905532.png)  

![image-20200620135243391](docker-java.assets/image-20200620135243391.png)  

![image-20200620135419797](docker-java.assets/image-20200620135419797.png)  

The first process ID is logged in as root and then it starts I see the beauty in the foreground.

Now remember that every image which you download from Docker hub or even the one you create you are going

to have the first process ID as well as what does the default startup script our default container which

has to be launched from that image.

![image-20200620135925535](docker-java.assets/image-20200620135925535.png)  

these two lines which basically were modified when we created the image.

### 6. Removing Containers and Images

So you need to stop a container container.

![image-20200620140509105](docker-java.assets/image-20200620140509105.png)

### 7. Usecase-1 Quick Summary and Recap
## 6. Use Case 2   Host a website on NGINX HTTP Server
### 1. Introduction to Use Case 2
### 2. Build-Tag-Push & Pull images
## 7. Brain Overload - 1
### 1. What have you learnt so far
## 8. Use Case 3  Docker-Git integration and creating a custom UBUNTU image
### 1. Introduction to Use Case 3
### 2. Build a Custom UBUNTU Image with JDK, VI editor, MAVEN
### 3. Docker-GIT-Integration
## 9. Use Case 4 Deploy a Spring MVC war application on Apache Tomcat 8.x
### 1. Introduction and Deployment of war application on Tomcat 8.5
## 10. Use Case 5 and 6  Multiple containers w different JDK and Tomcat on UBUNTU
### 1. JDK7-Tomcat-7 and JDK8-Tomcat-8 on UBUNTU
### 2. Summary
## 11. Use Case 7 Mounting Volumes
### 1. Mounting Log Volumes
## 12. Use Case 8 Microservices using Docker Machine and Docker Compose
### 1. Introduction to Docker-Machine
### 2. MAC Only Pre-requisite for installing Docker Machine
### 3. Windows only Pre-requisite for Installing Docker Machine
### 4. Windows only Setting up 2 Docker Machines
### 5. Docker-compose Basics and Use case set up
### 6. Working with Docker-compose
### 7. Summary
## 13. Use Case 9 Microservices with Docker, Spring Boot and Hibernate with MYSQL
### 1. Introduction and Initial Set up
### 2. Building Spring Boot Microservice with Docker
## 14. Use Case 10 Service Discovery and Load Balancing
### 1. Use Case 10 Scaling up Microservices, Service Discovery and Load Balancing
### 2. Quick Code Overview
### 3. Demo
## 15. Summary, Docker Cheatsheets, Feedback
### 1. All Powerpoints and Docker Cheatsheet
### 2. Summary and Feedback
======== list file ========