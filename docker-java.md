C:\Users\Admin\AppData\Local\Programs\Python\Python38-32\python.exe E:/programing/language/python/python-docs/readfile.py
======== name dir ========

[TOC]

---

- [Docker](#docker)
	- [DOCs:](#docs)
- [1. Important  Navigating through this course](#1-important-navigating-through-this-course)
	- [1. How to navigate through this course](#1-how-to-navigate-through-this-course)
- [2. Docker Fundamentals and Introduction](#2-docker-fundamentals-and-introduction)
	- [1. What is Docker](#1-what-is-docker)
	- [2. Docker Engine](#2-docker-engine)
	- [3. Real World Use case - The problem](#3-real-world-use-case---the-problem)
	- [4. Real World Use case - Docker to the rescue](#4-real-world-use-case---docker-to-the-rescue)
- [3. Docker Installation on the MAC and Windows](#3-docker-installation-on-the-mac-and-windows)
	- [1. Docker installation on the MAC](#1-docker-installation-on-the-mac)
	- [1.4 Installation on the MAC](#14-installation-on-the-mac)
	- [2. Docker installation on Windows 10 Professional](#2-docker-installation-on-windows-10-professional)
	- [3. Docker Summary Break - 1](#3-docker-summary-break---1)
- [4. Important-Note  Before you start the use cases](#4-important-note-before-you-start-the-use-cases)
	- [1. Windows only Before you start the use case](#1-windows-only-before-you-start-the-use-case)
	- [2. MAC only Before you start the use case](#2-mac-only-before-you-start-the-use-case)
- [5. Use Case 1   Host a website on Apache httpd Server](#5-use-case-1-host-a-website-on-apache-httpd-server)
	- [1. What are we going to do](#1-what-are-we-going-to-do)
	- [2. What is a Docker Image](#2-what-is-a-docker-image)
	- [3. Building, Listing and Inspecting Images](#3-building-listing-and-inspecting-images)
	- [4. Running Containers, listing, starting and stopping containers](#4-running-containers-listing-starting-and-stopping-containers)
	- [5. Logging into the container](#5-logging-into-the-container)
	- [6. Removing Containers and Images](#6-removing-containers-and-images)
	- [7. Usecase-1 Quick Summary and Recap](#7-usecase-1-quick-summary-and-recap)
- [6. Use Case 2   Host a website on NGINX HTTP Server](#6-use-case-2-host-a-website-on-nginx-http-server)
	- [1. Introduction to Use Case 2](#1-introduction-to-use-case-2)
	- [2. Build-Tag-Push & Pull images](#2-build-tag-push--pull-images)
- [7. Brain Overload - 1](#7-brain-overload---1)
	- [1. What have you learnt so far](#1-what-have-you-learnt-so-far)
- [8. Use Case 3  Docker-Git integration and creating a custom UBUNTU image](#8-use-case-3-docker-git-integration-and-creating-a-custom-ubuntu-image)
	- [1. Introduction to Use Case 3](#1-introduction-to-use-case-3)
	- [2. Build a Custom UBUNTU Image with JDK, VI editor, MAVEN](#2-build-a-custom-ubuntu-image-with-jdk-vi-editor-maven)
	- [3. Docker-GIT-Integration](#3-docker-git-integration)
- [9. Use Case 4 Deploy a Spring MVC war application on Apache Tomcat 8.x](#9-use-case-4-deploy-a-spring-mvc-war-application-on-apache-tomcat-8x)
	- [1. Introduction and Deployment of war application on Tomcat 8.5](#1-introduction-and-deployment-of-war-application-on-tomcat-85)
- [10. Use Case 5 and 6  Multiple containers w different JDK and Tomcat on UBUNTU](#10-use-case-5-and-6-multiple-containers-w-different-jdk-and-tomcat-on-ubuntu)
	- [1. JDK7-Tomcat-7 and JDK8-Tomcat-8 on UBUNTU](#1-jdk7-tomcat-7-and-jdk8-tomcat-8-on-ubuntu)
	- [2. Summary](#2-summary)
- [11. Use Case 7 Mounting Volumes](#11-use-case-7-mounting-volumes)
	- [1. Mounting Log Volumes](#1-mounting-log-volumes)
- [12. Use Case 8 Microservices using Docker Machine and Docker Compose](#12-use-case-8-microservices-using-docker-machine-and-docker-compose)
	- [1. Introduction to Docker-Machine](#1-introduction-to-docker-machine)
	- [2. MAC Only Pre-requisite for installing Docker Machine](#2-mac-only-pre-requisite-for-installing-docker-machine)
	- [3. Windows only Pre-requisite for Installing Docker Machine](#3-windows-only-pre-requisite-for-installing-docker-machine)
	- [Install Docker Machine](#install-docker-machine)
	- [4. Windows only Setting up 2 Docker Machines](#4-windows-only-setting-up-2-docker-machines)
	- [5. Docker-compose Basics and Use case set up](#5-docker-compose-basics-and-use-case-set-up)
	- [6. Working with Docker-compose](#6-working-with-docker-compose)
	- [7. Summary](#7-summary)
- [13. Use Case 9 Microservices with Docker, Spring Boot and Hibernate with MYSQL](#13-use-case-9-microservices-with-docker-spring-boot-and-hibernate-with-mysql)
	- [1. Introduction and Initial Set up](#1-introduction-and-initial-set-up)
	- [2. Building Spring Boot Microservice with Docker](#2-building-spring-boot-microservice-with-docker)
- [14. Use Case 10 Service Discovery and Load Balancing](#14-use-case-10-service-discovery-and-load-balancing)
	- [1. Use Case 10 Scaling up Microservices, Service Discovery and Load Balancing](#1-use-case-10-scaling-up-microservices-service-discovery-and-load-balancing)
	- [2. Quick Code Overview](#2-quick-code-overview)
	- [3. Demo](#3-demo)
- [15. Summary, Docker Cheatsheets, Feedback](#15-summary-docker-cheatsheets-feedback)
	- [1. All Powerpoints and Docker Cheatsheet](#1-all-powerpoints-and-docker-cheatsheet)
	- [2. Summary and Feedback](#2-summary-and-feedback)

---


## Docker

https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes

 Docker fix err in unbutu

https://www.linuxuprising.com/2018/07/how-to-fix-could-not-get-lock.html

`sudo rm /var/lib/apt/lists/lock`

https://xuanthulab.net/gioi-thieu-ve-docker-lam-quen-voi-docker-tao-container.html



```shell
# Account
DockerID: phuong1020
20100
pass: duyphuong1020

#kiểm tra phiên bản
docker --version

#liệt kê các image
docker images -a
docker images

#xóa một image (phải không container nào đang dùng)
docker images rm imageid

#tải về một image (imagename) từ hub.docker.com
docker pull imagename

#liệt kê các container
docker ps
docker container ls -a

#xóa container
docker container rm containerid
 
#Chạy container đang dừng
docker container start -i containerid

# Now to stop the above container use the below command.
docker stop eeae1186ea78

# So to delete the container, first stop it and then delete it.

docker stop cae760f70ec4
docker rm cae760f70ec4


# To forcefully delete a container without stopping it, use the -f option.

docker rm -f 18a1924e8499

# To delete all the containers at once, first stop them all and then delete them.

docker stop `docker ps -q`
docker rm `docker ps -aq`

# remove all

docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
docker rmi $(docker images -a -q)

# Build 
docker build -t <your username>/node-web-app .
docker run -p 80:8080 -d <your username>/node-web-app


```

### DOCs:

https://viblo.asia/p/tim-hieu-co-ban-ve-docker-qua-vi-du-YWOZr6REZQ0

https://viblo.asia/s/series-hoc-docker-cicd-tu-co-ban-den-ap-dung-vao-thuc-te-jeZ103QgKWz

https://docs.microsoft.com/en-us/virtualization/windowscontainers/quick-start/building-sample-app

https://docs.docker.com/engine/reference/commandline/build/

https://docs.docker.com/docker-for-windows/#docker-settings-dialog

https://www.thegeekdiary.com/how-to-list-start-stop-delete-docker-containers/

**Java**

https://runnable.com/docker/java/dockerize-your-java-application

https://mkyong.com/docker/docker-and-java-application-examples/

https://stackify.com/guide-docker-java/

https://www.javatpoint.com/docker-java-example

https://howtodoinjava.com/library/docker-hello-world-example/

https://spring.io/guides/gs/spring-boot-docker/

https://spring.io/guides/topicals/spring-boot-docker

**Nodejs**

https://www.digitalocean.com/community/tutorials/how-to-build-a-node-js-application-with-docker-quickstart

https://www.digitalocean.com/community/tutorials/how-to-build-a-node-js-application-with-docker

https://nodejs.org/de/docs/guides/nodejs-docker-webapp/

C

https://kipalog.com/posts/C-C---Preprocessor--Phan-1----Constant-va-Conditional-Inclusion



React

docker react turtorials

https://medium.com/@mannycodes/deploying-reactjs-with-docker-ac16728c0896

https://dev.to/peterj/run-a-react-app-in-a-docker-container-kjn

---



## 1. Important  Navigating through this course

https://www.udemy.com/course/introduction-to-docker-for-java-developers/

### 1. How to navigate through this course

https://github.com/pictolearn/docker-tutorial

## 2. Docker Fundamentals and Introduction
### 1. What is Docker

1.1 Docker Quick Introduction.pptx

![image-20201018203012113](docker-java.assets/image-20201018203012113.png)

![image-20201018203026491](docker-java.assets/image-20201018203026491.png)

Google on “[How ](http://stackoverflow.com/questions/16047306/how-is-docker-different-from-a-normal-virtual-machine)[is Docker different from a normal virtual machine](http://stackoverflow.com/questions/16047306/how-is-docker-different-from-a-normal-virtual-machine)[?](http://stackoverflow.com/questions/16047306/how-is-docker-different-from-a-normal-virtual-machine)” , click on the first link on stackoverflow.com to get a more detailed understanding of docker vs virtual machines.



**http://stackoverflow.com/questions/16047306/how-is-docker-different-from-a-normal-virtual-machine**





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

2.1 Docker Engine.pptx

![image-20201018203333848](docker-java.assets/image-20201018203333848.png)

![image-20201018203402457](docker-java.assets/image-20201018203402457.png)

### 3. Real World Use case - The problem

3.1 Real World Use Case - The Problem.pptx

![image-20201018203607582](docker-java.assets/image-20201018203607582.png)

![image-20201018203629316](docker-java.assets/image-20201018203629316.png)

![image-20201018203706103](docker-java.assets/image-20201018203706103.png)

![image-20201018203805956](docker-java.assets/image-20201018203805956.png)

![image-20201018203819069](docker-java.assets/image-20201018203819069.png)

![image-20201018203843505](docker-java.assets/image-20201018203843505.png)



### 4. Real World Use case - Docker to the rescue

![image-20201018203909811](docker-java.assets/image-20201018203909811.png)

![image-20201018203945013](docker-java.assets/image-20201018203945013.png)

![image-20201018204003257](docker-java.assets/image-20201018204003257.png)

**SUMMARY**

Simple and easily Configurable.

Easy to Develop on.

Faster Release Cycles.

Faster Deployment Times.

Reduced bloat as compared to other virtualization techniques.

Consistent development of software across all environments.

## 3. Docker Installation on the MAC and Windows
### 1. Docker installation on the MAC

- Download docker extension on vs code in MAC
- https://hub.docker.com/editions/community/docker-ce-desktop-mac/
- Run command: `docker run -it hello-world`

1.1 Installation of Code samples.pptx

![image-20201018204257983](docker-java.assets/image-20201018204257983.png)

1.2 Docker hello-world.pptx

![image-20201018204325957](docker-java.assets/image-20201018204325957.png)

![image-20201018204402940](docker-java.assets/image-20201018204402940.png)

![image-20201018205107428](docker-java.assets/image-20201018205107428.png)

### 1.4 Installation on the MAC
### 2. Docker installation on Windows 10 Professional

![image-20200620112104403](docker-java.assets/image-20200620112104403.png)  

- Cài extension docker

- gg: windows hypervisor enable

https://techcommunity.microsoft.com/t5/itops-talk-blog/step-by-step-enabling-hyper-v-for-use-on-windows-10/ba-p/267945

![image-20200620113113966](docker-java.assets/image-20200620113113966.png)  

1.**Open up the power shell**

2.**Execute the following command in the terminal**

```shell
docker version
docker run –it hello-world
```



### 3. Docker Summary Break - 1

![image-20201018205713331](docker-java.assets/image-20201018205713331.png)

![image-20200620113325918](docker-java.assets/image-20200620113325918.png)  



## 4. Important-Note  Before you start the use cases
### 1. Windows only Before you start the use case

> Make sure docker run in linux container

![image-20200620113514100](docker-java.assets/image-20200620113514100.png)  

![image-20200620113620272](docker-java.assets/image-20200620113620272.png)  



### 2. MAC only Before you start the use case

![image-20200620122911349](docker-java.assets/image-20200620122911349.png)

## 5. Use Case 1   Host a website on Apache httpd Server
### 1. What are we going to do

`HANDS ON DOCKER for JAVA Developers\PPTS-FULL\5-Windows10\3- Use case - 1`

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

```ini
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

```shell
#note if you run this it will NOT run in detached mode.
docker run -it --name my-http-container-not-detached-mode -p 5557:80 my-httpd:latest

==> click CTRL C => stop running
```



Nhược điểm của cách chạy cuối k có detach mode is if you CTRL C, you will cannot access this page

Nếu tham số -P được viết hoa thì random port

![image-20200620134447881](docker-java.assets/image-20200620134447881.png)  

http://localhost:32768



### 5. Logging into the container

![image-20200620134905532](docker-java.assets/image-20200620134905532.png)  

![image-20200620135243391](docker-java.assets/image-20200620135243391.png)

>  Có thể nhập vài characters đầu của container id 

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

![image-20201018215735481](docker-java.assets/image-20201018215735481.png)

![image-20201018215752451](docker-java.assets/image-20201018215752451.png)

![image-20201018215807890](docker-java.assets/image-20201018215807890.png)

![image-20201018215818688](docker-java.assets/image-20201018215818688.png)

## 6. Use Case 2   Host a website on NGINX HTTP Server
### 1. Introduction to Use Case 2

![image-20200620144719367](docker-java.assets/image-20200620144719367.png)  



### 2. Build-Tag-Push & Pull images

![image-20200620145042363](docker-java.assets/image-20200620145042363.png)  

Dockerfile

```dockerfile
# Updated as of Aug 16, 2017
# FROM specified which image i want to download
# Needs to be provided before any other section of code.
FROM nginx:1.14

#Author of the Docker File
# MAINTAINER Pictolearn Note: MAINTAINER has been deprecated for LABEL, 
# LABEL is a key value pair 
LABEL "Maintainer"="Pictolearn"

# Copy httpd.conf with changes to the root directory
COPY default.conf /etc/nginx/conf.d/

# Copy the following directory
COPY pictolearn-sample/ /usr/share/nginx/html/pictolearn 
```

```shell

#Step 1: Building an image
#Syntax: docker build -t <image-name> <location of dockerfile>
-------------------------------------------------------------------
docker build -t my-nginx .

#Step 2: List all the images
#Syntax: docker images
-------------------------------------------------------------------
docker images

#Step 3: Running a container from the image
#Syntax: docker run -itd --name <container-name> -p <host-port>:<port in container> image-name:tag
# note in the above syntax:
# -d : represents (detached mode), note that if you dont run this in detached mode, the life of the container will be the life of the terminal in which you are executing it.
# -p : represents the host-port to container-port mapping, if you substitute it with -P you will get a random port allocated by docker
# --name : represents the name of the container 
-------------------------------------------------------------------
docker run -itd --name my-nginx-container-1 -p 7777:80 my-nginx:latest
docker run -itd --name my-nginx-container-2 -p 7778:80 my-nginx:latest

Step 4: View all the containers
-------------------------------------------------------------------
# Shows all the containers which are running
docker ps 

#Shows all the containers stopped and running
docker ps -a

Step 5: Logging into the container
-------------------------------------------------------------------
#Note: The container must be started before we can do this.
docker exec -it <container-id> /bin/bash

Step 6: Logging into Dockerhub account on the terminal
-------------------------------------------------------------------
docker login 
docker tag <currentimage>:<tag> <repository-name>/<image-name>:<tag>
docker push <repository-name>/<image-name>:<tag>
docker commit <container-id> <repository-name>/<image-name>:<tag>

docker pull <repository-name>/<image-name>:<tag>




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

FROM nginx:1.14 => search version trên docker hub

![image-20200620150103895](docker-java.assets/image-20200620150103895.png)  

Go to termial

![image-20200620150246474](docker-java.assets/image-20200620150246474.png)  

![image-20200620150414183](docker-java.assets/image-20200620150414183.png)  

Vào page dockerhub log in

![image-20200620151447518](docker-java.assets/image-20200620151447518.png)  

![image-20200620153627698](docker-java.assets/image-20200620153627698.png)  

![image-20200620153703411](docker-java.assets/image-20200620153703411.png)  

![image-20200620154034473](docker-java.assets/image-20200620154034473.png)  

remove image in order

Afterwards, pull images

![image-20200620155108080](docker-java.assets/image-20200620155108080.png)

## 7. Brain Overload - 1
### 1. What have you learnt so far

**Dockerfile**

- Dockerfile is “Case sensitive”. So make sure the right case is used.

- It is used to build a Docker Image

![image-20200620160903386](docker-java.assets/image-20200620160903386.png)  

![image-20200620160924138](docker-java.assets/image-20200620160924138.png)  



## 8. Use Case 3  Docker-Git integration and creating a custom UBUNTU image
### 1. Introduction to Use Case 3

![image-20200620161210807](docker-java.assets/image-20200620161210807.png)  

![image-20200620161228850](docker-java.assets/image-20200620161228850.png)  

**Step 1:** **Open Github desktop and create a dummy Project, check it into GIT HUB**

**Step 2:** **Install Docker plugin for Eclipse**

**Step 3:** **Create a** **docker**-**git**-**hello-world** **project with a package structure of** **org.pictolearn.docker** **Build an image, run a container verify the use case before understanding what GIT is going to achieve for us.**

**Docker Hub** **does continuous integration for any changes detected on** **Github**. It automatically creates a deployable image for you.

**Summary:**

1.**Linking Docker hub with GIT**

2.**Using Docker hub as a continuous integration server to build images.**



### 2. Build a Custom UBUNTU Image with JDK, VI editor, MAVEN

Dockerfile

```dockerfile
# Updated as of Aug 16, 2017
# Install FROM UBUNTU IMAGE
FROM ubuntu:16.04

#Author of the Docker File
# MAINTAINER Pictolearn Note: MAINTAINER has been deprecated for LABEL, 
# LABEL is a key value pair 
LABEL "Maintainer"="Pictolearn"

# RUN COMMAND BASICALLY runs the command in the terminal and creates an image.
# Install all the updates for UBUNTU
RUN apt-get update && apt-get install -y python-software-properties software-properties-common

# Install all the updates for UBUNTU
RUN apt-get install -y iputils-ping

# Adds the repository where JDK 8 can be obtained for UBUNTU
RUN add-apt-repository ppa:webupd8team/java

# INSTALL THE VI EDITOR AND MYSQL-CLIENT
RUN apt-get install -y vim
RUN apt-get install -y mysql-client

# NOTE and WARNING: ORACLE JDK is no longer licensed. Please install default jdk or OPEN JDK. 
# The initial set up was to get this working with JDK 7 but when the licensing terms for oracle changing we will install the default JDK
# INSTALL ORACLE JDK 8 BY ACCEPTING YES
# RUN echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 boolean true" | debconf-set-selections
#INSTALL ALL the updates again and install MAVEN and JDK 8
# RUN apt-get update && apt-get install -y oracle-java8-installer maven
RUN apt-get update && apt-get install -y default-jdk maven


# ADD a directory called docker-git-hello-world inside the UBUNTU IMAGE where you will be moving all of these files under this 
# DIRECTORY to
ADD . /usr/local/docker-git-hello-world

# AFTER YOU HAVE MOVED ALL THE FILES GO AHEAD CD into the directory and run mvn assembly.
# Maven assembly will package the project into a JAR FILE which can be executed
RUN cd /usr/local/docker-git-hello-world && mvn assembly:assembly

#THE CMD COMMAND tells docker the command to run when the container is started up from the image. In this case we are
# executing the java program as is to print Hello World.
CMD ["java", "-cp", "/usr/local/docker-git-hello-world/target/docker-git-hello-world-0.0.1-SNAPSHOT-jar-with-dependencies.jar", "org.pictolearn.docker.HelloWorldPing"]
```

script

```shell
#Build the image.
docker build -t my-java-docker .


#Run the image
docker run -itd --name my-java-docker-container my-java-docker:latest

# Review the logs to see how the container is running. You can get it by executing $docker ps -a
docker logs -ft <container-id>
```

Xài docker-desktop sau khi create new repo thì publish

![image-20200620162428877](docker-java.assets/image-20200620162428877.png)  

setting jdk

![image-20200620162519911](docker-java.assets/image-20200620162519911.png)  

![image-20200620162610079](docker-java.assets/image-20200620162610079.png)  

CHọn jdk cho project

![image-20200620162656260](docker-java.assets/image-20200620162656260.png)  

![image-20200620162751904](docker-java.assets/image-20200620162751904.png)  

Update pom.xml và xóa file nằm trong test folder

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>docker-git-hello-world</groupId>
	<artifactId>docker-git-hello-world</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>docker-git-hello-world</name>
	<url>http://maven.apache.org</url>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
	</properties>

	<build>
		<plugins>
			<plugin>
				<artifactId>maven-assembly-plugin</artifactId>
				<version>2.6</version>
				<configuration>
					<descriptorRefs>
						<descriptorRef>jar-with-dependencies</descriptorRef>
					</descriptorRefs>
				</configuration>
			</plugin>
		</plugins>
	</build>
</project>

```

And we're going to create an image from ubuntu. So what we are doing here is we are installing all the software required for us to run Java.

Now what this is going to do is it copies all the files into that directory it's gonna run Mavin assembly

target and it's going to generate a jar file.

The command apparently tells doc the dock engine that this is the first command to run once a container

is started from the image. => dòng cuối

```shell
#Build the image.
docker build -t my-java-docker .


#Run the image
docker run -itd --name my-java-docker-container my-java-docker:latest

# Review the logs to see how the container is running. You can get it by executing $docker ps -a
docker logs -ft <container-id>
```

![image-20200620163713295](docker-java.assets/image-20200620163713295.png)  

:!q => exit



### 3. Docker-GIT-Integration

commit and sync

Vào dockerhub and vào setting 

Chọn github và đăng nhập

![image-20200620164551518](docker-java.assets/image-20200620164551518.png)  

 Chọn dropdown value thứ 2

![image-20200620164643110](docker-java.assets/image-20200620164643110.png)  

Sau đó chọn icon gỉhub

![image-20200620164804995](docker-java.assets/image-20200620164804995.png)  

Chọn hello-world-java

copy ![image-20200620164903115](docker-java.assets/image-20200620164903115.png)  

![image-20200620164928383](docker-java.assets/image-20200620164928383.png)  

Paste phần đã copy vào location

Vào build settings choose trigger

![image-20200620165040817](docker-java.assets/image-20200620165040817.png)  

Ấn vào building 

![image-20200620165149834](docker-java.assets/image-20200620165149834.png)  

DOcker file is displayed

![image-20200620165336299](docker-java.assets/image-20200620165336299.png)  

refresh and wait after a few minutes

![image-20200620165515345](docker-java.assets/image-20200620165515345.png)  

![image-20200620165542684](docker-java.assets/image-20200620165542684.png)  

![image-20200620165620116](docker-java.assets/image-20200620165620116.png)  

![image-20200620165701379](docker-java.assets/image-20200620165701379.png)  

![image-20200620165952149](docker-java.assets/image-20200620165952149.png)  

Then we commit it and sync

![image-20200620170122374](docker-java.assets/image-20200620170122374.png)  





## 9. Use Case 4 Deploy a Spring MVC war application on Apache Tomcat 8.x
### 1. Introduction and Deployment of war application on Tomcat 8.5

![image-20200620170258704](docker-java.assets/image-20200620170258704.png)  



## 10. Use Case 5 and 6  Multiple containers w different JDK and Tomcat on UBUNTU
### 1. JDK7-Tomcat-7 and JDK8-Tomcat-8 on UBUNTU

![image-20200620170503678](docker-java.assets/image-20200620170503678.png)  

script-7

```shell

#Step 1: Building an image
#Syntax: docker build -t <image-name> <location of dockerfile>
-------------------------------------------------------------------
docker build -t tomcat7-jdk7-image .

#Step 2: List all the images
#Syntax: docker images
-------------------------------------------------------------------
docker images

Step 3: Create a repository on github for tomcat-7-jdk7
-------------------------------------------------------------------

Step 4: Verify image creation and push it into Docker Hub 
# In my case i did 
# docker login
# docker tag tomcat7-jdk7-image:latest pictolearn/tomcat7-jdk7:latest
# docker push pictolearn/tomcat7-jdk7:latest

-------------------------------------------------------------------
docker login 
docker tag <currentimage>:<tag> <repository-name>/<image-name>:<tag>
docker push <repository-name>/<image-name>:<tag>
```

![image-20200620170903842](docker-java.assets/image-20200620170903842.png)  

*http://apache.rediris.es/tomcat/tomcat-7*

Vào link trên và lấy version cho chính xác

![image-20200620171056363](docker-java.assets/image-20200620171056363.png)  

Dockerfile7

```dockerfile
# Updated as of Aug 16, 2017
# ----------------------------------------------------------------------------------
# June 1, 2017: Oracle has archived JDK 7 and uses login to download JDK 7 hence
# UBUNTU is unable to download JDK 7, we will hence demonstrate this with OPEN JDK 7
#-----------------------------------------------------------------------------------
# This file is used to create a docker image.
# UBUNTU/CENTOS - > TOMCAT 7.x -> JDK 1.7 with all the updates, curl, vim
FROM ubuntu:16.04

#Author of the Docker File
# MAINTAINER Pictolearn Note: MAINTAINER has been deprecated for LABEL, 
# LABEL is a key value pair 
LABEL "Maintainer"="Pictolearn"

#Download the latest version of 7.x
#Verify the version exists here or else change it: http://apache.rediris.es/tomcat/tomcat-7
ENV TOMCAT_VERSION 7.0.94

# Run an update to get all the security patches
RUN apt-get -y update && apt-get -y upgrade

#Install curl/vim incase you want to debug. VIM - vi editor, curl is a utility which acts as http client which can be run from the unix prompt.
RUN apt-get -y install software-properties-common

# June 1, 2017 : Commented out Oracle JDK installation procedure
# RUN add-apt-repository ppa:webupd8team/java
#The below instruction is very important, failing to add this will not allow you to install JDK
# after the repository has been added.
# RUN apt-get -y update

# June 1, 2017 : Moved all installation packages to a single line
#Install CURL and VIM editors
RUN apt-get -y install curl wget vim

# June 1, 2017 : Commented out Oracle JDK installation procedure
# Accept the license
# RUN echo "oracle-java7-installer shared/accepted-oracle-license-v1-1 boolean true" | debconf-set-selections
# RUN apt-get -y install oracle-java7-installer
# Define commonly used JAVA_HOME variable
# ENV JAVA_HOME /usr/lib/jvm/java-7-oracle

# June 1, 2017: Added OPEN JDK Installation 
RUN add-apt-repository ppa:openjdk-r/ppa  
RUN apt-get update -y
RUN apt-get install -y openjdk-7-jdk 
ENV JAVA_HOME /usr/lib/jvm/java-1.7.0-openjdk-amd64

# Get Tomcat
# notice that i can add the same RUN command across multiple lines. This is done for Performance optimization
# and does not create too many layers in the image. Use this format if you would like for better maintenance.
RUN wget --quiet --no-cookies http://apache.rediris.es/tomcat/tomcat-7/v${TOMCAT_VERSION}/bin/apache-tomcat-${TOMCAT_VERSION}.tar.gz -O /tmp/tomcat.tgz && \
tar xzvf /tmp/tomcat.tgz -C /opt && \
mv /opt/apache-tomcat-${TOMCAT_VERSION} /opt/tomcat && \
rm /tmp/tomcat.tgz && \
rm -rf /opt/tomcat/webapps/examples && \
rm -rf /opt/tomcat/webapps/docs && \
rm -rf /opt/tomcat/webapps/ROOT
```

![image-20200620171247648](docker-java.assets/image-20200620171247648.png)  

![image-20200620171342215](docker-java.assets/image-20200620171342215.png)  

![image-20200620171409924](docker-java.assets/image-20200620171409924.png)  

Sau khi login in terminal

![image-20200620175304389](docker-java.assets/image-20200620175304389.png)  

Create new repo

We copy this name

![image-20200620175446479](docker-java.assets/image-20200620175446479.png)  

![image-20200620175619172](docker-java.assets/image-20200620175619172.png)  

![image-20200620180014854](docker-java.assets/image-20200620180014854.png)  

Likewise, create docker image with java 8

![image-20200620180132934](docker-java.assets/image-20200620180132934.png)  

![image-20200620180153488](docker-java.assets/image-20200620180153488.png)  

comment trong Docker file jdk 8

```dockerfile
#&& \
#rm -rf /opt/tomcat/webapps/examples && \
#rm -rf /opt/tomcat/webapps/docs && \
#rm -rf /opt/tomcat/webapps/ROOT
```

![image-20200621074821082](docker-java.assets/image-20200621074821082.png)  

script

```shell

#Step 1: Building an image
#Syntax: docker build -t <image-name> <location of dockerfile>
-------------------------------------------------------------------
docker build -t tomcat8-jdk8-image .

#Step 2: List all the images
#Syntax: docker images
-------------------------------------------------------------------
docker images

Step 3: Create a repository on github for tomcat-8-jdk8
-------------------------------------------------------------------

Step 4: Verify image creation and push it into Docker Hub
# In my case i did 
# docker login
# docker tag tomcat8-jdk8-image:latest pictolearn/tomcat8-jdk8:latest
# docker push pictolearn/tomcat8-jdk8:latest

-------------------------------------------------------------------
docker login 
docker tag <currentimage>:<tag> <repository-name>/<image-name>:<tag>
docker push <repository-name>/<image-name>:<tag>
```

![image-20200621075027063](docker-java.assets/image-20200621075027063.png)  

![image-20200621075110367](docker-java.assets/image-20200621075110367.png)  

![image-20200621075155293](docker-java.assets/image-20200621075155293.png) 

Use case 6

Dockerfile

```dockerfile
# This file is used to create a docker image.
# The image name created in the previous use case.
#FROM pictolearn/tomcat7-jdk7
FROM pictolearn/tomcat8-jdk8


# Add deployment
COPY docker-spring-mvc.war /opt/tomcat/webapps/ROOT.war

#Set Catalina HOME and JAVA_OPTS
ENV CATALINA_HOME /opt/tomcat
ENV PATH $PATH:$CATALINA_HOME/bin
ENV JAVA_OPTS="-Xms1024m -Xmx1024m -Xss8192k -XX:PermSize=500m -XX:CMSInitiatingOccupancyFraction=50 -XX:+ExplicitGCInvokesConcurrent -XX:+CMSClassUnloadingEnabled -XX:+UseConcMarkSweepGC -XX:+UseParNewGC -XX:NewRatio=1 -XX:SurvivorRatio=1  -Dorg.apache.cxf.JDKBugHacks.imageIO=false"

#Expose this a port to the host machine.
EXPOSE 8080
EXPOSE 8009

# install supervisor for debugging in case image is not built correctly.
# supervisor lets you debug information.
#RUN apt-get -y install supervisor
#RUN service supervisor restart

#The WORKDIR instruction sets the working directory for any RUN, CMD, ENTRYPOINT, COPY and ADD instructions that follow it in the Dockerfile.
WORKDIR /opt/tomcat

# Launch Tomcat
CMD ["/opt/tomcat/bin/catalina.sh", "run"]

# Used for debugging in case something does not work and the container fails to start up because of the CMD instruction specified above.
#ENTRYPOINT ["/bin/sh", "-c", "while true; do sleep 1; done"]


# Added for debugging in case image does not get built
# Install supervisor by commenting out that piece and make sure
# all works fine.
#ADD supervisord.conf /etc/supervisor/
#CMD ["/usr/bin/supervisord", "-n"]
```

![image-20200621075435578](docker-java.assets/image-20200621075435578.png)  

![image-20200621075548371](docker-java.assets/image-20200621075548371.png)  

![image-20200621075701361](docker-java.assets/image-20200621075701361.png)  

![image-20200621075748602](docker-java.assets/image-20200621075748602.png)  

![image-20200621075804297](docker-java.assets/image-20200621075804297.png)  

```shell
Step 1: Remove the existing pictolearn/tomcat7-jdk7 and pictolearn/tomcat8-jdk8 images
-------------------------------------------------------------------
docker rmi pictolearn/tomcat7-jdk7
docker rmi pictolearn/tomcat8-jdk8

#Step 2: Building an image
#Syntax: docker build -t <image-name> <location of dockerfile>
-------------------------------------------------------------------
docker build -t spring-mvc-tomcat7-jdk7-image .
docker build -t spring-mvc-tomcat8-jdk8-image .


#Step 3: Run a container from the image
#Syntax: docker run -itd --name <container-name> -p <host-port>:<container-port> <image-name>
---------------------------------------------------------------------------------------------
docker run -itd --name tomcat7-jdk7-container-1 -p 5555:8080 spring-mvc-tomcat7-jdk7-image
docker run -itd --name tomcat8-jdk8-container-2 -p 5556:8080 spring-mvc-tomcat8-jdk8-image
```

![image-20200621075923603](docker-java.assets/image-20200621075923603.png)  

Sau khi chạy `docker build -t spring-mvc-tomcat7-jdk7-image .` thì sửa docker file

![image-20200621080150102](docker-java.assets/image-20200621080150102.png)  

Sau đó build như trên

![image-20200621080521402](docker-java.assets/image-20200621080521402.png)

![image-20200621080255181](docker-java.assets/image-20200621080255181.png)  

![image-20200621080329902](docker-java.assets/image-20200621080329902.png)  



### 2. Summary
## 11. Use Case 7 Mounting Volumes
### 1. Mounting Log Volumes

![image-20200621081809204](docker-java.assets/image-20200621081809204.png)  

Dockerfile

```dockerfile
# This file is used to create a docker image.
# The image name created in the previous use case.
FROM pictolearn/tomcat7-jdk7

#Set Catalina HOME and JAVA_OPTS
ENV CATALINA_HOME /opt/tomcat
ENV PATH $PATH:$CATALINA_HOME/bin
ENV JAVA_OPTS="-Xms1024m -Xmx1024m -Xss8192k -XX:PermSize=500m -XX:CMSInitiatingOccupancyFraction=50 -XX:+ExplicitGCInvokesConcurrent -XX:+CMSClassUnloadingEnabled -XX:+UseConcMarkSweepGC -XX:+UseParNewGC -XX:NewRatio=1 -XX:SurvivorRatio=1  -Dorg.apache.cxf.JDKBugHacks.imageIO=false"

EXPOSE 8080
EXPOSE 8009

# Need a war file from the host to be mounted you can do so here. This instruction tells docker that content in those directories does not go in images and 
# can be accessed from other containers using the --volumes-from command line parameter. You have to run the container using -v 
#/path/on/host:/path/in/container to access directories from the host.
VOLUME "/opt/tomcat/webapps"
VOLUME "/opt/tomcat/logs"

#The WORKDIR instruction sets the working directory for any RUN, CMD, ENTRYPOINT, COPY and ADD instructions that follow it in the Dockerfile.
WORKDIR /opt/tomcat

# Launch Tomcat
CMD ["/opt/tomcat/bin/catalina.sh", "run"]
```

script

```shell
#Step 1: Building an image
#Syntax: docker build -t <image-name> <location of dockerfile>
-------------------------------------------------------------------
docker build -t spring-mvc-tomcat7-jdk7-volume-sample .

#Step 2: List all the images
#Syntax: docker images
-------------------------------------------------------------------
docker images


#Step 3: Run a container from the image with a volume mount
#Container volume is the logs directory for example or war directory
Example:  docker run -itd  -p <host-port>:<container-port> -v <host-volume-absolute-path>:<container-volume-path>  --name=<container-name> <image-id>
---------------------------------------------------------------------------------------------
docker run -itd  -p 3333:8080  -v F:/pictolearn/Docker/logs:/opt/tomcat/logs -v F:/pictolearn/Docker/webapps:/opt/tomcat/webapps  --name="tomcat-container-log" spring-mvc-tomcat7-jdk7-volume-sample
```

![image-20200621082243069](docker-java.assets/image-20200621082243069.png)  

![image-20200621082508367](docker-java.assets/image-20200621082508367.png)  

Vào setting của icon docker

![image-20200621082916436](docker-java.assets/image-20200621082916436.png)  

choose F folder

![image-20200621083017744](docker-java.assets/image-20200621083017744.png)  

Chỉnh norton smart firewall thành 1h

![image-20200621083135381](docker-java.assets/image-20200621083135381.png)  

Tạo folder log và webapp

Afterwards, we copy file .war into webapp folder

![image-20200621083734602](docker-java.assets/image-20200621083734602.png)

![image-20200621083629864](docker-java.assets/image-20200621083629864.png)  

![image-20200621083647677](docker-java.assets/image-20200621083647677.png)

## 12. Use Case 8 Microservices using Docker Machine and Docker Compose
### 1. Introduction to Docker-Machine

![image-20200621085105449](docker-java.assets/image-20200621085105449.png)  

![image-20200621085129604](docker-java.assets/image-20200621085129604.png)  

So basically what you're going to be doing is you're going to be running virtual machines on your current

computer beat the PC or the Mac  



### 2. MAC Only Pre-requisite for installing Docker Machine

![image-20200621085429623](docker-java.assets/image-20200621085429623.png)  

download 

scripts

```shell
*****************************************************************
Docker - machine: Windows and MAC
*****************************************************************

#Create 2 Docker machines (Remember both are virtual PCs running with different IPs)
------------------------------------------------------------------------

Windows: docker-machine create -d hyperv --hyperv-virtual-switch "vs-1" hyperv-vm-1
MAC: docker-machine create --driver virtualbox --virtualbox-disk-size "20000" hyperv-vm-1

Windows: docker-machine create -d hyperv --hyperv-virtual-switch "vs-1" hyperv-vm-2
MAC: docker-machine create --driver virtualbox --virtualbox-disk-size "20000" hyperv-vm-2

#Verify if docker-machine is running on an IP
------------------------------------------------------------------------
docker-machine ip hyperv-vm-1
docker-machine ip hyperv-vm-2

#Run the following command and whatever output you get run it again
------------------------------------------------------------------------
docker-machine env hyperv-vm-1
docker-machine env hyperv-vm-2

#Run the output of the last line of the command which is there before.
------------------------------------------------------------------------
 & "C:\Program Files\Docker\Docker\Resources\bin\docker-machine.exe" env hyperv-vm-1 | Invoke-Expression
 & "C:\Program Files\Docker\Docker\Resources\bin\docker-machine.exe" env hyperv-vm-2 | Invoke-Expression

#Verify the docker-machine is active.
----------------------------------------
docker-machine ls

Turning OFF and ON docker-machine
-------------------------------------
docker-machine stop hyperv-vm-1
docker-machine stop hyperv-vm-2
docker-machine start hyperv-vm-1
docker-machine start hyperv-vm-2

Remove docker-machine (Turn off docker-machine on hyper-v manager for windows before executing this command, for MAC no extra steps are required)
docker-machine rm -f <name-of-machine>

*****************************************************************
Docker - compose commands to follow (Common for MAC and Windows)
Manual Reference: https://docs.docker.com/compose/reference/
*****************************************************************
Step-1 # Builds the image
-------------------------------------------------------------------
docker-compose build

#Build a specific image
docker-compose build <service-name>

#Builds and run the containers
docker-compose up --build -d

Step-2 # View the image (All started and stopped containers)
-------------------------------------------------------------------
docker-compose ps 


Step-3 # Run the image in detached/non-detached mode (use -d) 
-------------------------------------------------------------------
docker-compose up -d
docker-compose up
docker-compose up -d <service-name>


Step-4 # View logs and Tail logs
-------------------------------------------------------------------
# View logs
docker-compose logs <service-name>

# Tail logs
docker-compose  logs -ft <service-name>

Step-5 # Login to the container
-------------------------------------------------------------------
docker-compose run <service-name> /bin/bash 

Step-6 # Stops all containers related to the compose file
--------------------------------------------------
docker-compose stop

#Stop and start specific container
docker-compose stop <service-name>

#Stop and remove containers
docker-compose down
```

![image-20200621085758640](docker-java.assets/image-20200621085758640.png)  

![image-20200621085941165](docker-java.assets/image-20200621085941165.png)  

![image-20200621090059492](docker-java.assets/image-20200621090059492.png)  

![image-20200621090257358](docker-java.assets/image-20200621090257358.png)  

![image-20200621090355142](docker-java.assets/image-20200621090355142.png)  

Với địa chỉ 100 thì chưa access được  

![image-20200621090618015](docker-java.assets/image-20200621090618015.png)  

So nginx can run in both container

![image-20200621090757672](docker-java.assets/image-20200621090757672.png)  



### 3. Windows only Pre-requisite for Installing Docker Machine

https://docs.docker.com/machine/install-machine/

### Install Docker Machine

1. Install [Docker](https://docs.docker.com/engine/install/).

2. Download the Docker Machine binary and extract it to your PATH.

   If you are running **macOS**:

   ```
   $ base=https://github.com/docker/machine/releases/download/v0.16.0 &&
     curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/usr/local/bin/docker-machine &&
     chmod +x /usr/local/bin/docker-machine
   ```

   If you are running **Linux**:

   ```
   $ base=https://github.com/docker/machine/releases/download/v0.16.0 &&
     curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
     sudo mv /tmp/docker-machine /usr/local/bin/docker-machine &&
     chmod +x /usr/local/bin/docker-machine
   ```

   If you are running **Windows** with [Git BASH](https://git-for-windows.github.io/):

   ```
   $ base=https://github.com/docker/machine/releases/download/v0.16.0 &&
     mkdir -p "$HOME/bin" &&
     curl -L $base/docker-machine-Windows-x86_64.exe > "$HOME/bin/docker-machine.exe" &&
     chmod +x "$HOME/bin/docker-machine.exe"
   ```

   > The above command works on Windows only if you use a terminal emulator such as [Git BASH](https://git-for-windows.github.io/), which supports Linux commands like `chmod`.

   Otherwise, download one of the releases from the [docker/machine release page](https://github.com/docker/machine/releases/) directly.

3. Check the installation by displaying the Machine version:

   ```shell
   $ docker-machine version
   docker-machine version 0.16.0, build 9371605
   ```

Vào ô search nhập turn windows feature on off

https://techcommunity.microsoft.com/t5/itops-talk-blog/step-by-step-enabling-hyper-v-for-use-on-windows-10/ba-p/267945

![image-20200621095106418](docker-java.assets/image-20200621095106418.png)  

Check container và hyper-v => restart

![image-20200621100022497](docker-java.assets/image-20200621100022497.png)  

Create new virtual switch manager by click on it

![image-20200621100119921](docker-java.assets/image-20200621100119921.png)  

chọn external and click CREATE

![image-20200621100559386](docker-java.assets/image-20200621100559386.png)

Nhập như trên chọn lại External network là 6025

![image-20200621101049489](docker-java.assets/image-20200621101049489.png)  

chọn yes

### 4. Windows only Setting up 2 Docker Machines

![image-20200621101804758](docker-java.assets/image-20200621101804758.png)  

![image-20200621102014423](docker-java.assets/image-20200621102014423.png)  

![image-20200621102352697](docker-java.assets/image-20200621102352697.png)  

![image-20200621102553765](docker-java.assets/image-20200621102553765.png)  

run với port 32771 cũng chạy

![image-20200621102830276](docker-java.assets/image-20200621102830276.png)  

![image-20200621102928224](docker-java.assets/image-20200621102928224.png)

### 5. Docker-compose Basics and Use case set up

![image-20200621114801536](docker-java.assets/image-20200621114801536.png)  

![image-20200621114918380](docker-java.assets/image-20200621114918380.png)  

Now Docker composed this used to create micro services are run services inside of Docker machines.

Vào eclipse import project java mysql

pom.xml

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>docker-mysql-connector</groupId>
	<artifactId>docker-mysql-connector</artifactId>
	<version>1.0.0-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>docker-mysql-connector</name>
	<url>http://maven.apache.org</url>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
	</properties>

	<dependencies>
		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<version>6.0.6</version>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<artifactId>maven-assembly-plugin</artifactId>
				<version>2.6</version>
				<configuration>
					<descriptorRefs>
						<descriptorRef>jar-with-dependencies</descriptorRef>
					</descriptorRefs>
				</configuration>
			</plugin>
		</plugins>
	</build>
</project>

```

Dockerfile

```dockerfile
FROM pictolearn/ubuntu-jdk8

#Author of the Docker File
# MAINTAINER Pictolearn Note: MAINTAINER has been deprecated for LABEL, 
# LABEL is a key value pair 
LABEL "Maintainer"="Pictolearn"

ADD . /usr/local/docker-mysql-connector
RUN cd /usr/local/docker-mysql-connector && mvn assembly:assembly
CMD ["java", "-cp", "/usr/local/docker-mysql-connector/target/docker-mysql-connector-1.0.0-SNAPSHOT-jar-with-dependencies.jar", "org.pictolearn.docker.mysql.MySQLConnection"]
```

![image-20200621120037320](docker-java.assets/image-20200621120037320.png)  

So just to take you back to that picture you're going to go back to that picture which I gave which

is the use case picture which is going to give you a clear description as you can see we created two

documentaries with two different IP addresses these are dummy IP addresses.

One has a Microsoft is running which is called My sql and another is a Java container and standalone

javascript called web.

=> 2 dịa chỉ Ip máy ảo khác nhau

docker-compose

```dockerfile
version: '3.1' #version of Docker-compose
services: #Specifies the micro-service you want to run
  db: # create an image by the name mysql
    # NOTE: As of June, 2018 this has been updated to use the version of mysql 5.7.22  
    image: mysql:5.7.22 # specify the image to download from docker hub, 
    ports: ["3306:3306"] # expose ports to docker-machine , same as the EXPOSE command
    hostname: db  #specify the name of a host which can be used by a container running on the same docker machine
    environment: # specify the password and default database to connect to, note that the default root user will be picked up.
        - MYSQL_ROOT_PASSWORD=root
        - MYSQL_DATABASE=Users
    container_name: mysqldatabase
  web: # create an image by the name web
    build: docker-mysql-connector 
    image: docker-mysql-connector
    hostname: web
    tty: true   # same as the "-t" option used in docker build "-t" 
    depends_on: #Specifies that this container should start up after mysql is build and has started
      - db
    links:  # you will specify this name or the alias name db:<alias> in the java code to connect, note you will not use localhost
      - db:db
    environment: #Specifies the environment variables
      - AWS_ACCESS_KEY=123456
```



### 6. Working with Docker-compose

![image-20200621121400556](docker-java.assets/image-20200621121400556.png)  

![image-20200621121508189](docker-java.assets/image-20200621121508189.png)  

![image-20200621121523296](docker-java.assets/image-20200621121523296.png)  

![image-20200621121637021](docker-java.assets/image-20200621121637021.png)  

![image-20200621121702955](docker-java.assets/image-20200621121702955.png)  

![image-20200621121759139](docker-java.assets/image-20200621121759139.png)  

Nhập vào store in va...  để nhập pass test

![image-20200621122108119](docker-java.assets/image-20200621122108119.png)  

Build specific id

![image-20200621122204427](docker-java.assets/image-20200621122204427.png)  

Lý do có url vì

![image-20200621122235602](docker-java.assets/image-20200621122235602.png)  

![image-20200621122547856](docker-java.assets/image-20200621122547856.png)  

copy the last command 

![image-20200621122658172](docker-java.assets/image-20200621122658172.png)  

![image-20200621122942098](docker-java.assets/image-20200621122942098.png)

Sau khi sửa lại url trong java có chỉ có db: mới chạy đúng

=> This make easier to deploy selective microservices

![image-20200621123631306](docker-java.assets/image-20200621123631306.png)  

stop all

![image-20200621123846810](docker-java.assets/image-20200621123846810.png)

### 7. Summary
## 13. Use Case 9 Microservices with Docker, Spring Boot and Hibernate with MYSQL
### 1. Introduction and Initial Set up

![image-20200621132323492](docker-java.assets/image-20200621132323492.png)  

script

```shell
*****************************************************************
Docker - compose commands to follow (Common for MAC and Windows)
Manual Reference: https://docs.docker.com/compose/reference/
*****************************************************************
Step-1 # Builds the image
-------------------------------------------------------------------
docker-compose build

#Build a specific image
docker-compose build <service-name>

#Builds and run the containers
docker-compose up --build -d

Step-2 # Run the image in detached/non-detached mode (use -d) 
-------------------------------------------------------------------
docker-compose up -d
docker-compose up
docker-compose up -d <service-name>

Step-3 # View the image (All started and stopped containers)
-------------------------------------------------------------------
docker-compose ps 

Step-4 # View logs and Tail logs
-------------------------------------------------------------------
# View logs
docker-compose logs <service-name>

# Tail logs
docker-compose  logs -ft <service-name>

Step-5 # Login to the container
-------------------------------------------------------------------
docker-compose run <service-name> /bin/bash 

Step-6 # Stops all containers related to the compose file
-------------------------------------------------------------------
Use a RESTFul Client to test the APIs

Step-7 # Stops all containers related to the compose file
--------------------------------------------------
docker-compose stop

#Stop and start specific container
docker-compose stop <service-name>

#Stop and remove containers
docker-compose down
```

docker-compose

```dockerfile
version: '3.1' #version of Docker-compose
services: #specifies 2 microservices "web" and "mysql"
  mysql:
    # NOTE: As of June, 2018 this has been updated to use the version of mysql 5.7.22  
    image: mysql:5.7.22 # Expose a mysql image
    ports: ["8888:3306"] # Expose port 8888
    hostname: mysql # mysql hostname
    environment: # root username and password
        - MYSQL_ROOT_PASSWORD=root
        - MYSQL_DATABASE=Users
  web: # Web microservice
    build: pictolearn-docker
    image: pictolearn-docker
    ports: ["5555:8080"] # expose port 5555 for the rest client to connect to
    hostname: web
    tty: true
#    volumes: # you can include volumes, will be a TODO exercise
#      - /Users/AGanesan/docker/docker-tutorial/resources/docker-compose-spring-boot/logs:/usr/local/pictolearn/logs
    depends_on:
      - mysql
    links:
      - mysql
    environment:
      - DB_PORT=tcp://mysql:3306  
```

![image-20200621132805623](docker-java.assets/image-20200621132805623.png)  

Dockerfile

```dockerfile
#Install from the same image built i usecase - 8
FROM pictolearn/ubuntu-jdk8

# add the directory to the path
ADD . /usr/local/pictolearn

# Run maven
RUN cd /usr/local/pictolearn && mvn clean package

#Spring boot initiation
CMD ["java","-jar","-DlogPath=/usr/local/pictolearn", "/usr/local/pictolearn/target/docker-compose-pictolearn-1.0.0-SNAPSHOT.jar"]
```

![image-20200621133057165](docker-java.assets/image-20200621133057165.png)  

![image-20200621133234462](docker-java.assets/image-20200621133234462.png)  

import to eclipse

![image-20200621133347903](docker-java.assets/image-20200621133347903.png)  

![image-20200621134448479](docker-java.assets/image-20200621134448479.png)  

![image-20200621135320324](docker-java.assets/image-20200621135320324.png)  

![image-20200621135448819](docker-java.assets/image-20200621135448819.png)  

![image-20200621135638775](docker-java.assets/image-20200621135638775.png)  

![image-20200621135805578](docker-java.assets/image-20200621135805578.png)  

Gọi post and get

body lấy từ file post.json, type is application/context

![image-20200621140015916](docker-java.assets/image-20200621140015916.png)

### 2. Building Spring Boot Microservice with Docker



## 14. Use Case 10 Service Discovery and Load Balancing
### 1. Use Case 10 Scaling up Microservices, Service Discovery and Load Balancing

![image-20200621140251007](docker-java.assets/image-20200621140251007.png)

scripts

```dockerfile
*****************************************************************
Step-1 # Run Powershell as administrator on WINDOWS or terminal on MAC
-------------------------------------------------------------------
docker-machine ps -a

*****************************************************************
Step-2 # Docker machine activation
-------------------------------------------------------------------
docker-machine env hyperv-vm-1
WINDOWS (Copy and execute the last line): # & "C:\Program Files\Docker\Docker\Resources\bin\docker-machine.exe" env hyperv-vm-1 | Invoke-Expression

Step-3 # Run the image in detached/non-detached mode (use -d) 
-------------------------------------------------------------------
docker-compose up -d
docker-compose up
docker-compose up -d <service-name>

docker-compose scale <service-name>=<total containers>
Ex: docker-compose scale web=2

Step-4 # View logs and Tail logs
-------------------------------------------------------------------
# View logs
docker-compose logs <service-name>

# Tail logs
docker-compose  logs -ft <service-name>

Step-5 # Login to the container
-------------------------------------------------------------------
docker-compose run <service-name> /bin/bash 

Step-6 # Stops all containers related to the compose file
--------------------------------------------------
docker-compose stop

#Stop and start specific container
docker-compose stop <service-name>

#Stop and remove containers
docker-compose down
```



### 2. Quick Code Overview

![image-20200621141227030](docker-java.assets/image-20200621141227030.png)  

![image-20200621141401064](docker-java.assets/image-20200621141401064.png)  

![image-20200621141631062](docker-java.assets/image-20200621141631062.png)  

pom.xml trong dispatcher

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>pictolearn-dispatcher</groupId>
	<artifactId>pictolearn-dispatcher</artifactId>
	<packaging>war</packaging>
	<version>0.0.1-SNAPSHOT</version>
	<name>docker-compose-dispatcher Maven Webapp</name>
	<url>http://maven.apache.org</url>
	<dependencies>
		<!-- https://mvnrepository.com/artifact/org.apache.commons/commons-lang3 -->
		<dependency>
			<groupId>org.apache.commons</groupId>
			<artifactId>commons-lang3</artifactId>
			<version>3.5</version>
		</dependency>

		<!-- https://mvnrepository.com/artifact/org.apache.commons/commons-collections4 -->
		<dependency>
			<groupId>org.apache.commons</groupId>
			<artifactId>commons-collections4</artifactId>
			<version>4.1</version>
		</dependency>


		<!-- https://mvnrepository.com/artifact/org.slf4j/slf4j-api -->
		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>slf4j-api</artifactId>
			<version>1.7.21</version>
		</dependency>

		<!-- https://mvnrepository.com/artifact/org.slf4j/jul-to-slf4j -->
		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>jul-to-slf4j</artifactId>
			<version>1.7.21</version>
		</dependency>

		<dependency>
			<groupId>org.slf4j</groupId>
			<artifactId>slf4j-log4j12</artifactId>
			<version>1.7.21</version>
		</dependency>

		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>javax.servlet-api</artifactId>
			<version>3.0.1</version>
			<scope>provided</scope>
		</dependency>
	</dependencies>
	<build>
		<finalName>pictolearn-dispatcher</finalName>
		<sourceDirectory>src</sourceDirectory>
		<plugins>
			<plugin>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.1</version>
				<configuration>
					<source>1.7</source>
					<target>1.7</target>
				</configuration>
			</plugin>
			<plugin>
				<artifactId>maven-war-plugin</artifactId>
				<version>2.4</version>
				<configuration>
					<warSourceDirectory>WebContent</warSourceDirectory>
					<failOnMissingWebXml>false</failOnMissingWebXml>
				</configuration>
			</plugin>
		</plugins>

	</build>
</project>

```

  



### 3. Demo

![image-20200621150057156](docker-java.assets/image-20200621150057156.png)  

Make sure your windows enable hyper-v and run powershell with administration

![image-20200621150319843](docker-java.assets/image-20200621150319843.png)  

![image-20200621150437551](docker-java.assets/image-20200621150437551.png)  

![image-20200621150542598](docker-java.assets/image-20200621150542598.png)  

![image-20200621150717085](docker-java.assets/image-20200621150717085.png) 

![image-20200621151018304](docker-java.assets/image-20200621151018304.png)  

![image-20200621151039038](docker-java.assets/image-20200621151039038.png)  

![image-20200621151149163](docker-java.assets/image-20200621151149163.png)  

Sau đó vào mysql chỉnh sửa connection

![image-20200621151310652](docker-java.assets/image-20200621151310652.png)  

Mysql run on port 8888

Test connection

![image-20200621151343946](docker-java.assets/image-20200621151343946.png)  

sau khi nhập pass ấn test

![image-20200621151458471](docker-java.assets/image-20200621151458471.png)  

![image-20200621151530248](docker-java.assets/image-20200621151530248.png)  

![image-20200621151649782](docker-java.assets/image-20200621151649782.png)  

So what I'm going to do here is and is going to say send and it's a success for introspect the headers

it's going to tell you which machine it actually hit.

So in this case it's 172 19 0.3.

So what I'm going to do right now as I'm going to go and check into my school database to make sure

there's an entry as I see it got inserted. 

![image-20200621152041874](docker-java.assets/image-20200621152041874.png)  



![image-20200621153402519](docker-java.assets/image-20200621153402519.png)

And the reason why we have a dispatcher is to be able to route to one of these.

So that said give it a few minutes until it starts up.

And typically for logging from all these containers we use tools like loudly that is a tool cloggy our

diner trays or at Dynamix higher performance monitoring tools.

![image-20200621153431621](docker-java.assets/image-20200621153431621.png)  

![image-20200621153544505](docker-java.assets/image-20200621153544505.png)  

scale down

## 15. Summary, Docker Cheatsheets, Feedback
### 1. All Powerpoints and Docker Cheatsheet
### 2. Summary and Feedback
======== list file ========