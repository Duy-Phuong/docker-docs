

C:\Users\Admin\AppData\Local\Programs\Python\Python38-32\python.exe E:/programing/language/python/python-docs/readfile.py
======== name dir ========

[TOC]



## 1. Introduction
### 1. Welcome Course Objectives and Overview

https://www.udemy.com/course/jenkins-continuous-integration-bootcamp/

### 2. Course Focus and Approach
### 3. Build Maturity

![image-20200621192125324](jenkins-bootcamp.assets/image-20200621192125324.png)  

![image-20200621192305043](jenkins-bootcamp.assets/image-20200621192305043.png)  

![image-20200621192850249](jenkins-bootcamp.assets/image-20200621192850249.png)

Many people actually use the term continuous inspection and continuous integration interchangeably.
However, to me, in order really achieve true continuous integration we need a branching strategy, and an approach for integration of the
changes into the main development branch, and a release policy for production.

**Continuous integration** includes everything from continuous inspection but adds a structure branching strategy and a release management policy. 

The automated building and running of unit tests and code quality tools is just continuous inspection.

**Jenkins** can serve as a central part of a robust continuous integration pipeline

### 4. What is Jenkins

![image-20200621194815915](jenkins-bootcamp.assets/image-20200621194815915.png)

As with any software Jenkins has to run on a host system.

This system determines which installer is used for Jenkins and the tools available for the use.
Jenkins runs on top of a Java web application container or application server. By default this is Jetty, but Jenkin's can be deployed
to any web application server with the right set up.

Since Jenkins runs on a Java web application server, a java runtime is required.
You should run Jetty and Jenkins on a Java development kit or JDK instead of just the Java runtime engine, so Jenkins can access the JDK tools when needed.
On most operating systems there is a small program called a **service** 
that is responsible for starting stopping and monitoring Jetty and the Jenkins application
Within **Jenkins views** provide a nice way to group projects or folders together.

![image-20200621203117340](jenkins-bootcamp.assets/image-20200621203117340.png)  



### 5. About the Instructor

## 2. Full Installation
### 1. Overview

![image-20200621204912354](jenkins-bootcamp.assets/image-20200621204912354.png)

### 2. Windows Installation

![image-20200621205138872](jenkins-bootcamp.assets/image-20200621205138872.png)  

![image-20200621205229205](jenkins-bootcamp.assets/image-20200621205229205.png)  

![image-20200621205511991](jenkins-bootcamp.assets/image-20200621205511991.png)  

![image-20200621205913119](jenkins-bootcamp.assets/image-20200621205913119.png)  

To validate maven: `mvn -v`

![image-20200621211033012](jenkins-bootcamp.assets/image-20200621211033012.png)  

![image-20200621211219021](jenkins-bootcamp.assets/image-20200621211219021.png)  

![image-20200621211258135](jenkins-bootcamp.assets/image-20200621211258135.png)

### 3. Mac Installation

### 4. Linux Installation

## 3. The Basics
### 1. The Basics Overview

![image-20200621211429443](jenkins-bootcamp.assets/image-20200621211429443.png)  

![image-20200621211442882](jenkins-bootcamp.assets/image-20200621211442882.png)

### 2. The First Job

![image-20200621211830451](jenkins-bootcamp.assets/image-20200621211830451.png)  

![image-20200621211915304](jenkins-bootcamp.assets/image-20200621211915304.png)  

Click on create new job

![image-20200621212148433](jenkins-bootcamp.assets/image-20200621212148433.png)  

Add build step

![image-20200621212554675](jenkins-bootcamp.assets/image-20200621212554675.png)  

**If you are on Mac or Linux choose execute shell instead.**

![image-20200621213047625](jenkins-bootcamp.assets/image-20200621213047625.png)  

mở cmd lên gõ echo "hi" để test

click build now

![image-20200621214653305](jenkins-bootcamp.assets/image-20200621214653305.png)  

Nếu xuất hiện chấm xanh phía dưới là success

![image-20200621215257888](jenkins-bootcamp.assets/image-20200621215257888.png)  

We click on the ball

![image-20200621215349479](jenkins-bootcamp.assets/image-20200621215349479.png)  

Ấn vào view as plain text để xem full



### 3. Jenkins Dashboard

Click back to dashboard

![image-20200621215833468](jenkins-bootcamp.assets/image-20200621215833468.png)  

Chọn vào Hello world link để xem last build success là 2

Click on legend

![image-20200621220306863](jenkins-bootcamp.assets/image-20200621220306863.png)  

![image-20200621220319761](jenkins-bootcamp.assets/image-20200621220319761.png)  

RSS stands for Really Simple Syndication  and is a format that describes information in a digestible, news feed like, data stream for consumption and display by newsreaders.

### 4. Failing Jobs

Click on configure

