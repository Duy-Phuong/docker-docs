C:\Users\Admin\AppData\Local\Programs\Python\Python38-32\python.exe E:/programing/language/python/python-docs/readfile.py
======== name dir ========

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