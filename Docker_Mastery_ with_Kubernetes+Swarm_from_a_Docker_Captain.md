## 1. Course Introduction and Docker Intro
### 1. Course Roadmap (overview)
### 2. November 2019 Update!
### 3. Why Docker Why Now

Docker focus on the migration experience

### 3.1 S01 Why Docker Slides.pdf
### 4. Getting Course Resources (GitHub Repo).html

All examples and assignment files are in a [single code repository on GitHub](https://github.com/bretfisher/udemy-docker-mastery). Each folder represents a single lecture video (but not all lectures have a folder, as not all need code). **You should clone this repo** into your user profile somewhere on your host. (`c:/Users/username/` on Windows and `/Users/username` on Mac). Having inside your user profile will ensure Docker works correctly on Mac and Windows. The location doesn't matter for Linux hosts. `git clone https://github.com/BretFisher/udemy-docker-mastery.git` 

If you're rather new to GitHub, you can download the GUI to make it very easy to push/pull code at https://desktop.github.com/ for Mac and Windows. A great alternative Git client is https://www.gitkraken.com/.

We won't use git much in this course but [knowing the basics](https://try.github.io) of pulling code, committing code, and pushing updates could be helpful at times in the course.

### 4.1 Docker_CheatSheet_08.09.2016_0.pdf
### 4.4 GitHub Repository For This Course.html

[GitHub - BretFisher/udemy-docker-mastery: Udemy Course to build, compose, deploy, and manage containers from local development to high-availability in the cloud](https://github.com/bretfisher/udemy-docker-mastery)



### 5. Course Chat 35k Students Learning Containers.html

**Get more out of this course by getting live help from other students and chatting with my DevOps community.**

**With this course, you have access to two options: Slack and Discord.** Read on, and **join one or both communities:**

#### Discord

Discord used to be a gamer-focused chat app, with lots of fun features and integrations, but they have now broadened to support all open communities, and it's a modern IRC-like way to interact. **It's my favorite chat system for open source communities.**

**Join my "Vital DevOps" Discord server and gain access to a special channel for this course:** [**https://discord.gg/AnP5pgM**](https://discord.gg/AnP5pgM)

![img](https://udemy-images.s3.amazonaws.com:443/redactor/raw/article_lecture/2020-11-23_22-09-22-b5c3a63422879952edbb1adc1fabbead.png)

#### Slack

If you prefer Slack, it has over 35,000 students that have helped each other learn container tools. Slack is a fantastic private, persistent chat product that I use in so many of the communities I'm in and thought it would be a great way for extending this course and adding more value to your learning. It comes with clients for all desktop and mobile OS's and also works in the browser.

![img](https://udemy-images.s3.amazonaws.com:443/redactor/raw/2019-11-27_22-03-41-7422363eb9c2e39a3e2524aba832f2fc.png)

**Steps to Join My Slack Team:**

1. Go to [chat.bretfisher.com](https://chat.bretfisher.com) and give it your email address.
2. You will be sent an email from Slack, with an invite link inside it.
3. Click that link in the email.
4. Fill out the form to create your Slack account.
5. Use that Slack account to access [dockermastery.slack.com](https://dockermastery.slack.com)

(I know that's a lot of steps, but since Udemy doesn't give me your email address, I have no way to pre-create you an account on Slack, and Slack is an invite-only system... so the first step is a way for it to auto-generate an invite for you. :)

Sign up and join the Docker and Kubernetes DevOps community!

### 6. YouTube Live Q&A with Bret.html

If you're just starting the course, or even already finished with the courses and have questions, I invite you to join me for an "Ask Me Anything" style of hangout. Every week (usually Thursday's) I spend an hour answering your questions about this course, containers, and general DevOps topics. It's scheduled and announced [on my YouTube Channel](https://www.youtube.com/channel/UC0NErq0RhP51iXx64ZmyVfg), so **be sure to subscribe and then click the bell to get alerts**.

[**Hope to see you there!**](https://www.youtube.com/channel/UC0NErq0RhP51iXx64ZmyVfg)

### 7. The Big FAQ.html

This course has over 5,000 a month taking it! That's amazing to me. It also means we get lots of the same questions. Some are just things I didn't explain clearly. Some are minor issues people hit along the way. Here's the most common Q&A in order of frequency.

**NOTE: Don't read all these now, but remember to come back when you hit a issue, This list is the FASTEST way to solve your issues for common course troubles.**

#### I'm using Docker Toolbox, and http://localhost isn't working. What's wrong?

Docker Toolbox uses a default IP of http://192.168.99.100 and doesn't support the localhost feature of Docker for Windows/Mac.

#### $(pwd) in Windows Is getting an error for bind-mounts: C:\Program Files\Docker Toolbox\docker.exe: invalid reference format.

PowerShell has a few minor differences in command format. This is a PowerShell thing, not a docker thing. When using the shell path shortcut "pwd":

For PowerShell use: `${pwd}` 

For cmd.exe "Command Prompt use: `%cd%`

bash, sh, zsh, and Docker Toolbox Quickstart Terminal use: `$(pwd)` 

Note, if you have spaces in your path, you'll usually need to quote the whole path in the docker command.

There's another issue sometimes seen, where other apps can mess up your path: https://stackoverflow.com/questions/50608301/docker-mounted-volume-adds-c-to-end-of-windows-path-when-translating-from-linux

#### I hit Ctrl-C in Windows and The Container is Still Running

In Windows, there's a quirk with the built-in Powershell and Command Prompt terminals. They don't interpret ctrl-c the same way as Linux, Unix, and macOS. They won't shutdown the container, and you'll need to use `docker stop` commands. Sorry for the confusion.

#### PowerShell Tab Completion Isn't Working Or I Can't Find the Page in Docs

The posh-docker repo is no longer being maintained, but a new better one now exists at https://github.com/matt9ucci/DockerCompletion so give that a shot. Then please thank the author if it works for you so they keep it updated. Yay open source!

#### I'm using Docker Toolbox and bind-mounts aren't working (sharing files between Windows and docker with -v  )

Docker Toolbox requires your files be in your profile under `c:\users\<username>\`  before file sharing will work in Toolbox.

#### Bind for 0.0.0.0:80 failed: port is already allocated. -OR- port already in use -OR- permission denied.

This will happen if you are attempting to start a new container with a port that is already in-use on your machine. Remember in TCP/UDP, only one application/service can use a single IP+PORT at a time. This doesn’t change with containers when you use `-p` to bind to the host IP+PORT.

First run docker container ls to check if there are any containers using this port - if there are not; you likely have a non-Docker related application running on your machine that is using this port. Maybe IIS, maybe Apache, etc.

If you are on a Mac, you can check what is using port 80 with the command: `lsof -i :80 ` 

If you are on Windows, you can check what is using port 80 with: `netstat` 

Of course - if you don’t have a reason to specifically use the port that is throwing this error, simply run your container on another port. Remember, the syntax is `<host port>:<container port>` , so binding to port 8888 on your host machine with a container that uses port 80, would look like: `docker container run -p 8888:80 your_image` 

#### How do I cleanup space (images etc.)?

Run prune commands https://www.udemy.com/docker-mastery/learn/v4/t/lecture/7407918?start=0

#### Bind Mount Won't Show Up In Container

This is usually a Docker for Windows issue, where you need to go into Docker Settings GUI (lower right icon) and uncheck the drive where your code is, then save, and then re-check that drive to re-apply the SMB file sharing permissions between the Linux VM and the Windows OS.

#### Starting container process caused "exec: \"ping\": executable file not found in $PATH": unknown

That error is telling you that ping is not available in the image you’re trying to run it from. Official images have changed over time and the official nginx default image (nginx:latest) no longer has ping in it by default. Image nginx:alpine should still have ping installed (a few of my videos show utilities like ping that are no longer in those images).

If it's a debian-based image (the default nginx) then you can also use `apt-get update && apt-get install -y iputils-ping`  inside the container to install it.

Lastly, I keep a “bunch of troubleshooting and handy admin utilities” in an image here that you can run ping from: `bretfisher/netshoot` 

https://www.udemy.com/docker-mastery/learn/v4/questions/3751216

#### Starting mysql container and running ps causes "ps: command not found"

Like above, this is the container shell telling you the binary "ps" isn't in your path, and not installed in the container. Docker changed the mysql image after the video was recorded and removed the ps utility. You can add it back in using the apt package manager.

```
apt-get update && apt-get install procps
```

For more info: https://stackoverflow.com/questions/26982274/ps-command-doesnt-work-in-docker-container

#### How to run two container websites on a single port in Docker or Swarm services

This is a bit more advanced, but common for production Swarms. You'll need a "reverse proxy"

https://www.udemy.com/docker-mastery/learn/v4/questions/3931678

#### Error response from daemon: pull access denied.

Double and triple-check the spelling of the image you are pulling; if you are attempting to pull a publicly hosted image - this error will not occur, but if there is a typo and Docker can’t find the image - it will expect that it is a private image and ask you to login.

Also, there are times when the config.json file gets messed up, so try docker logout && docker login. If all that still causes the same issue, try removing `~/.docker/config.json` and then pull again.

#### Kubernetes vs. Swarm.

https://www.udemy.com/docker-mastery/learn/v4/questions/3446126

#### Does this help with Docker Certified Associate?

Yes, but it’s not a study guide. Here’s the Lecture with info: https://www.udemy.com/docker-mastery/learn/v4/t/lecture/9485678?start=0

#### Ubuntu Container vs. Ubuntu OS, What's the Difference?

https://www.udemy.com/docker-mastery/learn/v4/questions/5390204

#### How to use volumes in Swarm for databases.

https://www.udemy.com/docker-mastery/learn/v4/questions/2675184

#### How do we do backups in docker?

https://www.udemy.com/docker-mastery/learn/v4/questions/2756448

#### Getting a shell in VM’s that run Docker

Workaround: https://www.udemy.com/docker-mastery/learn/v4/questions/3860412

```
docker run -it --rm --privileged --pid=host justincormack/nsenter1 
```

macOS https://www.bretfisher.com/docker-for-mac-commands-for-getting-into-local-docker-vm/

Docker for Windows https://www.bretfisher.com/getting-a-shell-in-the-docker-for-windows-vm/

Docker Toolbox `docker-machine ssh default` 

#### Windows firewalls preventing networking or bind mounts in containers

https://www.udemy.com/docker-mastery/learn/v4/questions/3258290

#### Anti-Virus Blocking file sharing in Windows

https://www.udemy.com/docker-mastery/learn/v4/questions/3442460

#### Are containers more secure than VM’s?

https://www.udemy.com/docker-mastery/learn/v4/questions/4020880

#### I have a network proxy and images won’t build

https://stackoverflow.com/questions/23111631/cannot-download-docker-images-behind-a-proxy/

#### Public vs. Private IP for Swarm advertise-addr and data-path-addr

https://www.udemy.com/docker-mastery/learn/v4/questions/3710518

#### Custom Docker Networks, macvlan and IP setting hardcoding

https://www.udemy.com/docker-mastery/learn/v4/questions/3706540





## 2. The Best Way to Setup Docker for Your OS
### 1. Docker Editions Which Do I Use

```shell
# The Best Way to Set Up Docker for Your OS

## Docker for Windows 10 Pro/Ent: Setup and Tips

http://store.docker.com

docker version

cd .\udemy-docker-mastery\

docker ps

docker info

## Docker Toolbox for Windows 7, 8 and 10 Home: Setup and Tips

http://store.docker.com

cd .\udemy-docker-mastery\

docker-machine ls

docker-machine start

docker-machine ls

docker version

docker version

docker-machine ls

docker-machine help

docker-machine env default

docker version

## Docker for Mac Setup and Tips

http://store.docker.com

docker version

http://github.com/BretFisher/udemy-docker-mastery

docker version

docker container

docker container run --

docker

docker pause

## Docker for Linux Setup and Tips

docker

http://get.docker.com

curl -fsSL get.docker.com -o get-docker.sh

sh get-docker.sh

sudo usermod -aG docker bret

sudo docker version

docker version

sudo docker version

docker-machine version

http://github.com/docker/compose

http://github.com/docker/compose/releases

curl -L https://github.com/docker/compose/releases/download/1.15.0/docker-compose- `uname -s `- `uname -m` >/usr/local/bin/docker-compose

docker-compose version

http://github.com/docker/machine/releases

http://github.com/BretFisher/udemy-docker-mastery

git clone https://github.com/Bretfisher/udemy-docker-mastery.git

cd udemy-docker-mastery/

docker image

docker image ls --

```



### 1.2 S02 Docker Setup Slides 1.0.pdf
### 2. Installing Docker The Fast Way.html

If you don't already have docker installed, Docker already has some great guides on how to do it. The rest of this Section is about how to setup Docker on your specific OS, but if you already know which OS you want to install on, here's the short-list for downloading it. The videos after this Lecture are walkthroughs of installing Docker, getting the GitHub repo, getting a code editor, and tweaking the command line if you want to. Feel free to skip any and all of this if you have at least docker version 17.06 and like your current setup :)

**Installing on Windows 10 (Pro or Enterprise)**

This is the best experience on Windows, but due to OS feature requirements, it only works on the Pro and Enterprise editions of Windows 10 (with latest update rollups). You need to install ["Docker for Windows" from the Docker Store](https://www.docker.com/docker-windows).

With this Edition I recommend using PowerShell for the best CLI experience. See more info in the next few Lectures.

**Installing on Windows 7, 8, or 10 Home Edition**

Unfortunately, Microsoft's OS features for Docker and Hyper-V don't work in these older versions, and "Windows 10 Home" edition doesn't have Hyper-V, so you'll need to [install the Docker Toolbox](https://docs.docker.com/toolbox/overview/), which is a slightly different approach to using Docker with a VirtualBox VM. This means Docker will be running in a Virtual Machine that sits behind the IP of your OS, and uses NAT to access the internet.

**NOTE FOR TOOLBOX USERS**: For all examples that use `http://localhost` , **you'll need to replace with** `http://192.168.99.100`

**Installing on Mac**

You'll want to install [Docker for Mac](https://www.docker.com/docker-mac), which is great. If you're on an older Mac with less than OSX Yosemite 10.10.3, you'll need to [install the Docker Toolbox instead](https://docs.docker.com/toolbox/overview/).

**Installing on Linux**

**Do \*not\* use your built in default packages like** `**apt/yum install docker.io**` because those packages are old and not the Official Docker-Built packages. 

I prefer to use the Docker's automated script to add their repository and install all dependencies: `curl -sSL https://get.docker.com/ | sh` but you can also install in a more manual method by following specific instructions on the Docker Store for your distribution, like [this one for Ubuntu](https://store.docker.com/editions/community/docker-ce-server-ubuntu).

**What if None Of These Options Work**

Maybe you don't have local admin, or maybe your machine doesn't have enough resources. Well the best free option here is to use [play-with-docker.com](http://play-with-docker.com), which will run one or more Docker instances inside your browser, and give you a terminal to use it with. You can actually create multiple machines on it, and even use the URL to share the session with others in a sort of collaborative experience.  I highly recommend you check it out.  Most of the lectures in this course can be used with "PWD", but it's only limitation really is it's time bombed to 4 hours, at which time it'll delete your servers.

### 3. Windows Docker Options

![image-20210204005745148](Docker_Mastery_%20with_Kubernetes+Swarm_from_a_Docker_Captain.assets/image-20210204005745148.png)

If you store your code, you will choose C



Go to https://cmder.net/

![image-20210204010151518](Docker_Mastery_%20with_Kubernetes+Swarm_from_a_Docker_Captain.assets/image-20210204010151518.png)

Choose checkbox unblock

then we extract

![image-20210204010351748](Docker_Mastery_%20with_Kubernetes+Swarm_from_a_Docker_Captain.assets/image-20210204010351748.png)

Drag the Cmder.exe to the start menu below

https://draculatheme.com/cmder





### 4. Docker for Windows 10 ProEnt Setup and Tips
### 4.1 Download cmder (optional).html
### 4.2 Getting Started with Docker for Windows.html

[Docker Desktop for Windows user manual | Docker Documentation](https://docs.docker.com/docker-for-windows/)

### 4.3 Download Docker CE for Windows.html

[Docker Desktop for Windows - Docker Hub](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

### 4.4 Download GitHub Desktop.html

[GitHub Desktop | Simple collaboration from your desktop](https://desktop.github.com/)

### 4.5 Clone this GitHub Repo.html

[GitHub - BretFisher/udemy-docker-mastery: Udemy Course to build, compose, deploy, and manage containers from local development to high-availability in the cloud](https://github.com/BretFisher/udemy-docker-mastery)

### 4.6 Tab Completion for Windows PowerShell.html

[GitHub - matt9ucci/DockerCompletion: Docker command completion for PowerShell.](https://github.com/matt9ucci/DockerCompletion)

### 4.7 Docker for Windows FAQ.html

[Frequently asked questions | Docker Documentation](https://docs.docker.com/desktop/faqs/)

### 4.8 Download Visual Studio Code.html



### 5. Docker for Mac Setup and Tips

Watch again

### 5.1 Clone This GitHub Repo.html

https://github.com/BretFisher/udemy-docker-mastery

### 5.2 Logs and troubleshooting Docker for Mac.html

https://docs.docker.com/docker-for-mac/troubleshoot/

### 5.3 Docs Configure shell completion on Mac.html

https://docs.docker.com/docker-for-mac/#install-shell-completion

### 5.4 Download GitHub Desktop.html

https://desktop.github.com/

### 5.5 Download Visual Studio Code.html
### 5.6 Installing Homebrew (the brew CLI).html

https://brew.sh/

### 5.7 Download Docker CE for Mac.html

https://hub.docker.com/editions/community/docker-ce-desktop-mac

### 5.8 Download iTerm2.html

[iTerm2 - macOS Terminal Replacement](https://iterm2.com/)

### 6. Docker Toolbox for Win7, 8, and 10 Home Setup and Tips



### 6.1 Download GitHub Desktop.html
### 6.2 Download Visual Studio Code.html
### 6.3 Download cmder (optional).html
### 6.4 Clone this GitHub Repo.html

https://github.com/BretFisher/udemy-docker-mastery

### 6.5 Download Docker Toolbox.html

https://docs.docker.com/docker-for-windows/docker-toolbox/

**Deprecated**

Docker Toolbox has been deprecated and is no longer in active development. Please use Docker Desktop instead. See [Docker Desktop for Mac](https://docs.docker.com/docker-for-mac/) and [Docker Desktop for Windows](https://docs.docker.com/docker-for-windows/).

### 7. Docker for Linux Setup and Tips

![image-20210204223701091](Docker_Mastery_%20with_Kubernetes+Swarm_from_a_Docker_Captain.assets/image-20210204223701091.png)

![image-20210204223753536](Docker_Mastery_%20with_Kubernetes+Swarm_from_a_Docker_Captain.assets/image-20210204223753536.png)



Copy command from https://docs.docker.com/machine/install-machine/

![image-20210204223829209](Docker_Mastery_%20with_Kubernetes+Swarm_from_a_Docker_Captain.assets/image-20210204223829209.png)

Copy from the release

![image-20210204224159442](Docker_Mastery_%20with_Kubernetes+Swarm_from_a_Docker_Captain.assets/image-20210204224159442.png)





### 7.1 Download Visual Studio Code.html
### 7.2 Clone This GitHub Repo.html
### 7.3 Download Docker Machine.html

[Install Docker Machine | Docker Documentation](https://docs.docker.com/machine/install-machine/)

### 7.4 Download Docker Compose.html

https://docs.docker.com/compose/install/

### 7.5 Download Docker CE for your Linux distribution.html

https://hub.docker.com/

### 8. Quiz on Proper Docker Install.html



### 9. Code or Text Editor for Docker and Compose files.html

You'll need a text or code editor. Preferably one that can do Syntax Highlighting for Dockerfile and YAML files. Good free ones are GitHub's [Atom](https://atom.io/), Microsoft's [Visual Studio Code](https://code.visualstudio.com/), or even vim if you're into shell-based editors. [I use SpaceVim as my vim distro](https://spacevim.org/), and [VS Code](https://code.visualstudio.com/) as my GUI editor.



### 10. Terminal Shell and Tab Completion for Docker CLI.html

#### Docker Desktop for Windows Terminals

On Windows you'll likely want to use PowerShell terminal (PowerShell.exe) rather than Command Prompt (cmd.exe), but if you don't like the default GUI window that Microsoft provides, you might want to check out [cmder](http://cmder.net/), which can run PowerShell inside a fancy tab-based GUI with lots of features. You can also use Bash shells but you're on your own for setting those up.

#### Windows PowerShell Tab Completion

Tab completion lets you quickly fill the rest of a command or argument as you type by hitting Tab. To get "tab completion" in PowerShell, [try the setup steps for "DockerCompletion" on GitHub](https://github.com/matt9ucci/DockerCompletion).

#### macOS Terminals

On Mac you can use the built in Terminal program which uses the default Bash shell. I prefer to use [iTerm](https://www.iterm2.com/) as my GUI terminal interface to gain more features than the built in one. I also use [oh-my-zsh](https://ohmyz.sh/) rather then Bash, and if you want to see my full setup, check out [bretfisher.com/shell](https://www.bretfisher.com/shell/)

#### macOS Bash Tab Completion

Tab completion lets you quickly fill the rest of a command or argument as you type by hitting Tab. Assuming you're running Docker for Mac, you'll want to connect up the completion scripts that come with Docker for Mac to your shell. [Docker talks about this in their docs](https://docs.docker.com/docker-for-mac/#install-shell-completion). 1. install docker 2. install completion with brew 3. update your .bash_profile 4. symlink your docker completion files 5. restart your terminal.

#### Linux

In a desktop Linux distro like Ubuntu, Mint, etc. you'll likely need to do nothing. They already have good built-in terminals and Bash tab completion works out of the box. Happy days!

#### What You See In This Course

If you like the tools, theme, VIM, etc. as seen in this course on my Mac, I've got a list of tools in my setup at [www.bretfisher.com/shell](http://www.bretfisher.com/shell) that someday I'll turn into a tutorial, but mostly I'm just running their defaults.

### 11. Docker Version Format Change.html

**TL;DR:** Versions are now `YY.MM` based (like Ubuntu) and you can choose *Stable* (slower) or *Edge* (faster) releases. This means that newer features drop faster in Edge releases, and fixes are backported for a longer timeline to Stable releases. Everyone wins.

There may be mentions of `1.12` and `1.13` in this course, which were the two versions before `17.03` . `1.13.1` is actually the same features as `17.03.0` , so if you see `1.13` on my screen recording and `17.04` or similar in your CLI, it's fine!

**In 2017 the** **Docker versioning, release cycle, and product names changed, but features haven't.** [Full details are here](https://blog.docker.com/2017/03/docker-enterprise-edition/), but my commentary on important highlights are below:

- **Docker Engine** (the free one we all know and love) **is now Docker CE** (Community Edition). Notice the drop of the word *Engine*. I suspect we can just call this Docker now. It includes the cli client and backend daemon/service and api (just like it did before). You can get it the same ways as before.

- **Docker Data Center is now Docker EE** (Enterprise Edition) and adds additional [paid products and support](https://store.docker.com/search?offering=enterprise&type=edition) on top of Docker in three pricing tiers.

- These changes don't affect Docker Compose or Docker Machine.

- **Docker's version is now** `**YY.MM**` **based**, using the month of its expected release, and the first one will be `17.03.0` , which is "the first point release" of the `17.03` release. If any bug/security fixes are needed to that release, the first update will be `17.03.1` etc.

- We now have two release tracks (called variants) "Edge" and "Stable". 

  - Edge is released monthly and supported for a month.

  - Stable is released quarterly and support for 4 months.

  - You can extend Stable's support and backported fixes through a [Docker EE subscription](https://store.docker.com/search?offering=enterprise&type=edition).

![img](https://udemy-images.s3.amazonaws.com:443/redactor/2017-04-12_05-32-23-54822ca82152a32910290782857f6271/lifecycle.png)

## 3. Creating and Using Containers Like a Boss
### 1. Check Our Docker Install and Config
### 1.2 S03 Containers Slides.pdf


### 2. Starting a Nginx Web Server
### 3. Debrief What Happens When We Run a Container
### 4. Container VS. VM It's Just a Process
### 4.1 Docker for Windows Command for Getting Into Local Docker VM.html
### 4.2 Mike Coleman (Docker Employee) Docker for the Virtualization Admin eBook.html
### 4.3 Docker Internals cgroups, namespaces, and beyond (YouTube).html
### 4.4 Docker for Mac Commands for Getting Into Local Docker VM.html
### 5. Windows Containers Docker Is No Longer Just Linux.html
### 6. Assignment Manage Multiple Containers
### 7. Assignment Answers Manage Multiple Containers
### 8. Container Quiz 1.html
### 9. What's Going On In Containers CLI Process Monitoring
### 10. Getting a Shell Inside Containers No Need for SSH

### 10.1 Package Management Basics apt, yum, dnf, pkg.html

### 11. Docker Networks Concepts for Private and Public Comms in Containers

### 11.1 Docker's --format option for filtering cli output.html

### 12. FIXME Change In Official Nginx Image Removes Ping.html

### 13. Docker Networks CLI Management of Virtual Networks

### 14. Docker Networks DNS and How Containers Find Each Other

### 14.1 DNS Basics (in a comic, fun!).html

### 14.2 DNS Basics (blog and video).html

### 15. Container Quiz 2.html

### 16. Assignment Using Containers for CLI Testing

### 17. Assignment Answers Using Containers for CLI Testing

### 18. FIXME Bug in alpine affects nslookup.html

### 19. Assignment DNS Round Robin Test

### 19.1 Round-robin DNS, what is it.html

### 20. Assignment Answers DNS Round Robin Test



## 4. Container Images, Where To Find Them and How To Build Them
### 1. What's In An Image (and What Isn't)
### 1.2 S04 Images Slides.pdf
### 1.3 Official Docker Image Specification.html
### 10. Assignment Answers Build Your Own Dockerfile and Run Containers From It
### 11. Using Prune to Keep Your Docker System Clean (YouTube).html
### 2. The Mighty Hub Using Docker Hub Registry Images
### 2.1 List of Official Docker Images.html
### 3. Images and Their Layers Discover the Image Cache
### 3.1 Images and Containers From Docker Docs.html
### 4. Image Tagging and Pushing to Docker Hub
### 5. Building Images The Dockerfile Basics
### 6. Building Images Running Docker Builds
### 7. Building Images Extending Official Images
### 8. Image Quiz.html
### 9. Assignment Build Your Own Dockerfile and Run Containers From It
### 5.1-docker-command.html
## 5. Container Lifetime & Persistent Data Volumes, Volumes, Volumes
### 1. Container Lifetime & Persistent Data
### 1.1 Intro to Immutable Infrastructure Concepts.html
### 1.2 Docker Storage Introduction in Docker Docs.html
### 1.3 The 12-Factor App (Everyone Should Read Key to Cloud Native App Design, Deployment, and Operation).html
### 1.4 S05 Volumes Slides.pdf
### 1.6 12 Fractured Apps (A follow-up to 12-Factor, a great article on how to do 12F correctly in containers).html
### 10. Database Passwords in Containers.html
### 2. Persistent Data Data Volumes
### 3. Shell Differences for Path Expansion.html
### 4. Persistent Data Bind Mounting
### 5. Quiz on Persistent Data.html
### 6. Assignment Database Upgrades with Named Volumes
### 7. Assignment Answers Database Upgrades with Named Volumes
### 8. Assignment Edit Code Running In Containers With Bind Mounts
### 8.1 Jekyll, a Static Site Generator (just as background info, no need to install).html
### 9. Assignment Answers Edit Code Running In Containers With Bind Mounts
## 6. Making It Easier with Docker Compose The Multi-Container Tool
### 1. Docker Compose and The docker-compose.yml File
### 1.1 S06 Compose Slides.pdf
### 1.2 The YAML Format Sample Generic YAML File.html
### 1.4 The YAML Format Quick Reference.html
### 1.5 Docker Compose Release Downloads (good for Linux users that need to download manually).html
### 1.6 S06 Compose Slides.pdf
### 1.7 Compose File Version Differences (Docker Docs).html
### 2. Trying Out Basic Compose Commands
### 2.1 Production Servers Compose vs. Swarm.html
### 2.2 docker-compose download for Linux via GitHub, WinMac already have it..html
### 3. Assignment Build a Compose File For a Multi-Container Service
### 3.1 Compose File Settings (BOOKMARK AND REVIEW). You'll use it often when making compose files..html
### 3.2 Don't use Links! It's a legacy feature of compose, and isn't needed.html
### 4. Assignment Answers Build a Compose File For a Multi-Container Service
### 5. Adding Image Building to Compose Files
### 5.1 (Docker Docs) Compose file build options.html
### 6. Assignment Compose For Run-Time Image Building and Multi-Container Development
### 7. Assignment Answers Compose For Run-Time Image Building and Multi-Container Dev
### 8. Quiz on Docker Compose.html
## 7. Swarm Intro and Creating a 3-Node Swarm Cluster
### 1.1 Docker 1.12 Swarm Mode Deep Dive Part 1 Topology (YouTube).html
### 1.2 Docker 1.12 Swarm Mode Deep Dive Part 2 Orchestration (YouTube).html
### 1.3 Raft Consensus Visualization (Our Swarm DB and how it stays in sync across nodes).html
### 1.4 Heart of the SwarmKit Store, Topology & Object Model (YouTube).html
### 1.5 S07 Swarm Intro Slides.pdf
### 1.7 Heart of the SwarmKit Topology Management (slides).html
### 2. Create Your First Service and Scale It Locally
### 2.1 Deploy services to a swarm (Docker Docs).html
### 3. UI Change For Service CreateUpdate.html
### 4. Docker Machine Bug With Swarm.html
### 5.1 Docker Swarm Firewall Ports.html
### 5.2 Windows Hyper-V driver for docker-machine.html
### 5.3 DigitalOcean $100 credit on new signups.html
### 5.4 Configure SSH for Saving Options for Specific Connections.html
### 5.5 Create and Upload a SSH Key to Digital Ocean.html
### 6. Quiz on Swarm Mode Basics.html
### 1. Swarm Mode Built-In Orchestration
### 5. Creating a 3-Node Swarm Cluster
## 8. Swarm Basic Features and How to Use Them In Your Workflow
### 1. Scaling Out with Overlay Networking
### 1.2 S08 Swarm Basic Features Slides.pdf
### 10. Assignment Create A Stack with Secrets and Deploy
### 11. Assignment Answers Create A Stack with Secrets and Deploy
### 2. Scaling Out with Routing Mesh
### 2.1 Use swarm mode routing mesh (Docker Docs).html
### 3. Quiz on Docker Swarm Basics.html
### 4. Assignment Create A Multi-Service Multi-Node Web App
### 5. Assignment Answers Create A Multi-Service Multi-Node Web App
### 6. Swarm Stacks and Production Grade Compose
### 6.1 Features Not Supported In Stack Deploy.html
### 6.2 Production Servers Compose vs. Swarm.html
### 7. Secrets Storage for Swarm Protecting Your Environment Variables
### 8. Using Secrets in Swarm Services
### 8.1 Manage sensitive data with Docker secrets (Docker Docs) (Lots of good reading and examples).html
### 9. Using Secrets with Swarm Stacks
### 9.1 Secrets In Compose Files (Docker Docs).html
## 9. Swarm App Lifecycle
### 1. Using Secrets With Local Docker Compose
### 1.1 S09 Swarm App Lifecycle Slides.pdf
### 2. Full App Lifecycle Dev, Build and Deploy With a Single Compose Design
### 2.1 Using Compose Files In Production (Docker Docs).html
### 2.2 Using Multiple Compose Files (Docker Docs).html
### 3. Service Updates Changing Things In Flight
### 3.1 Service Update command (Docker Docs).html
### 4. Healthchecks in Dockerfiles
### 4.1 PHP Laravel Good Defaults with Docker.html
### 4.2 Healthcheck in Compose files (Docker Docs).html
### 4.3 HEALTHCHECK in Dockerfile (Docker Docs).html
### 5. Quiz on Swarm App Lifecycle.html
### 6. Info on Swarm Mastery

## 10. Container Registries Image Storage and Distribution

### 1. Docker Hub Digging Deeper

### 1.1 S10 Container Registries Slides.pdf

### 1.2 Docker Hub.html

### 2. Understanding Docker Registry

### 2.1 Registry Garbage Collection.html

### 2.2 Registry Configuration Docs.html

### 2.3 Use Registry As A Mirror of Docker Hub.html

### 3. Run a Private Docker Registry

### 4. Assignment Secure Docker Registry With TLS and Authentication.html

### 5. Using Docker Registry With Swarm

### 6. Third Party Image Registries.html

### 7. Quiz on Container Registries.html

## 11. Docker in Production

### 1. My DockerCon Talk on Docker and Swarm in Production

### 2. The Future of Swarm.html

### 3. Swarm Raft Quorum and Recovery (Laura Frank from DockerCon 2017).html

## 12. The What and Why of Kubernetes

### 1. Kubernetes Intro

### 1.1 S12 Slides The What and Why of Kubernetes.pdf

### 2. What Is Kubernetes

### 2.1 Kubernetes Home Page.html

### 2.2 History of Kubernetes.html

### 3. Why Kubernetes

### 3.1 List of Certified Kubernetes Distributions.html

### 4. Kubernetes vs Swarm

## 13. Kubernetes Install And Your First Pods

### 1. Section Intro

### 1.2 S13 Slides Kubernetes Install and Your First Pods.pdf

### 10.1 Stern for better multi-node log viewing at the CLI.html

### 2. Kubernetes Architecture Terminology

### 2.1 Kubernetes Components.html

### 3. Kubernetes Local Install

### 3.1 Minikube Download.html

### 3.2 Play-with-K8s in a Browser.html

### 3.3 MikroK8s for Linux Hosts.html

### 3.4 Install kubectl on Windows when you don't have Docker Desktop.html

### 3.5 Katacoda Kubernetes in a Browser.html

### 4. Install Tips for minikube and MicroK8s.html

### 5. Kubernetes Container Abstractions

### 5.1 Pod Overview (docs).html

### 5.2 Service (docs).html

### 5.3 Namespace (docs).html

### 6. Kubectl run, create, and apply

### 7. Our First Pod With kubectl run

### 7.1 Kubectl Cheat Sheet.html

### 7.2 Kubectl for Docker Users.html

### 8. 1.18 Changes to Kubectl Run.html

### 9. Scaling ReplicaSets

### 10. Inspecting Kubernetes Objects

## 14. Exposing Kubernetes Ports

### 1. Section Intro

### 1.1 S14 Slides Exposing Kubernetes Ports with Services.pdf

### 2. Service Types

### 2.1 Service Types (docs tutorial).html

### 2.2 Service (docs).html

### 3. Creating a ClusterIP Service

### 3.1 Using Services (docs tutorial).html

### 4. Creating a NodePort and LoadBalancer Service

### 4.1 NodePort (docs).html

### 5. Kubernetes Services DNS

### 5.1 CoreDNS for Kubernetes.html

### 5.2 Kubernetes DNS Specification.html

## 15. Kubernetes Management Techniques

### 1. Section Intro

### 1.2 S15 Slides Kubernetes Management Techniques.pdf

### 2. Run, Expose, and Create Generators

### 2.1 kubectl Usage Conventions (docs).html

### 3. The Future of Kubectl Run

### 3.1 Kubectl Usage Best Practices (docs).html

### 4. Imperative vs. Declarative

### 5. Three Management Approaches

### 5.1 Imperative Config Files (doc tutorials).html

### 5.2 Kubernetes Management Techniques (docs).html

### 5.3 Declarative Config Files.html

### 5.4 Imperative Command Examples (docs tutorial).html

## 16. Moving to Declarative Kubernetes YAML

### 1. Section Intro

### 1.1 S16 Slides Moving to Declarative YAML.pdf

### 2. Kubectl apply

### 2.1 Declarative Management of Kubernetes (Docs).html

### 3. Kubernetes Configuration YAML

### 3.1 Understanding Kubernetes Objects and Spec's (Docs).html

### 4. Building Your YAML Files

### 5. Building Your YAML Spec

### 5.1 Kubernetes API Reference (Docs).html

### 6. Dry Runs and Diff's

### 6.1 APIServer dry-run and kubectl diff.html

### 7. Labels and Label Selectors

### 7.1 Assigning Pods to Nodes (Docs).html

### 7.2 Difference Between Labels and Annotations.html

### 7.3 Taints and Tolerations (Docs).html

### 7.4 Recommended Labels (Docs).html

### 7.5 Label Selectors (Docs).html

## 17. Your Next Steps and The Future of Kubernetes

### 1.1 S17 Slides Your Next Steps and The Future of Kubernetes.pdf

### 2.1 Volumes (Docs).html

### 2.2 StatefulSets (Docs).html

### 2.3 PersistentVolume (Docs).html

### 3. Ingress

### 3.1 Ingress (Docs).html

### 3.2 Traefik Ingress.html

### 3.3 Ingress Controllers (Docs).html

### 3.4 Set up Ingress on Minikube with the NGINX Ingress Controller (Docs).html

### 4. CRD's and The Operator Pattern

### 4.1 OperatorHub.html

### 4.2 The Operator Pattern (Docs).html

### 4.3 Custom Resources (Docs).html

### 4.4 Awesome Operators List.html

### 5.1 Introducing Kustomize.html

### 5.2 Deploying Compose on Kubernetes.html

### 5.3 Kustomize (GitHub).html

### 5.4 Docker App (GitHub).html

### 5.5 CNAB spec.html

### 5.6 Spreadsheet of Kubernetes Deployment Tools.html

### 6. Kubernetes Dashboard

### 6.1 The Kubernetes Dashboard.html

### 7. Namespaces and Context

### 7.1 Configure Access to Multiple Clusters (Docs).html

### 7.2 Namespaces (Docs).html

### 8. Future of Kubernetes

### 8.1 Kubernetes Release Notes.html

### 2. Storage in Kubernetes

### 1. Section Intro

### 5. Higher Deployment Abstractions

## 18. Docker Security Good Defaults and Tools

### 1. Section Intro Top 10 Security Steps for Docker

### 1.1 My list of security objectives for Docker projects.html

### 10. The Security Top 10 Differences for Windows Containers

### 11. What are Distroless Images

### 11.1 GitHub Google's Distroless Repo.html

### 12. Are Swarm and Kubernetes Secrets Really Secure

### 2. Docker Cgroups and Namespaces

### 2.1 Big List of Docker Security Tools.html

### 2.2 Docker Engine Security.html

### 3. Docker Engine's Out-Of-The-Box Security Features

### 3.1 Docs AppArmor security profiles.html

### 3.2 Docs Seccomp security profiles.html

### 4. Docker Bench, The Host Configuration Scanner

### 4.1 CIS Benchmark for Securing Docker.html

### 4.2 Docker Bench.html

### 5. Using USER in Dockerfiles to Avoid Running as Root

### 5.1 Sample Dockerfile of using USER in a Node.js App.html

### 5.2 Docs USER Stanza in Dockerfiles.html

### 6. Docker User Namespaces for Extra Host Security

### 6.1 More Info on User Namespaces.html

### 6.2 Docs How to Use User Namespaces.html

### 7. Code Repo and Image Scanning for CVE's

### 7.1 What Is Shift Left Security.html

### 7.2 CVE Database.html

### 7.3 Aqua MicroScanner, to scan your images during docker build.html

### 7.4 Aqua Trivy, to scan your images after their built.html

### 7.5 Snyk, one of the ways to scan your Git repos and Images.html

### 8. Sysdig Falco, Content Trust,  and Custom Seccomp and AppArmor Profiles

### 8.1 Docs AppArmor profiles.html

### 8.2 Docker Content Trust.html

### 8.3 Sysdig Falco.html

### 8.4 Docs Seccomp security profiles.html

### 9. Docker Rootless Mode

### 9.1 YouTube Video on Rootless Mode from DockerCon 2019.html

### 9.2 Docs Rootless mode.html

### 9.3 Rootless Mode Install Script.html

### 9.4 Docker Blog Experimenting with Rootless Docker.html

## 19. Docker 19.03 Release New Features

### 1. Section Intro.html

### 2. BuildKit and the new Docker buildx CLI

### 4. Docker App and Image Packaging of Compose YAML

### 5. Rootless Mode in Docker Engine

### 6. Docker Desktop Enterprise

### 7. Docker Desktop Enterprise Clusters

### 3. Docker Context and SSH Connections



## 20. DevOps and Docker Clips

### 1. DevOps and Docker Talk Intro

### 1.1 YouTube Live Channel.html

### 1.2 Podcast.html

### 10. Should You Use Docker Compose or Swarm For A Single Server

### 10.1 Only one host for production, should I use docker-compose or Swarm.html

### 11.1 Those Same ENV's overwritten with docker-compose.yml.html

### 11.2 Twelve Factor Apps The Config.html

### 11.3 Simple example of using Docker ENV's to create custom app config.html

### 11.4 3 Docker Compose Features for Improving Team Development Workflow.html

### 11.5 Docker MySQL Official Image Entrypoint Script that creates ENV's from files (for secrets).html

### 11.6 Sample PHP Dockerfile with lots of ENV.html

### 12. Java and JBoss in Containers. One .war File Per Container

### 13. TLS in Dev and Prod with Docker

### 13.1 My Examples of using Traefik with Swarm.html

### 13.2 Using TLS for Localhost.html

### 13.3 Traefik Proxy.html

### 14. Multiple Docker Images From One Git Repo

### 14.1 Docker Build Documentation.html

### 15. Docker + ARM, Using Raspberry Pi or AWS A1 Instances with Docker

### 15.1 Docker and ARM announcement.html

### 15.2 Docker Mastery for Node.js.html

### 15.3 AWS ARM A1 instances.html

### 15.4 QEMU.html

### 16. Docker and Swarm RBAC Options

### 17. ENTRYPOINT vs. CMD, what's the difference in Dockerfiles

### 17.1 ENTRYPOINT vs CMD.html

### 17.2 ENTRYPOINT Best Practices.html

### 17.3 ENTRYPOINT in Dockerfiles.html

### 18. How to Use External Storage in Docker

### 19. Can I Turn a VM into a Container

### 19.1 image2docker demo.html

### 19.2 image2docker for windows container.html

### 19.3 image2docker linux container.html

### 2. Alpine Base Images. Are They Really More Secure

### 2.1 Alpine Linux.html

### 2.2 CVE Database.html

### 20. Startup Order With Multi-Container Apps

### 20.1 The 12 Factor App.html

### 3. Dealing With Non-root Users In Containers and File Permissions

### 4. Apache Web Server Design. Many Sites In One Container, or Many Containers

### 5. Docker Network IP Subnet Conflicts with Outside Networks

### 5.1 Three places to control different docker IP subnet settings.html

### 6. Raspberry Pi Development in Docker

### 6.1 Alex Ellis' Raspberry Pi blog posts.html

### 6.2 QEMU Emulator in Docker Desktop for MacWindows.html

### 7. Windows 10 Containers Get Process Isolation

### 7.1 MobyMoby PR for Process Isolation on Win10.html

### 7.2 Setting up Windows 10 Docker Process Isolation.html

### 8. Should You Move Postgres to Containers

### 8.1 HPE and Docker Whitepaper on MySQL performance.html

### 8.2 Sysbench and Docker Setups to Benchmark Physical, Virtual, and Container-based MySQL.html

### 9. Using Supervisor To Run Multiple Apps In A Container

### 9.1 Docker Docs on Supervisor and Multiple Services In Containers.html

### 9.2 Bret's Example of PHP-FPM plus Nginx Supervisor Config.html

### 11. Docker Environment Configs, Variables, and Entrypoints

## 21. Dockerfile and Compose File Reviews

### 1. Section Intro - My Reviews Of Your Dockerfiles

### 2. Real World PHP Dockerfile Review

### 3. Real World PHP, Apache, and Alpine Dockerfile Review

### 4. Real World PHP and FPM Dockerfile Review

### 5. Real World Elasticsearch Compose Stack File

## 22. Extra's, Common Questions, and Resources

### 1. Node.js Good Defaults For Docker.html

### 2. PHP and Docker Good Defaults Project Template.html

### 3. About the DCA (Docker Certificated Associate).html

### 4. Bonus.html