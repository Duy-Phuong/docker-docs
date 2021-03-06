C:\Users\Admin\AppData\Local\Programs\Python\Python38-32\python.exe E:/programing/language/python/python-docs/readfile.py
======== name dir ========

[TOC]

---

- [1. Introduction](#1-introduction)
  - [1. Welcome Course Objectives and Overview](#1-welcome-course-objectives-and-overview)
  - [2. Course Focus and Approach](#2-course-focus-and-approach)
  - [3. Build Maturity](#3-build-maturity)
  - [4. What is Jenkins](#4-what-is-jenkins)
  - [5. About the Instructor](#5-about-the-instructor)
- [2. Full Installation](#2-full-installation)
  - [1. Overview](#1-overview)
  - [2. Windows Installation](#2-windows-installation)
  - [3. Mac Installation](#3-mac-installation)
  - [4. Linux Installation](#4-linux-installation)
- [3. The Basics](#3-the-basics)
  - [1. The Basics Overview](#1-the-basics-overview)
  - [2. The First Job](#2-the-first-job)
  - [3. Jenkins Dashboard](#3-jenkins-dashboard)
  - [4. Failing Jobs](#4-failing-jobs)
  - [5. Copy and Rename Jobs](#5-copy-and-rename-jobs)
  - [6. Update Plugins](#6-update-plugins)
  - [7. Delete a Job](#7-delete-a-job)
  - [8. Manage Jenkins](#8-manage-jenkins)
  - [9. Jenkins Configuration](#9-jenkins-configuration)
- [4. Maven Projects](#4-maven-projects)
  - [1. Maven Projects Overview](#1-maven-projects-overview)
  - [2. Confirm Maven Project Outside Jenkins](#2-confirm-maven-project-outside-jenkins)
  - [2.1 httpsgithub.comjenkins-training.html](#21-httpsgithubcomjenkins-traininghtml)
  - [3. Maven Freestyle](#3-maven-freestyle)
  - [4. Jenkins Workspace](#4-jenkins-workspace)
  - [5. Maven Jobs](#5-maven-jobs)
  - [6. Maven Build Modules](#6-maven-build-modules)
  - [7. Failed Maven Projects](#7-failed-maven-projects)
  - [8. Scheduling Jenkins Jobs](#8-scheduling-jenkins-jobs)
  - [9. Source Control Polling in Jenkins](#9-source-control-polling-in-jenkins)
  - [10. Jenkins Tabs](#10-jenkins-tabs)
  - [11. Jenkins Home Directory](#11-jenkins-home-directory)
  - [12. Upgrading Jenkins](#12-upgrading-jenkins)
- [5. Tests and Quality Analysis Continuous Inspection](#5-tests-and-quality-analysis-continuous-inspection)
  - [1. Continuous Inspection Overview](#1-continuous-inspection-overview)
  - [2. Project Source Review (Unit Tests and updates for quality analysis)](#2-project-source-review-unit-tests-and-updates-for-quality-analysis)
  - [3. Quality Analysis Plugins and Configuration](#3-quality-analysis-plugins-and-configuration)
  - [4. Build and Review](#4-build-and-review)
  - [5. Unit Testing in Jenkins](#5-unit-testing-in-jenkins)
  - [6. Reviewing Quality Analysis](#6-reviewing-quality-analysis)
  - [7. Enforcing Minimum Quality Scores](#7-enforcing-minimum-quality-scores)
  - [8. Improving Quality Scores](#8-improving-quality-scores)
- [6. Publishing Build Artifacts to an Artifact Repository](#6-publishing-build-artifacts-to-an-artifact-repository)
  - [1. Publishing Overview](#1-publishing-overview)
  - [2. Maven Repository Plugin and Configuration](#2-maven-repository-plugin-and-configuration)
  - [3. Build and Review Artifact Publishing](#3-build-and-review-artifact-publishing)
- [7. Build Artifact Deployment with Jenkins](#7-build-artifact-deployment-with-jenkins)
  - [1. Deployment Overview](#1-deployment-overview)
  - [2. Tomcat Installation](#2-tomcat-installation)
  - [2.1 httptomcat.apache.org.html](#21-httptomcatapacheorghtml)
  - [3. Deployment Plugin](#3-deployment-plugin)
  - [4. Deployment](#4-deployment)
- [8. Security in Jenkins](#8-security-in-jenkins)
  - [1. Security Overview](#1-security-overview)
  - [2. Manually Disable Security](#2-manually-disable-security)
  - [3. Enable Security and Login](#3-enable-security-and-login)
  - [4. Adding Users in Matrix-Based Security](#4-adding-users-in-matrix-based-security)
  - [5. Users Role](#5-users-role)
  - [6. Project Role](#6-project-role)
- [9. AWS Lightsail for Jenkins Production](#9-aws-lightsail-for-jenkins-production)
  - [1. Jenkins Production Using Lightsail Overview](#1-jenkins-production-using-lightsail-overview)
  - [2. AWS Signup](#2-aws-signup)
  - [2.1 httpsaws.amazon.com.html](#21-httpsawsamazoncomhtml)
  - [3. Course Repository](#3-course-repository)
  - [3.1 httpsgithub.comjenkins-training.html](#31-httpsgithubcomjenkins-traininghtml)
  - [4. Jenkins Instance](#4-jenkins-instance)
  - [5. Static IP Address and DNS](#5-static-ip-address-and-dns)
  - [6. Instance Access](#6-instance-access)
  - [7. Jenkins Setup](#7-jenkins-setup)
  - [8. Restart within Lightsail](#8-restart-within-lightsail)
  - [9. Instance Snapshots](#9-instance-snapshots)
  - [10. Instance Flip](#10-instance-flip)
  - [11. Clean Up](#11-clean-up)
  - [12. Update HostKey](#12-update-hostkey)
  - [13. Web Secured, Part 1](#13-web-secured-part-1)
  - [14. Web Secured, Part 2](#14-web-secured-part-2)
  - [15. Update Jenkins](#15-update-jenkins)
  - [16. Beyond Lightsail](#16-beyond-lightsail)
- [10. Course Errata and Updates](#10-course-errata-and-updates)
  - [1. Jenkins Incompatibility with Java 9, 10 and 11.html](#1-jenkins-incompatibility-with-java-9-10-and-11html)
  - [2. Known Issue Maven Projects Fail with POM Parse Error.html](#2-known-issue-maven-projects-fail-with-pom-parse-errorhtml)
  - [3. Maven Repository Server plugin causes Build Failure.html](#3-maven-repository-server-plugin-causes-build-failurehtml)
  - [4. Resolve Problem with MacOS Upgrade Breaking Git (new!)](#4-resolve-problem-with-macos-upgrade-breaking-git-new)
- [11. Conclusion](#11-conclusion)
  - [1. Final Thoughts](#1-final-thoughts)
- [12. Bonus Full Install on Windows](#12-bonus-full-install-on-windows)
  - [1. 32 vs 64-bit Windows](#1-32-vs-64-bit-windows)
  - [2. Google Chrome on Windows](#2-google-chrome-on-windows)
  - [2.1 httpswww.google.comchrome.html](#21-httpswwwgooglecomchromehtml)
  - [3. Git for Windows](#3-git-for-windows)
  - [3.1 httpsgit-scm.com.html](#31-httpsgit-scmcomhtml)
  - [4. Git Configuration](#4-git-configuration)
  - [5. Atom Installation on Windows](#5-atom-installation-on-windows)
  - [5.1 Atom Text Editor Website..html](#51-atom-text-editor-websitehtml)
  - [6. Atom Configuration](#6-atom-configuration)
  - [7. Java Installation on Windows](#7-java-installation-on-windows)
  - [7.1 Java Download.html](#71-java-downloadhtml)
  - [8. Java Configuration](#8-java-configuration)
  - [9. Maven Installation on Windows](#9-maven-installation-on-windows)
  - [9.1 Apache Maven 3.3.9 Binary Archive (Zip).html](#91-apache-maven-339-binary-archive-ziphtml)
  - [10. Jenkins Installation on Windows](#10-jenkins-installation-on-windows)
  - [10.1 Jenkins 1.651.3 LTS.html](#101-jenkins-16513-ltshtml)
  - [11. Jenkins Getting Started](#11-jenkins-getting-started)
  - [12. Starting and Stopping Jenkins via Windows Services](#12-starting-and-stopping-jenkins-via-windows-services)
  - [13. Installation Notes for Windows 10 (Updated).html](#13-installation-notes-for-windows-10-updatedhtml)
  - [13.1 Installation.pdf.pdf](#131-installationpdfpdf)
- [13. Bonus Special Offers](#13-bonus-special-offers)
  - [1. Bonus Exclusive Student Discounts.html](#1-bonus-exclusive-student-discountshtml)

---

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

RSS stands for Really Simple Syndication and is a format that describes information in a digestible, news feed like, data stream for consumption and display by newsreaders.

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

![image-20200622205634769](jenkins-bootcamp.assets/image-20200622205634769.png)

### 2. Confirm Maven Project Outside Jenkins

https://github.com/jenkins-training

https://github.com/jenkins-training/time-tracker

Đăng nhập và fork this project

![image-20200622210155021](jenkins-bootcamp.assets/image-20200622210155021.png)  

```shell
git clone
cd time-tracker
mvn clean package
```

Phần 3:

Vào localhost 8080 đăng nhập jenkins

![image-20200622210828782](jenkins-bootcamp.assets/image-20200622210828782.png)  

Choose freestyle

![image-20200622210954471](jenkins-bootcamp.assets/image-20200622210954471.png)  

Vào build chọn build step là Execute windows batch command

![image-20200622211032397](jenkins-bootcamp.assets/image-20200622211032397.png)  

![image-20200622211245640](jenkins-bootcamp.assets/image-20200622211245640.png)  

Sau đó click on Build now

![image-20200622211344648](jenkins-bootcamp.assets/image-20200622211344648.png)  

Click on the date of green ball

![image-20200622211440869](jenkins-bootcamp.assets/image-20200622211440869.png)  

xuất hiện mới

Click on console ouput

![image-20200622211515654](jenkins-bootcamp.assets/image-20200622211515654.png)  

Click on FUll log kéo xuống dưới cùng thấy BUild success

![image-20200622211859058](jenkins-bootcamp.assets/image-20200622211859058.png)  

![image-20200622211936900](jenkins-bootcamp.assets/image-20200622211936900.png)  

Save => Build now

![image-20200622212046359](jenkins-bootcamp.assets/image-20200622212046359.png)  

Vào console output 



### 2.1 httpsgithub.comjenkins-training.html

### 3. Maven Freestyle

### 4. Jenkins Workspace

Click on workspace



![image-20200622212241052](jenkins-bootcamp.assets/image-20200622212241052.png)

Khám phá thư mục

### 5. Maven Jobs

Lý do không cài nhiều plugin vì làm jenkins chậm

Click Manage Jenkins ở dashboard/ 

Search maven và chọn 2 cái

![image-20200622213141106](jenkins-bootcamp.assets/image-20200622213141106.png)  

Sau đó click download

![image-20200622213231053](jenkins-bootcamp.assets/image-20200622213231053.png)  

Check restart

![image-20200622213318531](jenkins-bootcamp.assets/image-20200622213318531.png)  

choose maven and click ok

![image-20200622213441716](jenkins-bootcamp.assets/image-20200622213441716.png)  

copy link git paste

![image-20200622213534241](jenkins-bootcamp.assets/image-20200622213534241.png)  

Sau đó ấn save



### 6. Maven Build Modules

Click build now and check console

![image-20200622213740268](jenkins-bootcamp.assets/image-20200622213740268.png)  

![image-20200622213806877](jenkins-bootcamp.assets/image-20200622213806877.png)  

Click o Time Tracker

![image-20200622214104226](jenkins-bootcamp.assets/image-20200622214104226.png)  

Back to time tracker



### 7. Failed Maven Projects

Vào core/pom.xml sửa cho sai

### 8. Scheduling Jenkins Jobs

![image-20200622220816884](jenkins-bootcamp.assets/image-20200622220816884.png)  

![image-20200622220922641](jenkins-bootcamp.assets/image-20200622220922641.png)  

Sau đó chờ nó sẽ tự động build

### 9. Source Control Polling in Jenkins

Vào config/ build triggers and uncheck Build periodically

![image-20200622222508355](jenkins-bootcamp.assets/image-20200622222508355.png)  

Save

detect change on git and build

Thay đổi file readme.md ở git 



![image-20200622222639418](jenkins-bootcamp.assets/image-20200622222639418.png)  

Chọn git polling log

Sau đó thay số 3 thành 15 minutes rồi ấn Apply

Change descriptions

![image-20200622222856085](jenkins-bootcamp.assets/image-20200622222856085.png)  

Save



### 10. Jenkins Tabs

Click on plus 

![image-20200622223030850](jenkins-bootcamp.assets/image-20200622223030850.png)  

![image-20200622223050426](jenkins-bootcamp.assets/image-20200622223050426.png)  

![image-20200622223119343](jenkins-bootcamp.assets/image-20200622223119343.png)  

Check on maven freestyle and time tracker

![image-20200622223200945](jenkins-bootcamp.assets/image-20200622223200945.png)  

![image-20200622223316110](jenkins-bootcamp.assets/image-20200622223316110.png)  

Create new free style project, create new job with free style and this one will be displayed on all and Free style project

and the reason why we have on this tab because we create job in this tab

![image-20200622223504547](jenkins-bootcamp.assets/image-20200622223504547.png)  

Now we click on Delete View to delete tab

### 11. Jenkins Home Directory

Trên linux var/lib/jenkins

windows

![image-20200622224044146](jenkins-bootcamp.assets/image-20200622224044146.png)

![image-20200622224035342](jenkins-bootcamp.assets/image-20200622224035342.png)

### 12. Upgrading Jenkins

![image-20200622224233978](jenkins-bootcamp.assets/image-20200622224233978.png)  

CLick on change log để biết update những gì tại manage jenkins

![image-20200622224357186](jenkins-bootcamp.assets/image-20200622224357186.png)  

CLick on restart

![image-20200622224447240](jenkins-bootcamp.assets/image-20200622224447240.png)  

update trên linux và mac

```shell
sudo apt-get update
sudo apt-get upgrade -y

```



![image-20200622224645597](jenkins-bootcamp.assets/image-20200622224645597.png)  

click manage plugin

 ![image-20200622224906301](jenkins-bootcamp.assets/image-20200622224906301.png)  

Check now/ All/ Download

## 5. Tests and Quality Analysis Continuous Inspection

### 1. Continuous Inspection Overview

![image-20200622225931232](jenkins-bootcamp.assets/image-20200622225931232.png)

### 2. Project Source Review (Unit Tests and updates for quality analysis)

Xem trong pom của time tracker và core



### 3. Quality Analysis Plugins and Configuration

Vào mange plugin 

![image-20200622230640570](jenkins-bootcamp.assets/image-20200622230640570.png)  

Search pmd, find bug, check style

![image-20200622230732687](jenkins-bootcamp.assets/image-20200622230732687.png)  

check download and restart

![image-20200622230820373](jenkins-bootcamp.assets/image-20200622230820373.png)  

![image-20200622230834465](jenkins-bootcamp.assets/image-20200622230834465.png)  

chọn cả 3

![image-20200622230900981](jenkins-bootcamp.assets/image-20200622230900981.png)  

The first way is to simply add the "site" target to our Maven command.
That will trigger the analysis plugin while the site plugin attempts to build and HTML report for all the findings.
Basically it would run the analysis after all the parts of the build.

The other approach is to **specify the plugin go for each of the analysis tools** we're going to use .
Using this approach we'll run the analysis more in line with the rest of the build.
Let's use that approach, since I really don't need the HTML report provided by the "site" goal.

![image-20200622231545539](jenkins-bootcamp.assets/image-20200622231545539.png)  

Save

### 4. Build and Review

Click on build now

![image-20200622231822871](jenkins-bootcamp.assets/image-20200622231822871.png)  

![image-20200622231916492](jenkins-bootcamp.assets/image-20200622231916492.png)  

![image-20200622232002393](jenkins-bootcamp.assets/image-20200622232002393.png)  

![image-20200622232128553](jenkins-bootcamp.assets/image-20200622232128553.png)  

Click on time tracker 

![image-20200622232229397](jenkins-bootcamp.assets/image-20200622232229397.png)  

  

### 5. Unit Testing in Jenkins

Ctrl F: surfile

Check in console

![image-20200622232941361](jenkins-bootcamp.assets/image-20200622232941361.png)  

![image-20200622233217571](jenkins-bootcamp.assets/image-20200622233217571.png)  

![image-20200622233529074](jenkins-bootcamp.assets/image-20200622233529074.png)  

![image-20200622233602884](jenkins-bootcamp.assets/image-20200622233602884.png)  

Click into module

![image-20200622233641767](jenkins-bootcamp.assets/image-20200622233641767.png)  

![image-20200622233701613](jenkins-bootcamp.assets/image-20200622233701613.png)  

![image-20200622233901483](jenkins-bootcamp.assets/image-20200622233901483.png)  

change to false to test

![image-20200622234031696](jenkins-bootcamp.assets/image-20200622234031696.png)

### 6. Reviewing Quality Analysis

click in last build #10

![image-20200622234308386](jenkins-bootcamp.assets/image-20200622234308386.png)  

bên trái cũng có link tương ứng vs 3 plugin

![image-20200622234516524](jenkins-bootcamp.assets/image-20200622234516524.png)  

Tương tự check vào từng tab để xem kĩ



### 7. Enforcing Minimum Quality Scores

![image-20200623000340165](jenkins-bootcamp.assets/image-20200623000340165.png)  

![image-20200623000418332](jenkins-bootcamp.assets/image-20200623000418332.png)  

![image-20200623000443934](jenkins-bootcamp.assets/image-20200623000443934.png)  

![image-20200623000526290](jenkins-bootcamp.assets/image-20200623000526290.png)  

Sau đó check Build now

![image-20200623000618356](jenkins-bootcamp.assets/image-20200623000618356.png)  

![image-20200623001314249](jenkins-bootcamp.assets/image-20200623001314249.png)  

The top row, with the yellow ball, refers to thresholds to consider the build unstable.

The bottom row is the threshold to fail the build.

For example, on this project, I want to consider the build unstable
if we have more than 10 warnings, regardless of the priority.
Placing a zero in the high priority column will trip the unstable status if one or more high priority warnings is found.

I place a 5 for normal and 10 for low, making these unstable thresholds for those categories respectively.

That means, provided we don't exceed 10 warnings total, the project can have up to five normal priority
warnings and still get a success or green ball.

Let's pick some reasonable thresholds for failing the build, which is the bottom row.

For all priorities let's use 100. For high, normal, and low use 40, 75, and blank respectively.

That means, if the project has more than 40 high priority warnings or more than 75 normal priority warnings

Jenkins will automatically fail the build, which will also happen if any combination exceeds 100 warnings.

The last field, for low priority warnings, is left blank



### 8. Improving Quality Scores

## 6. Publishing Build Artifacts to an Artifact Repository

### 1. Publishing Overview

![image-20200623002011254](jenkins-bootcamp.assets/image-20200623002011254.png)

### 2. Maven Repository Plugin and Configuration

![image-20200623002253883](jenkins-bootcamp.assets/image-20200623002253883.png)  

![image-20200623002623947](jenkins-bootcamp.assets/image-20200623002623947.png)  

Nếu xuất hiện như trên là success

Rename

![image-20200623002420179](jenkins-bootcamp.assets/image-20200623002420179.png)  

Choose advanced

![image-20200623002503890](jenkins-bootcamp.assets/image-20200623002503890.png)  

![image-20200623002544249](jenkins-bootcamp.assets/image-20200623002544249.png)  



### 3. Build and Review Artifact Publishing

Build now

CHọn enable auto refresh

![image-20200623002759357](jenkins-bootcamp.assets/image-20200623002759357.png)  

![image-20200623002857901](jenkins-bootcamp.assets/image-20200623002857901.png)  

copy Url paste

Click bên trái cũng tương tự nhưng thêm 1 level

![image-20200623003149644](jenkins-bootcamp.assets/image-20200623003149644.png)  

![image-20200623003239981](jenkins-bootcamp.assets/image-20200623003239981.png)  

project/ training/ time tracker core

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