![image-20200621221105593](jenkins-bootcamp.assets/image-20200621221105593.png)  

Back to dashboard

![image-20200621221149558](jenkins-bootcamp.assets/image-20200621221149558.png) 

![image-20200621221226159](jenkins-bootcamp.assets/image-20200621221226159.png)  

Click build now

![image-20200621221249015](jenkins-bootcamp.assets/image-20200621221249015.png)  

![image-20200621221311855](jenkins-bootcamp.assets/image-20200621221311855.png)  

Red ball

![image-20200621221411164](jenkins-bootcamp.assets/image-20200621221411164.png)  

![image-20200621221452076](jenkins-bootcamp.assets/image-20200621221452076.png)  

Back to dashboard

Khi ấn nút build lại bên trái thì nhiều lần và f5 page => weather rain  

![image-20200621221543842](jenkins-bootcamp.assets/image-20200621221543842.png)  

![image-20200621221852682](jenkins-bootcamp.assets/image-20200621221852682.png)  

Config project có thể chọn disable

![image-20200621221949215](jenkins-bootcamp.assets/image-20200621221949215.png)

### 5. Copy and Rename Jobs

![image-20200621222737386](jenkins-bootcamp.assets/image-20200621222737386.png)  

![image-20200621222935116](jenkins-bootcamp.assets/image-20200621222935116.png)  

Sau khi ấn apply click vào button advanced tiếp

![image-20200621223056848](jenkins-bootcamp.assets/image-20200621223056848.png)  

The web URL remains the same short path from earlier but the display name is used for most other
places, including on the bread crumb trail.

localhost:8080/job/problem

![image-20200621223405817](jenkins-bootcamp.assets/image-20200621223405817.png)  

![image-20200621223425453](jenkins-bootcamp.assets/image-20200621223425453.png)  

Problems World is displayed

CLick on new Item

![image-20200621223529121](jenkins-bootcamp.assets/image-20200621223529121.png)  

choose copy from problem

![image-20200621223624629](jenkins-bootcamp.assets/image-20200621223624629.png)  

![image-20200621223655876](jenkins-bootcamp.assets/image-20200621223655876.png)  

Click on Build Now

![image-20200621223726020](jenkins-bootcamp.assets/image-20200621223726020.png)  

![image-20200621223851359](jenkins-bootcamp.assets/image-20200621223851359.png)

### 6. Update Plugins

Click on manage Jenkins

![image-20200621223934196](jenkins-bootcamp.assets/image-20200621223934196.png)  

choose manage plugins

Vào jenkins.io => plugin

![image-20200621224156888](jenkins-bootcamp.assets/image-20200621224156888.png)  

Choose Git

![image-20200621224231123](jenkins-bootcamp.assets/image-20200621224231123.png)  

click install without restart

![image-20200621224407462](jenkins-bootcamp.assets/image-20200621224407462.png)  

Normally I'm happy with the latest version of plugins, but in some cases you might want to
install an older version directly.

Click on Archives

![image-20200621225010199](jenkins-bootcamp.assets/image-20200621225010199.png)

Choose 1.14

![image-20200621225054293](jenkins-bootcamp.assets/image-20200621225054293.png)  

scroll down

![image-20200621225126176](jenkins-bootcamp.assets/image-20200621225126176.png)  

trỏ tới file.hpi vừa mới tải

vào url restart like below

![image-20200621225237101](jenkins-bootcamp.assets/image-20200621225237101.png) 

if ok green ball is displayed

![image-20200621230317201](jenkins-bootcamp.assets/image-20200621230317201.png)  

  

![image-20200621225856100](jenkins-bootcamp.assets/image-20200621225856100.png)  

Sau khi restart

Click download now

![image-20200621225944468](jenkins-bootcamp.assets/image-20200621225944468.png)  

![image-20200621230002837](jenkins-bootcamp.assets/image-20200621230002837.png)  

Check vào restart như hình

If you don't want to use green ball, you can uncheck on install plugins

![image-20200621230212188](jenkins-bootcamp.assets/image-20200621230212188.png)  

Afterwards, choose restart



### 7. Delete a Job

![image-20200621230350271](jenkins-bootcamp.assets/image-20200621230350271.png)   

![image-20200621230514392](jenkins-bootcamp.assets/image-20200621230514392.png)  

![image-20200621230556287](jenkins-bootcamp.assets/image-20200621230556287.png)  



### 8. Manage Jenkins

![image-20200621230736040](jenkins-bootcamp.assets/image-20200621230736040.png)  

The first item, which we will cover a bit later, is
the main configuration page for the Jenkins server.

Global security, also something we will cover later on in this course,
is where we will configure how people log in and general security policies for the server.

Credentials is where we set up and manage passwords, API keys, SSH keys and other credentials we would use with
plugins or connecting to other systems from Jenkins.

Global tools, which we will cover soon, is where we will configure the tools we will
use with Jenkins, like Git, Java, and Maven
"Reload Configuration from Disk" does exactly what you think:

it reloads the Jenkins configuration from the system disk.



### 9. Jenkins Configuration

![image-20200621232002996](jenkins-bootcamp.assets/image-20200621232002996.png)  

save

![image-20200621232059021](jenkins-bootcamp.assets/image-20200621232059021.png)  

First we have the number of executors.

That refers to the number of concurrent build threads or processes

that we can have at the same time, specifically on the master.
By default Jenkins sets this value to 2, which, for most systems, is rather low.

![image-20200621232243988](jenkins-bootcamp.assets/image-20200621232243988.png)  

click add jdk

uncheck install automatically on jdk

![image-20200621232425849](jenkins-bootcamp.assets/image-20200621232425849.png)  

![image-20200621232454798](jenkins-bootcamp.assets/image-20200621232454798.png)  

Click Apply

![image-20200621232609411](jenkins-bootcamp.assets/image-20200621232609411.png)  



## 4. Maven Projects
### 1. Maven Projects Overview

### 2. Confirm Maven Project Outside Jenkins
### 2.1 httpsgithub.comjenkins-training.html
### 3. Maven Freestyle
### 4. Jenkins Workspace
### 5. Maven Jobs
### 6. Maven Build Modules
### 7. Failed Maven Projects
### 8. Scheduling Jenkins Jobs
### 9. Source Control Polling in Jenkins
### 10. Jenkins Tabs
### 11. Jenkins Home Directory
### 12. Upgrading Jenkins
## 5. Tests and Quality Analysis Continuous Inspection
### 1. Continuous Inspection Overview
### 2. Project Source Review (Unit Tests and updates for quality analysis)
### 3. Quality Analysis Plugins and Configuration
### 4. Build and Review
### 5. Unit Testing in Jenkins
### 6. Reviewing Quality Analysis
### 7. Enforcing Minimum Quality Scores
### 8. Improving Quality Scores
## 6. Publishing Build Artifacts to an Artifact Repository
### 1. Publishing Overview
### 2. Maven Repository Plugin and Configuration
### 3. Build and Review Artifact Publishing
## 7. Build Artifact Deployment with Jenkins
### 1. Deployment Overview
### 2. Tomcat Installation
### 2.1 httptomcat.apache.org.html
### 3. Deployment Plugin
### 4. Deployment
## 8. Security in Jenkins
### 1. Security Overview
### 2. Manually Disable Security
### 3. Enable Security and Login
### 4. Adding Users in Matrix-Based Security
### 5. Users Role
### 6. Project Role
## 9. AWS Lightsail for Jenkins Production
### 1. Jenkins Production Using Lightsail Overview

### 2. AWS Signup
### 2.1 httpsaws.amazon.com.html
### 3. Course Repository
### 3.1 httpsgithub.comjenkins-training.html
### 4. Jenkins Instance
### 5. Static IP Address and DNS
### 6. Instance Access
### 7. Jenkins Setup
### 8. Restart within Lightsail
### 9. Instance Snapshots
### 10. Instance Flip
### 11. Clean Up
### 12. Update HostKey
### 13. Web Secured, Part 1
### 14. Web Secured, Part 2
### 15. Update Jenkins
### 16. Beyond Lightsail
## 10. Course Errata and Updates
### 1. Jenkins Incompatibility with Java 9, 10 and 11.html
### 2. Known Issue Maven Projects Fail with POM Parse Error.html
### 3. Maven Repository Server plugin causes Build Failure.html
### 4. Resolve Problem with MacOS Upgrade Breaking Git (new!)
## 11. Conclusion
### 1. Final Thoughts
## 12. Bonus Full Install on Windows
### 1. 32 vs 64-bit Windows

### 2. Google Chrome on Windows
### 2.1 httpswww.google.comchrome.html
### 3. Git for Windows
### 3.1 httpsgit-scm.com.html
### 4. Git Configuration
### 5. Atom Installation on Windows
### 5.1 Atom Text Editor Website..html
### 6. Atom Configuration
### 7. Java Installation on Windows
### 7.1 Java Download.html
### 8. Java Configuration
### 9. Maven Installation on Windows
### 9.1 Apache Maven 3.3.9 Binary Archive (Zip).html
### 10. Jenkins Installation on Windows
### 10.1 Jenkins 1.651.3 LTS.html
### 11. Jenkins Getting Started
### 12. Starting and Stopping Jenkins via Windows Services
### 13. Installation Notes for Windows 10 (Updated).html
### 13.1 Installation.pdf.pdf
## 13. Bonus Special Offers
### 1. Bonus Exclusive Student Discounts.html