



## 1. Introduction
### 1. Introduction to Kubernetes Microservices course

https://github.com/DickChesterwood/k8s-fleetman

### 1.2 K8S Command Reference.pdf.pdf

Here's a run down of all (ok, most of) of the commands used in the

Kubernetes Microservices course

**Minikube**

minikube start

starts minikube. If this hangs (wait 15 minutes), then see the video in section 3

that addresses common problems

minikube stop

(Section 3): stops the minikube virtual machine. This may be necessary to do if

you have an error when starting

minikube delete

(Section 3): do this to completely wipe away the minikube image. Useful if

minikube is refusing to start and all else fails. Also you can delete all files in

<home>/.minikube and <home>/.kube

minikube env

(Section 4): find out the required environment variables to connect to

the docker daemon running in minikube.

minikube ip

(Section 4 or 5): find out the ip address of minikube. Needed for

browser access.

**Kubectl**

kubectl get all

(Section 5): list all objects that you’ve created. Pods at first, later,

ReplicaSets, Deployments and Services

kubectl apply –f <yaml file>

(Section 5): either creates or updates resources depending on the

contents of the yaml file

kubectl apply –f .

(Section 7): apply all yaml files found in the current directory

kubectl describe pod <name of pod>

(Section 5): gives full information about the specified pod

kubectl exec –it <pod name> <command>

(Section 5): execute the specified command in the pod’s container.

Doesn’t work well in Cygwin.

kubectl get (pod | po | service | svc | rs | replicaset | deployment |

deploy)

(Section 6): get all pods or services. Later in the course, replicasets and

deployments.

kubectl get po --show-labels

(Section 6): get all pods and their labels

kubectl get po --show-labels -l {name}={value}

(Section 6): get all pods matching the specified name:value pair

kubectl delete po <pod name>

(Section 8): delete the named pod. Can also delete svc, rs, deploy

kubectl delete po --all

(Section 8): delete all pods (also svc, rs, deploy)

**Deployment Management**

kubectl rollout status deploy <name of deployment>

(Section 9): get the status of the named deployment

kubectl rollout history deploy <name of deployment>

(Section 9): get the previous versions of the deployment

kubectl rollout undo deploy <name of deployment>

(Section 9): go back one version in the deployment. Also optionally --

to-revision=<revision number>

We recommend this is used only in stressful emergency situations! Your

YAML will now be out of date with the live deployment!

## 2. Welcome to Kubernetes
### 1. Introducing Kubernetes

https://en.wikipedia.org/wiki/Orchestration_(computing)

In [system administration](https://en.wikipedia.org/wiki/System_administration), **orchestration** is the automated [configuration](https://en.wikipedia.org/wiki/Configuration_management), coordination, and management of computer systems and [software](https://en.wikipedia.org/wiki/Software_deployment).[[1\]](https://en.wikipedia.org/wiki/Orchestration_(computing)#cite_note-Erl-1)



In this video, I just want to say a few words for anybody who has already worked with Docker Swarm.
If that's the case, you're probably aware that Docker Swarm features it's own
built in orchestration system.
You don't have to to anything special to install Swarm and it just comes integrated with Docker Engine.
So it's a very common question as to well,
why would I want to use Kubernetes instead of Docker Swarm?
And well, the answer is really, of course it is entirely up to you, if you're an architect of a project for example, then you can choose between Kubernetes and Docker Swarm.
Now guess the number one advantage of Swarm is it's built in, and I have to admit
that Docker Swarm, I've found, is quite a bit simpler to work with than Kubernetes.
I've previously written a course on Docker, where I've covered Docker Swarm
in about two or three chapters, and we got to quite the production standard
with Swarm in that time.
Whereas with Kubernetes we've got a much bigger course, the learning curve in Kubernetes

### 2. Hands-on Project



## 3. Installing Minikube for local Kubernetes Development
### 1. Setting up Virtualization

http://goo.gl/nLKmA1

https://minikube.sigs.k8s.io/docs/start/

![image-20210206081556214](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206081556214.png)

![image-20210206081612138](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206081612138.png)

![image-20210206081627570](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206081627570.png)

### 2. (Windows 10 Professional Only) Setting up Hyper-V

![image-20210205232937401](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/image-20210205232937401.png)



**if you have Hyper-V enabled then VirtualBox will crash and will crash horribly.**

**You can't use the two things at the same time.**
I would advise you, if you are using Windows 10 Professional
then you may as well enable this option, I think you have to do a reboot after enabling it,but once you've enabled it, be careful not to use Oracle VirtualBox otherwise you will have some horrible blue screens of death.

https://goo.gl/4yEFbF

https://docs.microsoft.com/en-us/archive/blogs/wasimbloch/setting-up-kubernetes-on-windows10-laptop-with-minikube

**Pre-requisites for Development Machine Environment:**
• VT-x/AMD-v virtualization must be enabled in BIOS (requires machine restart)
• Enable Hyper-V – go to Windows features On or Off, you will see dialog box with a list of Windows features as shown below. Navigate to the Hyper-V section and enable it (requires machine restart).
![setup-minikube-1](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/Setup-Minikube-1.png)

**Minikube Installation:**
I prefer to use Hyper-V over VirtualBox to setup Kubernetes on my Windows machine because of its native windows support. In this blog, I am installing docker and then Kubernetes but you can install Kubernetes without Docker. 

**(Optional)** The first step is to download Beta Channel Docker for Windows from [here](https://docs.docker.com/docker-for-windows/). Run Setup default configuration to Install Docker on your machine. Refer [here](https://docs.microsoft.com/en-us/virtualization/windowscontainers/quick-start/quick-start-windows-10) if you need details about how to setup Docker on Windows 10 machine. Once you have successfully installed Docker, confirm deployment by typing “docker info” command in Command window as shown below.
![setup-minikube-4](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/Setup-Minikube-4.png)
Now, we will setup a new external network switch which will be used by our Hyper-V to setup the Kubernetes on local machine as described below.
o Make sure you have Ethernet connectivity while you are setting this.
o Open the Hyper-V manager.
o Select the Virtual Switch Manager on the left-side Actions panel.
![setup-minikube-2](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/Setup-Minikube-2.png)
o Set up a new external network switch to use instead of Docker NAT network switch (for Moby), which is set up by default when you install Docker for Windows.
o For this example, we created a virtual switch called “My Virtual Switch”.
![setup-minikube-3](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/Setup-Minikube-3.png)

I would prefer to create one default Docker machine by using command `docker-machine create --driver hyperv default` ![setup-minikube-4-1](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/Setup-Minikube-4.1.png)

The next step is to download the latest Minikube binary from [here](https://github.com/kubernetes/minikube/releases) and place that in the root folder of C drive. You may think why do you want to place binary in OS drive. This is because there is a bug in the Minikube which does not allow to install the local cluster if it is place anywhere other than C drive or in OS drive. Refer [here](https://github.com/kubernetes/minikube/issues/459) for more details about bug. The file name is minikube-windows-amd64.exe. Rename this exe as “minikube” (just for simplicity).
Download the Kubectl command line utility from [here](http://storage.googleapis.com/kubernetes-release/release/v1.4.0/bin/windows/amd64/kubectl.exe) and copy this alongside the kubectl.exe file from the previous section. We are all set now to launch a local Kubernetes one node cluster. Launch the PowerShell in Administrator mode and navigate to the drive where you have copied kubectl.exe and minikube.exe.
Let’s do standard testing to validate Minikube deployment by finding the version of Minikube and supported Kubernetes version as shown below. Go to **%HOMEPATH%\.minikube** folder and you will notice several folders are created. Have a look!

`PS C:\> .\minikube.exe version`
minikube version: v0.14.0

`PS C:\> .\minikube get-k8s-versions`
The following Kubernetes versions are available:
\- v1.6.0-alpha.0
\- v1.5.2
\- v1.5.1
\- v1.4.5
\- v1.4.3
\- v1.4.2
\- v1.4.1
\- v1.4.0
\- v1.3.7
\- v1.3.6
\- v1.3.5
\- v1.3.4
\- v1.3.3
\- v1.3.0

There are multiple commands that Minikube supports. You can use ‘--help’ option to see the list of commands.

**Start Kubernetes Cluster locally**
We are now ready to launch our Kubernetes cluster locally and we use start command for it. Before we start the cluster, we will check available flags/options via the help options and will use few of them. We want to use **Kubernetes version v1.5.2** and **VM driver is hyperv**. If you would like to add more memory to local Kubernetes cluster, I would recommend using **memory flag**. Make sure you define **hyperv-virtual-switch flag** which should point to the external network switch you have created previously. We are also going to use couple of global flags like **--v=7** and **--alsologtostderr** to see what is going on under the hood.

`PS C:\> .\minikube.exe start --help` Usage: minikube start [flags] Flags: --container-runtime string The container runtime to be used --cpus int Number of CPUs allocated to the minikube VM (default 2) --disk-size string Disk size allocated to the minikube VM (format: [], where unit = b, k, m or g) (default "20g") --docker-env stringArray Environment variables to pass to the Docker daemon. (format: key=value) --extra-config ExtraOption A set of key=value pairs that describe configuration that may be passed to different components. The key should be '.' separated, and the first part before the dot is the component to apply the configuration to. Valid components are: kubelet, apiserver, controller-manager, etcd, proxy, scheduler. --host-only-cidr string The CIDR to be used for the minikube VM (only supported with Virtualbox driver) (default "192.168.99.1/24") --hyperv-virtual-switch string The hyperv virtual switch name. Defaults to first found. (only supported with HyperV driver) --insecure-registry stringSlice Insecure Docker registries to pass to the Docker daemon --iso-url string Location of the minikube iso (default "https://storage.googleapis.com/minikube/minikube-0.7.iso") --kubernetes-version string The kubernetes version that the minikube VM will use (ex: v1.2.3) OR a URI which contains a localkube binary (ex: https://storage.googleapis.com/minikube/k8sReleases/v1.3.0/localkube-linux-amd64) (default "v1.5.1") --kvm-network string The KVM network name. (only supported with KVM driver) (default "default") --memory int Amount of RAM allocated to the minikube VM (default 2048) --network-plugin string The name of the network plugin --registry-mirror stringSlice Registry mirrors to pass to the Docker daemon --vm-driver string VM driver is one of: [virtualbox hyperv] (default "virtualbox")Global Flags:
**--alsologtostderr log to standard error as well as files**
--log_backtrace_at traceLocation when logging hits line file:N, emit a stack trace (default :0)
--log_dir string If non-empty, write log files in this directory (default "")
--logtostderr log to standard error instead of files
--show-libmachine-logs Whether or not to show logs from libmachine.
--stderrthreshold severity logs at or above this threshold go to stderr (default 2)
--test.bench string regular expression per path component to select benchmarks to run
--test.benchmem print memory allocations for benchmarks
--test.benchtime duration approximate run time for each benchmark (default 1s)
--test.blockprofile string write a goroutine blocking profile to the named file after execution
--test.blockprofilerate int if >= 0, calls runtime.SetBlockProfileRate() (default 1)
--test.count n run tests and benchmarks n times (default 1)
--test.coverprofile string write a coverage profile to the named file after execution
--test.cpu string comma-separated list of number of CPUs to use for each test
--test.cpuprofile string write a cpu profile to the named file during execution
--test.memprofile string write a memory profile to the named file after execution
--test.memprofilerate int if >=0, sets runtime.MemProfileRate
--test.outputdir string directory in which to write profiles
--test.parallel int maximum test parallelism (default 4)
--test.run string regular expression to select tests and examples to run
--test.short run smaller test suite to save time
--test.timeout duration if positive, sets an aggregate time limit for all tests (default 0s)
--test.trace string write an execution trace to the named file after execution
--test.v verbose: print additional output
**-v, --v Level log level for V logs**
--vmodule moduleSpec comma-separated list of pattern=N settings for file-filtered logging

Here is the command which we will execute to start the local Kuberenetes cluster.
`.\minikube.exe start --kubernetes-version="v1.5.2" --vm-driver="hyperv" --memory=1024 --hyperv-virtual-switch="My Virtual Switch" --v=7 --alsologtostderr`
On success, you will get the messaging stating **“Kubectl is now configured to use the cluster.”** ![setup-minikube-7](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/Setup-Minikube-7.png)

Let us understand what it is doing behind the scene.
o It generates the certificates and provision local Docker host which creates VM inside the Hyper-V.
o The host is provisioned with the boot2docker.iso and setup it up.
o At the end, it configures the Kubectl to use the local Kubernetes cluster.

You can check the status of the local cluster using status command.

`PS C:\> .\minikube.exe status`
minikubeVM: Running
localkube: Running

Use the kubectl CLI to get the cluster information. In case you see the error like **“.\kubectl : error: couldn't read version from server:”** , then you need to probably set the context again. The command for that is **.\kubectl config set-context minikube**

**PS C:\> .\kubectl cluster-info** Kubernetes master is running at [https://192.168.1.101:8443](https://192.168.1.101:8443/) KubeDNS is running at https://192.168.1.101:8443/api/v1/proxy/namespaces/kube-sy stem/services/kube-dns kubernetes-dashboard is running at https://192.168.1.101:8443/api/v1/proxy/names paces/kube-system/services/kubernetes-dashboard

![setup-minikube-10](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/Setup-Minikube-10.png)

**Conclusion**
Minikube is a work in progress at this moment and it does not support all the features of Kubernetes. Refer [here](https://github.com/kubernetes/minikube) to know what is supported today. Hope this blog post gets you started with Kubernetes on your Windows development machine by using minikube. Please let me know your experience.

If you are interested in Kubernetes in Azure, please see Azure Container Service: [/en-us/azure/container-service/container-service-kubernetes-walkthrough](https://docs.microsoft.com/en-us/azure/container-service/container-service-kubernetes-walkthrough)

**In next post, we’ll look at how to deploy container application in Kubernetes development machine**.

### 3. Installing kubectl and minikube

https://kubernetes.io/docs/tasks/tools/install-kubectl/

![image-20210206005225759](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/image-20210206005225759.png)

Create new folder

![image-20210206005251859](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/image-20210206005251859.png)

![image-20210206004409432](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/image-20210206004409432.png)



![image-20210206004354409](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/image-20210206004354409.png)

Test by run `kubectl`

```java
Admin@LAPTOP-QO8E8EAL MINGW64 /d/git-docs/docker (master)
$ kubectl
kubectl controls the Kubernetes cluster manager.

 Find more information at: https://kubernetes.io/docs/reference/kubectl/overview/

Basic Commands (Beginner):
  create        Create a resource from a file or from stdin.
  expose        Take a replication controller, service, deployment or pod and expose it as a new Kubernetes Service
  run           Run a particular image on the cluster
  set           Set specific features on objects

Basic Commands (Intermediate):
  explain       Documentation of resources
  get           Display one or many resources
  edit          Edit a resource on the server
  delete        Delete resources by filenames, stdin, resources and names, or by resources and label selector

Deploy Commands:
  rollout       Manage the rollout of a resource
  scale         Set a new size for a Deployment, ReplicaSet or Replication Controller
  autoscale     Auto-scale a Deployment, ReplicaSet, or ReplicationController

Cluster Management Commands:
  certificate   Modify certificate resources.
  cluster-info  Display cluster info
  top           Display Resource (CPU/Memory/Storage) usage.
  cordon        Mark node as unschedulable
  uncordon      Mark node as schedulable
  drain         Drain node in preparation for maintenance
  taint         Update the taints on one or more nodes
```

https://www.cygwin.com/

**Cygwin là một môi trường giả lập hệ điều hành Linux chạy trên Windows, giúp người sử dụng Windows có thể làm việc y như trên Linux mà không cần phải cài đặt hệ điều hành này vào máy tính**

Go to 

https://github.com/kubernetes/minikube/releases

Windows download minikube-windows-amd64.exe

Rename to minikube.exe

> No need to download minikube-installer.exe because it can be complicated

![image-20210206011925126](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/image-20210206011925126.png)

Run `minikube`

In the win 10 pro you have to run

![image-20210206012052468](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/image-20210206012052468.png)



Run `kubectl version`

![image-20210206012507276](kubernetes-hands-on---deploy-microservices-to-the-aws-cloud.assets/image-20210206012507276.png)

Now you can see client and server version => ok

### 4. Troubleshooting Minikube

https://github.com/kubernetes/minikube/issues/2765

NOTE

- If we use normal terminal, you can go to `C:\Users\Admin`and delete folder `.kube`and `minikube`

- With cygwin yo navigate to `C:\cygwin64\home\Admin`and delete

  ![image-20210206081430587](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206081430587.png)


## 4. (optional) Docker Quickstart
### 1. Docker Overview

![image-20210206083130041](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206083130041.png)

I'm just using a caption here
from my previous Docker course.

If you're on Windows 10 Professional, then you will download Docker for windows,
Docker Community Edition for Windows, using the link here, but if you're on a previous version, and I am,
I'm on Windows 10 Home Edition, then you need to follow the link to Docker Toolbox.
For Macintosh, it's a similar story.

If you're on Mac on Yosemite 10.10.3 or above,
then you will get the Docker for Mac,
which uses a native virtual machine environment.
If you're on an older version,
then you're going to be getting Docker Toolbox.

### 2. Docker Containers vs Images

Now, once you have gone through the installation process,
the difference now should be, when you type the docker command--
I'm going to do a video edit here because it's taking a long time for me.
It's clearly hanging.
I did eventually get a response, but it did take a very long time to respond.

![image-20210206084232125](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206084232125.png)

The reason for that long pause is, Docker was trying to connect to the Docker server.
The idea is that, on your local computer, you have a daemon process running in the background
that is doing all of the Docker work, and you need to have that running
in order to do any work with Docker.
Let me show you one of the most common Docker commands, which is docker image ls.
That's saying, "Give me a list of all of the images "that I have downloaded to this computer."
I think you'll find, if you run that command, there will be a long pause, it's trying to connect
to your Docker server.
Yeah, it was well over a minute for me before I got this error during connect.
Can you see that it's clearly trying to connect to some kind of IP address somewhere?
I think it's worth explaining what's going on here on a caption.
What's happening here is that the Docker command line,
this is where you were entering that docker command,
is trying to connect to Docker itself, which, typically, you run as a separate daemon process.
If you're not running on Linux, and I assume most of you probably aren't running on Linux,
there's a problem here because, just as with Kubernetes, this Docker daemon
needs to run on Linux because it's using various features
of the Linux operating system to support containers.
A little digression is that Microsoft are currently
working really hard to build their own support
for Docker containers built into Windows, but at the time of recording,
that's a kind of experimental feature that isn't in common use.

![image-20210206084421791](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206084421791.png)

What will happen is, and this is a very similar story
to what's been happening in Kubernetes,
assuming you're not running on Linux, the setup is going to be,
the Docker command line is actually going to look for a virtual machine, which, by default,
is that Oracle VirtualBox that you saw earlier.
It's going to look for a Docker daemon running in this virtual machine.
What you can do with a Docker tooling that you've just installed
is start up this virtual machine, and start up a new Docker daemon.

![image-20210206084503802](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206084503802.png)

That's absolutely fine, but because you're on a Kubernetes course,
I have a plan.
Of course, in the previous section, you went through all of that pain
of installing Minikube, which is, as you know, a cut-down version of Kubernetes.
What I haven't told you is that, inside Minikube is an installation of Docker.
It has a Docker daemon running just fine.
What we can do, and this is just a little bit of a trick that I often use,
if we're already running Minikube, then we might as well tell the Docker command line
to use Minikube's version of Docker to do our work.
It's a neat little trick.
Let's switch across to the terminal, and I'll show you how it works.
I hope you managed to instal Minikube in the previous section.
I don't know if it's running for you at the moment.
If you're not currently running Minikube, then let's get it started with minikube start.
If you're running on Windows 10 Professional, then you will need those extra command line arguments.
Jet back to the previous section for details on that.
As always, this takes quite a long time to start, so let's do a video edit here.
Great, we should have Minikube up and running now.
Now, remember, there is a Docker environment inside that Minikube.
Now, at present, just to remind you, if we do a docker image ls, you're probably still going to see an error.
That's because we need to configure Docker
to tell it that we are talking to the Minikube environment rather than the traditional Docker
that we run in its own virtual machine.

![image-20210206084838587](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206084838587.png)

```java
Admin@LAPTOP-QO8E8EAL ~
$ minikube docker-env
* The control plane node must be running for this command
  - To start a cluster, run: "minikube start"

Admin@LAPTOP-QO8E8EAL ~
$ minikube start
* minikube v1.17.1 on Microsoft Windows 10 Pro 10.0.18363 Build 18363
* Using the docker driver based on existing profile
* Starting control plane node minikube in cluster minikube
* Restarting existing docker container for "minikube" ...
* Preparing Kubernetes v1.20.2 on Docker 20.10.2 ...
* Verifying Kubernetes components...
* Enabled addons: storage-provisioner, default-storageclass
* Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default

Admin@LAPTOP-QO8E8EAL ~
$ docker image ls
REPOSITORY                           TAG                                                     IMAGE ID       CREATED         SIZE
gcr.io/k8s-minikube/kicbase          v0.0.17                                                 a9b1f16d8ece   2 weeks ago     985MB
docker/desktop-kubernetes            kubernetes-v1.19.3-cni-v0.8.5-critools-v1.17.0-debian   bb2106081d17   2 months ago    285MB
httpd                                latest                                                  0a30f4c29d25   2 months ago    138MB
k8s.gcr.io/kube-proxy                v1.19.3                                                 cdef7632a242   3 months ago    118MB
k8s.gcr.io/kube-scheduler            v1.19.3                                                 aaefbfa906bd   3 months ago    45.7MB
k8s.gcr.io/kube-apiserver            v1.19.3                                                 a301be0cd44b   3 months ago    119MB
k8s.gcr.io/kube-controller-manager   v1.19.3                                                 9b60aca1d818   3 months ago    111MB
ubuntu                               14.04                                                   df043b4f0cf1   4 months ago    197MB
k8s.gcr.io/etcd                      3.4.13-0                                                0369cf4303ff   5 months ago    253MB
k8s.gcr.io/coredns                   1.7.0                                                   bfe3a36ebd25   7 months ago    45.2MB
docker/desktop-storage-provisioner   v1.1                                                    e704287ce753   10 months ago   41.8MB
docker/desktop-vpnkit-controller     v1.0                                                    79da37e5a3aa   11 months ago   36.6MB
k8s.gcr.io/pause                     3.2         

Admin@LAPTOP-QO8E8EAL ~
$ minikube docker-env
export DOCKER_TLS_VERIFY="1"
export DOCKER_HOST="tcp://127.0.0.1:49155"
export DOCKER_CERT_PATH="C:\cygwin64\home\Admin\.minikube\certs"
export MINIKUBE_ACTIVE_DOCKERD="minikube"

# To point your shell to minikube's docker-daemon, run:
# eval $(minikube -p minikube docker-env)


```

Now, what we can do here is, we can use the command minikube followed by docker-env,
and that's going to tell you what environment variables you need to set up
in order for your Docker command line to talk to the Docker inside Minikube.
If you're on Mac, if you're on Linux, or if you're on Windows using Cygwin, then you could copy and paste these export commands, or even better, you can just copy this eval here.
All that's going to do is, it's going to run that minikube docker-env,
and take this output, and then execute the output.
It's going to run these four exports. Let's try that.
I'll copy and paste.

```java
eval $(minikube -p minikube docker-env)
```

![image-20210206085052314](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206085052314.png)

All that has done is, if I do a echo $DOCKER_HOST, for example, you can see that the value here
is matching the value here.
Just in case you're working in the standard Windows command prompt,
which, to be honest, I don't recommend, you would be better on something like Cygwin,
but if you have decided to use the standard Windows command shell,
you might be worried that all of that Unix-y stuff that we've just seen won't work for you.
Well, I've just switched my command prompt for a demonstration.
I must admit, I've never tried this.
I was surprised to see the results.
You can see that they've actually thought of that, and if you are running on the command prompt,
then it will issue standard DOS command prompts, I suppose they are.
These will be set commands.

![image-20210206085143760](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206085143760.png)

You can see, there's a final REM statement here, which suggests that we can just copy this here,
and if we run that, we'll get exactly the same results as we just did over in Cygwin.
Just to remind you, don't mix and match.
Don't use Windows command shell sometimes, and Cygwin some other times.
Choose one or the other.
Otherwise, things get in a terrible mess.
I just wanted to do that to show you that, if you are on the Windows command prompt,
you're not left out.

![image-20210206085240101](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206085240101.png)

We've now set up these environment variables, and the big thing now is,
you should be able to type the command docker image ls, and what we're seeing here is a list
of all of the Docker images that are contained inside the Minikube virtual machine.
Now, these images are nothing to do with us.
We never downloaded them.
In fact, they're the Docker images
that Minikube requires to set up a Kubernetes environment.
We will be looking at some of these images a bit later on in the course, but for now, just think of them
as internal images that Minikube needs.
That's a little trick you can do.
We're effectively reusing the Docker process inside Minikube.
Now, the beauty of reusing the Docker process
that's inside Minikube rather than starting up
the Docker daemon again is just that it's more efficient on your computer's resources.
I often work on a laptop, which isn't very powerful.
There isn't a lot of RAM in there, and if I'm running Minikube
and I'm running Docker Toolbox at the same time, then that's two virtual machines
that my laptop has to manage, and it really does start to struggle.
This is a nice trick that I use quite often.

### 3. Running Containers from DockerHub
## 5. Kubernetes Pods
### 1. Pods Overview

*Pods* are the smallest deployable units of computing that you can create and manage in Kubernetes.

A *Pod* (as in a pod of whales or pea pod) is a group of one or more [containers](https://kubernetes.io/docs/concepts/containers/), with shared storage and network resources, and a specification for how to run the containers. A Pod's contents are always co-located and co-scheduled, and run in a shared context. A Pod models an application-specific "logical host": it contains one or more application containers which are relatively tightly coupled. In non-cloud contexts, applications executed on the same physical or virtual machine are analogous to cloud applications executed on the same logical host.

https://kubernetes.io/docs/concepts/workloads/pods/

And to put this simply, for every container that we are planning to deploy,
we're going to create a Pod in Kubernetes, and you can think of each of these Pods
as just being a wrapper for a container so every one of these Microservices,
is going to become a Pod in it's own right.
For most situations you're going to find
that a Pod and a container are in a one to one relationship.
So you might be wondering why have Kubernetes gone to the bother,
of creating some extra jargon here. 
Well there's two things to say about that, it is perfectly possible to have more than
one container inside a Pod, as I'm trying to illustrate here.

![image-20210206085945079](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206085945079.png)

![image-20210206090009184](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210206090009184.png)



what Kubernetes is going to do with these Pods,
is it's going to manage those Pods,
and by that I mean it's going to do things like
making sure they're running all the time,
Kubernetes will make sure that a Pod
isn't using too much disc, or CPU, and so on
isn't using too much disc, or CPU, and so on
so a Pod in Kubernetes is just
the most basic unit of deployment.

#### How Pods manage multiple containers

Pods are designed to support multiple cooperating processes (as containers) that form a cohesive unit of service. The containers in a Pod are automatically co-located and co-scheduled on the same physical or virtual machine in the cluster. The containers can share resources and dependencies, communicate with one another, and coordinate when and how they are terminated.

### 2. Writing a Pod

https://hub.docker.com/u/richardchesterwood

https://hub.docker.com/r/richardchesterwood/k8s-fleetman-webapp-angular

https://github.com/DickChesterwood/k8s-fleetman

Refer:

[Pod | Kubernetes](https://kubernetes.io/docs/reference/kubernetes-api/workloads-resources/pod-v1/)

![image-20210208211308920](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210208211308920.png)

Hello world



D:\git-docs\docker\Source\Udemy - Kubernetes Hands-On - Deploy Microservices to the AWS Cloud\1. Introduction\Chapter 5 Pods\first-pod.yaml

```ini
apiVersion: v1
kind: Pod
metadata:
  name: webapp
spec:
  containers:
  - name: webapp
    image: richardchesterwood/k8s-fleetman-webapp-angular:release0
```



### 3. Running a Pod

Now this command is going to show us everything
that we have defined in our Kubernetes cluster.
It's going to show us all about pods, and everything else
that we create throughout the rest of the course.

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d
$ cd devops-practices/k8s/

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s
$ ls
'1.1 Course files v3.zip.zip'  'Chapter 11 Microservices'  'Chapter 13 AWS'  'Chapter 16 Helm and Monitoring'  'Chapter 5 Pods'      'Chapter 7 Exercise'     'Chapter 9 Deployments'
'Chapter 10 Networking'        'Chapter 12 Persistence'    'Chapter 15 ELK'  'Chapter 17 Alerts'               'Chapter 6 Services'  'Chapter 8 ReplicaSets'

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s
$ cd Chapter\ 5\ Pods/

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ ls
first-pod.yaml

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ minikube status
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
timeToStop: Nonexistent


Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ kubectl get all
NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   2d19h

```

We use `minikube status` to check status for minikube



Now we haven't created anything yet but you'll notice
there is one entry in this list, and it's called the `service/kubernetes`.
What we're seeing here actually is a rest service that is exposed by our Kubernetes cluster.
And what's happening every time we enter one of these kubectl commands, is kubectl is automatically posting commands to this rest api end point.
So, do you need to know that?
No, not really.
Kubectl will do the job for us but I just wanted you to know
why we're seeing something appearing in that list already.
We need to tell Kubernetes that we want it to deploy a pod to the cluster. And we do that with the command `kubectl apply`, followed by -f. for final name, and then the name of the file that you just created.

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ kubectl get all
NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   2d19h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ kubectl apply -f first-pod.yaml
pod/webapp created

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ kubectl get all
NAME         READY   STATUS              RESTARTS   AGE
pod/webapp   0/1     ContainerCreating   0          16s

NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   2d20h

```

Now we know it's a web application pod so we'll probably guess that it's exposing ports 80.
While I would love to do that, it turns out that pods are not visible outside the Kubernetes cluster.
Let's have a demo of that.
Firstly, in order to visit our Kubernetes cluster in a web browser, we need to know the IP address
of the minikube cluster itself.

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ minikube ip
192.168.49.2

```

Check status

![image-20210208213138882](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210208213138882.png)



In fact, we can tell, we'd be able to tell that by looking inside the Docker file that was used
to create this container.
So we know that's running on port 80, and we know from the demo we've just attempted to connect from a browser, to the cluster, on that port.

> there's a big wall between the browser and the Kubernetes cluster.
> And it's just simply the case, that we're missing a concept.
> Pods are not intended to be visible from outside of the cluster.

![image-20210208213531332](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210208213531332.png)

Run

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ minikube ip
192.168.49.2

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ kubectl describe pod webapp
Name:         webapp
Namespace:    default
Priority:     0
Node:         minikube/192.168.49.2
Start Time:   Mon, 08 Feb 2021 21:27:01 +0700
Labels:       <none>
Annotations:  <none>
Status:       Running
IP:           172.17.0.3
IPs:
  IP:  172.17.0.3
Containers:
  webapp:
    Container ID:   docker://21838957015bee2d0aa588e23981f402a49b44e763cd14a316a5965e7a80e1bb
    Image:          richardchesterwood/k8s-fleetman-webapp-angular:release0
    Image ID:       docker-pullable://richardchesterwood/k8s-fleetman-webapp-angular@sha256:9b98fec20772bd1d7d4c9085048f28af35b31ad3a7b7d3ba395fb512c5c359e6
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Mon, 08 Feb 2021 21:27:58 +0700
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-j9srd (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             True
  ContainersReady   True
  PodScheduled      True
Volumes:
  default-token-j9srd:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  default-token-j9srd
    Optional:    false
QoS Class:       BestEffort
Node-Selectors:  <none>
Tolerations:     node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                 node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  10m   default-scheduler  Successfully assigned default/webapp to minikube
  Normal  Pulling    10m   kubelet            Pulling image "richardchesterwood/k8s-fleetman-webapp-angular:release0"
  Normal  Pulled     9m9s  kubelet            Successfully pulled image "richardchesterwood/k8s-fleetman-webapp-angular:release0" in 56.2370259s
  Normal  Created    9m9s  kubelet            Created container webapp
  Normal  Started    9m9s  kubelet            Started container webapp

```

And that's telling us exactly what happened when they container was starting up, or I should say really,
when the pod was starting up.



Well I'm really running out of things to show you with pods.
Pods are so basic that there's really very little that you
can do with them directly.
As we've seen, we can't visit that pod via a browser.
But I supposed there is on last thing we can do with a pod,
and that is, we can just as you can in Docker,
we can connect to the pod,
and we can execute a command against the pod.
Now, this is something you'll need to do
quite frequently when you're first setting up a cluster
and you may be debugging a pod,
and just trying to get it stable.

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ kubectl exec webapp ls
kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
bin
dev
etc
home
lib
media
mnt
proc
root
run
sbin
srv
sys
tmp
usr
var

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ kubectl exec webapp -- ls
bin
dev
etc
home
lib
media
mnt
proc
root
run
sbin
srv
sys
tmp
usr
var

```

Run `kubectl exec <pod name> -- <command>`

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ kubectl -it exec webapp sh
kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
/ # exit

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods
$ kubectl -it exec webapp -- sh
/ # ls
bin    dev    etc    home   lib    media  mnt    proc   root   run    sbin   srv    sys    tmp    usr    var
/ # wget http://localhost:80
Connecting to localhost:80 (127.0.0.1:80)
index.html           100% |*********************************************************************************************************************************************|   585   0:00:00 ETA
/ # cat index.html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Fleet Management</title>
  <base href="/">

  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.png">
</head>
<body>
  <app-root></app-root>
<script type="text/javascript" src="runtime.js"></script><script type="text/javascript" src="polyfills.js"></script><script type="text/javascript" src="styles.js"></script><script type="text
/javascript" src="vendor.js"></script><script type="text/javascript" src="main.js"></script></body>
</html>
/ # exit

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 5 Pods

```

=> prove it works



## 6. Services in Kubernetes
### 1. Services

that's because Pods are not visible outside the cluster and it's by design because you're going to discover when we go a little further on the course that Pods are designed to be very throw away things.
Pods have short lifetimes. Pods regularly die.
Pods are regularly recreated and as the old saying goes,
as I mentioned in the introduction section, we treat Pods like cattle.
We don't treat them like pets.
So because Pods have this, as they say, ephemeral lifecycle, and that just means **short-lived**,
Kubernetes has a further concept called a service and the idea is that a service is a **long-running** object in Kubernetes.
A **service** will have an IP address and a service will have a stable, fixed port.
And what we can do is we can attach services to Pods.
I'll show you how that works in a very short while.

![image-20210208221141650](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210208221141650.png)

> With a service we can connect to the Kubernetes Cluster
> and the service will find a suitable Pod to service that request.

![image-20210208221253756](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210208221253756.png)



**Pod Label**
What we can do with a Pod is we can set up a series of key value pairs.
You can have one or more of these key value pairs so for example we might give a Pod a label
whose name is app and the value is webapp.
Now this can be anything you like.
I've only used this because all of the reference documentation uses, as its first example really,
the key value pair of app followed by some value.

[Service | Kubernetes](https://kubernetes.io/docs/reference/kubernetes-api/services-resources/service-v1/)

![image-20210208221726500](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210208221726500.png)









### 2. NodePort and ClusterIP

D:\git-docs\docker\Source\Udemy - Kubernetes Hands-On - Deploy Microservices to the AWS Cloud\1. Introduction\Chapter 6 Services\first-pod.yaml

```ini
apiVersion: v1
kind: Pod
metadata:
  name: webapp
  labels:
    app: webapp
    release: "0"
spec:
  containers:
  - name: webapp
    image: richardchesterwood/k8s-fleetman-webapp-angular:release0

---
apiVersion: v1
kind: Pod
metadata:
  name: webapp-release-0-5
  labels:
    app: webapp
    release: "0-5"
spec:
  containers:
  - name: webapp
    image: richardchesterwood/k8s-fleetman-webapp-angular:release0-5

```

D:\git-docs\docker\Source\Udemy - Kubernetes Hands-On - Deploy Microservices to the AWS Cloud\1. Introduction\Chapter 6 Services\webapp-service.yaml

```ini
apiVersion: v1
kind: Service
metadata:
  name: fleetman-webapp

spec:
  # This defines which pods are going to be represented by this Service
  # The service becomes a network endpoint for either other services
  # or maybe external users to connect to (eg browser)
  selector:
    app: webapp
    release: "0-5"

  ports:
    - name: http
      port: 80
      nodePort: 30080

  type: NodePort

```

https://kubernetes.io/docs/reference/kubernetes-api/services-resources/service-v1/

**type** (string) 

type determines how the Service is exposed. Defaults to ClusterIP. Valid options are ExternalName, ClusterIP, NodePort, and LoadBalancer. "ClusterIP" allocates a cluster-internal IP address for load-balancing to endpoints. Endpoints are determined by the selector or if that is not specified, by manual construction of an Endpoints object or EndpointSlice objects. If clusterIP is "None", no virtual IP is allocated and the endpoints are published as a set of endpoints rather than a virtual IP. "NodePort" builds on ClusterIP and allocates a port on every node which routes to the same endpoints as the clusterIP. "LoadBalancer" builds on NodePort and creates an external load-balancer (if supported in the current cloud) which routes to the same endpoints as the clusterIP. "ExternalName" aliases this service to the specified externalName. Several other fields do not apply to ExternalName services. More info: https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types

---

The first option is **ClusterIP**. 
If you make your service be of type ClusterIP then you're telling Kubernetes that this
service will only be accessible from inside the Cluster.
**It will not be accessible to external things such as web browsers**, so you're going to use ClusterIP
if this service is just going to be an internal service such as our micro services that we're building.
Many of the micro services that we're building, we will not want to expose to external traffic.
We just want other micro services inside the Cluster to talk to it.
In that case, ClusterIP would be the right choice,
It makes it a kind of private service.
That's just my terminology but that's the way I think of it.
It will give this service an IP address and that IP address will be stable because
services are long lived entities in Kubernetes.
Remember, pods come and go.
Pods will constantly die, pods are going to be restarted.
And that's the point of having this service, to act as a fronts to the pods
so we can have stable IP addresses.
Actually **ClusterIP is probably going to be what we use for most of our services**
**when we start introducing the micro services, but of course, that's not the right choice for the web app.**
We want the web app, of course, to be exposed to the outside world.
So for that reason, the type we're going to need is the final choice available and that type is called a **NodePort**. That this is where we are going to expose a port through the node, the node in our case is the entire Kubernetes Cluster, of course, when we go further with this we are going to have multiple nodes in a Cluster but this means we're going to expose a port through the node.

![image-20210208223041218](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210208223041218.png)

> Port > 30000

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl get all
NAME         READY   STATUS    RESTARTS   AGE
pod/webapp   1/1     Running   0          67m

NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   2d21h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl apply -f webapp-service.yaml
service/fleetman-webapp created

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl get all
NAME         READY   STATUS    RESTARTS   AGE
pod/webapp   1/1     Running   0          68m

NAME                      TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
service/fleetman-webapp   NodePort    10.109.124.196   <none>        80:30080/TCP   2s
service/kubernetes        ClusterIP   10.96.0.1        <none>        443/TCP        2d21h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ ls
first-pod.yaml  webapp-service.yaml

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ minikube ip
192.168.49.2

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services

```



Go to http://192.168.49.2:30080/ => not works





### 3. Pod Selection with Labels

Add label in first-pod.yaml

```ini
metadata:
  name: webapp
  labels:
    app: webapp # we can use any name instead of app and it should be the same with service selector
    release: "0"
```

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl get all
NAME         READY   STATUS    RESTARTS   AGE
pod/webapp   1/1     Running   0          67m

NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   2d21h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl apply -f webapp-service.yaml
service/fleetman-webapp created

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl get all
NAME         READY   STATUS    RESTARTS   AGE
pod/webapp   1/1     Running   0          68m

NAME                      TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
service/fleetman-webapp   NodePort    10.109.124.196   <none>        80:30080/TCP   2s
service/kubernetes        ClusterIP   10.96.0.1        <none>        443/TCP        2d21h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ ls
first-pod.yaml  webapp-service.yaml

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ minikube ip
192.168.49.2

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl apply -f first-pod.yaml
pod/webapp configured
pod/webapp-release-0-5 created


Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl get all
NAME                     READY   STATUS    RESTARTS   AGE
pod/webapp               1/1     Running   0          76m
pod/webapp-release-0-5   1/1     Running   0          66s

NAME                      TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
service/fleetman-webapp   NodePort    10.109.124.196   <none>        80:30080/TCP   7m45s
service/kubernetes        ClusterIP   10.96.0.1        <none>        443/TCP        2d21h

```

![image-20210208224929821](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210208224929821.png)

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ minikube ip
192.168.49.2

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl apply -f first-pod.yaml
pod/webapp unchanged
pod/webapp-release-0-5 unchanged

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl apply -f webapp-service.yaml
service/fleetman-webapp unchanged

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl get all
NAME                     READY   STATUS    RESTARTS   AGE
pod/webapp               1/1     Running   0          80m
pod/webapp-release-0-5   1/1     Running   0          5m19s

NAME                      TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
service/fleetman-webapp   NodePort    10.109.124.196   <none>        80:30080/TCP   11m
service/kubernetes        ClusterIP   10.96.0.1        <none>        443/TCP        2d21h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ curl http://192.168.49.2:30080
curl: (7) Failed to connect to 192.168.49.2 port 30080: Timed out

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl describe svc fleetman-webapp
Name:                     fleetman-webapp
Namespace:                default
Labels:                   <none>
Annotations:              <none>
Selector:                 app=webapp,release=0-5
Type:                     NodePort
IP:                       10.109.124.196
Port:                     http  80/TCP
TargetPort:               80/TCP
NodePort:                 http  30080/TCP
Endpoints:                172.17.0.4:80
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services

```

Show pods

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl get pods
NAME                 READY   STATUS    RESTARTS   AGE
webapp               1/1     Running   0          88m
webapp-release-0-5   1/1     Running   0          12m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl get po
NAME                 READY   STATUS    RESTARTS   AGE
webapp               1/1     Running   0          88m
webapp-release-0-5   1/1     Running   0          13m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl get po --show-labels
NAME                 READY   STATUS    RESTARTS   AGE   LABELS
webapp               1/1     Running   0          88m   app=webapp,release=0
webapp-release-0-5   1/1     Running   0          13m   app=webapp,release=0-5

# Filter by release
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl get po --show-labels -l release=0
NAME     READY   STATUS    RESTARTS   AGE   LABELS
webapp   1/1     Running   0          90m   app=webapp,release=0

```

https://minikube.sigs.k8s.io/docs/handbook/accessing/

I**ncreasing the NodePort range**
By default, minikube only exposes ports 30000-32767. If this does not work for you, you can adjust the range by using:



```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ kubectl get all
NAME                     READY   STATUS    RESTARTS   AGE
pod/webapp               1/1     Running   0          100m
pod/webapp-release-0-5   1/1     Running   0          25m

NAME                      TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
service/fleetman-webapp   NodePort    10.109.124.196   <none>        80:30180/TCP   31m
service/kubernetes        ClusterIP   10.96.0.1        <none>        443/TCP        2d21h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ minikube ip
192.168.49.2

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ minikube service fleetman-webapp
|-----------|-----------------|-------------|---------------------------|
| NAMESPACE |      NAME       | TARGET PORT |            URL            |
|-----------|-----------------|-------------|---------------------------|
| default   | fleetman-webapp | http/80     | http://192.168.49.2:30180 |
|-----------|-----------------|-------------|---------------------------|
* Starting tunnel for service fleetman-webapp.
|-----------|-----------------|-------------|------------------------|
| NAMESPACE |      NAME       | TARGET PORT |          URL           |
|-----------|-----------------|-------------|------------------------|
| default   | fleetman-webapp |             | http://127.0.0.1:63961 |
|-----------|-----------------|-------------|------------------------|
* Opening service default/fleetman-webapp in default browser...
! Because you are using a Docker driver on windows, the terminal needs to be open to run it.

```

![image-20210208231048748](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210208231048748.png)



Minikube doesn't support LoadBalancer services, so the service will never get an external IP.

But you can access the service anyway with its external port.

You can get the IP and PORT by running:

```yaml
minikube service <service_name>
```

https://stackoverflow.com/questions/39850819/kubernetes-minikube-external-ip-does-not-work



https://kubernetes.io/docs/tutorials/hello-minikube/#create-a-service



---



https://stackoverflow.com/questions/63600378/cant-access-minikube-service-using-nodeport-from-host-on-mac

You are mostly facing [this issue](https://github.com/kubernetes/minikube/issues/7344) when you use `minikube ip` which returns `127.0.0.1`. It should work if you use internal ip from `kubectl get node -o wide` instead of `127.0.0.1`.

A much easier approach from the official reference [docs](https://kubernetes.io/docs/tutorials/hello-minikube/) is you can get the url using `minikube service web-test --url` and use it in browser or if you use `minikube service web-test` it will open the url in browser directly

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 6 Services
$ minikube service fleetman-webapp --url
* Starting tunnel for service fleetman-webapp.
|-----------|-----------------|-------------|------------------------|
| NAMESPACE |      NAME       | TARGET PORT |          URL           |
|-----------|-----------------|-------------|------------------------|
| default   | fleetman-webapp |             | http://127.0.0.1:57237 |
|-----------|-----------------|-------------|------------------------|
http://127.0.0.1:57237
! Because you are using a Docker driver on windows, the terminal needs to be open to run it.

```



## 7. Exercise Deploy ActiveMQ as a Pod and Service to Kubernetes
### 1. Exercise Deploy ActiveMQ as a Pod and Service

![image-20210208234345926](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210208234345926.png)

D:\git-docs\docker\Source\Udemy - Kubernetes Hands-On - Deploy Microservices to the AWS Cloud\1. Introduction\Chapter 7 Exercise\pods.yaml

```ini
---
# add

apiVersion: v1
kind: Pod
metadata:
  name: queue
  labels:
    app: queue
spec:
  containers:
  - name: queue
    image: richardchesterwood/k8s-fleetman-queue:release1
```



D:\git-docs\docker\Source\Udemy - Kubernetes Hands-On - Deploy Microservices to the AWS Cloud\1. Introduction\Chapter 7 Exercise\services.yaml

```ini
---
apiVersion: v1
kind: Service
metadata:
  name: fleetman-queue

spec:
  # This defines which pods are going to be represented by this Service
  # The service becomes a network endpoint for either other services
  # or maybe external users to connect to (eg browser)
  selector:
    app: queue

  ports:
    - name: http
      port: 8161
      nodePort: 30010

  type: NodePort
```

Run `kubectl apply -f .` to apply all

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ kubectl apply -f .
pod/webapp-release-0-5 unchanged
pod/webapp-release-0 created
pod/queue created
service/fleetman-webapp unchanged
service/fleetman-queue created

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ kubectl get all
NAME                     READY   STATUS              RESTARTS   AGE
pod/queue                0/1     ContainerCreating   0          5s
pod/webapp               1/1     Running             0          15m
pod/webapp-release-0     1/1     Running             0          5s
pod/webapp-release-0-5   1/1     Running             0          15m

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   5s
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     15m
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          16m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ kubectl describe pod queue
Name:         queue
Namespace:    default
Priority:     0
Node:         minikube/192.168.49.2
Start Time:   Mon, 08 Feb 2021 23:50:10 +0700
Labels:       app=queue
Annotations:  <none>
Status:       Running
IP:           172.17.0.6
IPs:
  IP:  172.17.0.6
Containers:
  queue:
    Container ID:   docker://d82ab5b505b036ae72bfb6dbc198048e5b710967ef991b52fa124f5d0c9080f8
    Image:          richardchesterwood/k8s-fleetman-queue:release1
    Image ID:       docker-pullable://richardchesterwood/k8s-fleetman-queue@sha256:bc2cb90a09aecdd8bce5d5f3a8dac17281ec7883077ddcfb8b7acfe2ab3b6afa
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Mon, 08 Feb 2021 23:51:00 +0700
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-mxg8z (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             True
  ContainersReady   True
  PodScheduled      True
Volumes:
  default-token-mxg8z:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  default-token-mxg8z
    Optional:    false
QoS Class:       BestEffort
Node-Selectors:  <none>
Tolerations:     node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                 node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age    From               Message
  ----    ------     ----   ----               -------
  Normal  Scheduled  3m37s  default-scheduler  Successfully assigned default/queue to minikube
  Normal  Pulling    3m36s  kubelet            Pulling image "richardchesterwood/k8s-fleetman-queue:release1"
  Normal  Pulled     2m49s  kubelet            Successfully pulled image "richardchesterwood/k8s-fleetman-queue:release1" in 47.1026686s
  Normal  Created    2m47s  kubelet            Created container queue
  Normal  Started    2m47s  kubelet            Started container queue


Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ minikube ip
192.168.49.2

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ minikube service fleetman-queue
|-----------|----------------|-------------|---------------------------|
| NAMESPACE |      NAME      | TARGET PORT |            URL            |
|-----------|----------------|-------------|---------------------------|
| default   | fleetman-queue | http/8161   | http://192.168.49.2:30010 |
|-----------|----------------|-------------|---------------------------|
* Starting tunnel for service fleetman-queue.
|-----------|----------------|-------------|------------------------|
| NAMESPACE |      NAME      | TARGET PORT |          URL           |
|-----------|----------------|-------------|------------------------|
| default   | fleetman-queue |             | http://127.0.0.1:58199 |
|-----------|----------------|-------------|------------------------|
* Opening service default/fleetman-queue in default browser...
! Because you are using a Docker driver on windows, the terminal needs to be open to run it.

```

![image-20210208235208961](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210208235208961.png)



### 1.2 K8S-Command-Reference.pdf.pdf
## 8. Kubernetes ReplicaSets
### 1. ReplicaSets

Now, pods are very basic and disposable objects in Kubernetes.
In a full running system, it's more than possible that pods are going to die.
Lots of reasons for that.
If a node were to fail, then of course all of the pods running on that node are going to die.
If a pod consumes too many resources, such as CPU, then Kubernetes will kill the pod.
We will talk about that in a dedicated section, but for now, as long as you're aware that
that's a possibility.
So for whatever reason, pods can be short-lived.

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ minikube status
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
timeToStop: Nonexistent


Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ kubectl describe svc fleetman-webapp
Name:                     fleetman-webapp
Namespace:                default
Labels:                   <none>
Annotations:              <none>
Selector:                 app=webapp,release=0-5
Type:                     NodePort
IP:                       10.96.67.149
Port:                     http  80/TCP
TargetPort:               80/TCP
NodePort:                 http  30080/TCP
Endpoints:                172.17.0.4:80
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ kubectl get all
NAME                     READY   STATUS    RESTARTS   AGE
pod/queue                1/1     Running   0          9h
pod/webapp               1/1     Running   0          10h
pod/webapp-release-0     1/1     Running   0          9h
pod/webapp-release-0-5   1/1     Running   0          10h

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   9h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     10h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          10h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ kubectl delete po webapp-release-0-5
pod "webapp-release-0-5" deleted

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ kubectl get all
NAME                   READY   STATUS    RESTARTS   AGE
pod/queue              1/1     Running   0          10h
pod/webapp             1/1     Running   0          10h
pod/webapp-release-0   1/1     Running   0          10h

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   10h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     10h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          10h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise

```

Now we will delete a pod 

What we do with a ReplicaSet is we just provide, really, an additional piece of configuration to Kubernetes.
We specify how many instances of this pod do we want Kubernetes to make sure are running
at any one time?
So we could start simple, and we could simply specify that we want one replica of this pod to be running at any one time.
And all that will mean is, if this pod were to die for any reason, any reason at all, then Kubernetes will spring up another one.
And I would suggest, therefore, you're going to be doing this in general for all of your pods.
So if you're deploying a general microservice pod, once again, you would be wrapping it inside a ReplicaSet.
Now, we'll keep the replicas at one for now, but you can probably guess that we can use
any number we want in there, more on that later.
But first we need to learn how to define a replica set.
So how do we define a replica set, then?
![image-20210209101446657](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209101446657.png)

https://kubernetes.io/docs/reference/kubernetes-api/workloads-resources/replica-set-v1/

Notice `group` is app/v1



### 2. Writing a ReplicaSet

D:\git-docs\docker\Source\Udemy - Kubernetes Hands-On - Deploy Microservices to the AWS Cloud\1. Introduction\Chapter 8 ReplicaSets\pods.yaml

```ini

apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: webapp
spec:
  selector:
    matchLabels:
      app: webapp
  replicas: 2
  template: # template for the pods
    metadata:
      labels:
        app: webapp
    spec:
      containers:
      - name: webapp
        image: richardchesterwood/k8s-fleetman-webapp-angular:release0-5

---
apiVersion: v1
kind: Pod
metadata:
  name: queue
  labels:
    app: queue
spec:
  containers:
  - name: queue
    image: richardchesterwood/k8s-fleetman-queue:release1

```

D:\git-docs\docker\Source\Udemy - Kubernetes Hands-On - Deploy Microservices to the AWS Cloud\1. Introduction\Chapter 8 ReplicaSets\services.yaml

```ini
apiVersion: v1
kind: Service
metadata:
  name: fleetman-webapp

spec:
  # This defines which pods are going to be represented by this Service
  # The service becomes a network endpoint for either other services
  # or maybe external users to connect to (eg browser)
  selector:
    app: webapp
    # remove release: "0-5"

  ports:
    - name: http
      port: 80
      nodePort: 30080

  type: NodePort
---
apiVersion: v1
kind: Service
metadata:
  name: fleetman-queue

spec:
  # This defines which pods are going to be represented by this Service
  # The service becomes a network endpoint for either other services
  # or maybe external users to connect to (eg browser)
  selector:
    app: queue

  ports:
    - name: http
      port: 8161
      nodePort: 30010

  type: NodePort

```

![image-20210209151933496](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209151933496.png)





### 3. Applying a ReplicaSet to Kubernetes

Delete all pods

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ kubectl get all
NAME                   READY   STATUS    RESTARTS   AGE
pod/queue              1/1     Running   0          10h
pod/webapp             1/1     Running   0          10h
pod/webapp-release-0   1/1     Running   0          10h

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   10h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     10h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          10h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ kubectl delete po --all
pod "queue" deleted
pod "webapp" deleted
pod "webapp-release-0" deleted

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ kubectl get all
NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   15h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     15h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          15h

```

> If some pods are still existing, you must run this command again.

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 7 Exercise
$ cd ../Chapter\ 8\ ReplicaSets/

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl apply -f pods.yaml
replicaset.apps/webapp created
pod/queue created

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl get all
NAME               READY   STATUS              RESTARTS   AGE
pod/queue          0/1     ContainerCreating   0          4s
pod/webapp-5f2vd   0/1     ContainerCreating   0          4s
pod/webapp-cgrz4   0/1     ContainerCreating   0          4s

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   15h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     15h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          15h

NAME                     DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp   2         2         0       4s

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl describe replicaset webapp
Name:         webapp
Namespace:    default
Selector:     app=webapp
Labels:       <none>
Annotations:  <none>
Replicas:     2 current / 2 desired
Pods Status:  2 Running / 0 Waiting / 0 Succeeded / 0 Failed
Pod Template:
  Labels:  app=webapp
  Containers:
   webapp:
    Image:        richardchesterwood/k8s-fleetman-webapp-angular:release0-5
    Port:         <none>
    Host Port:    <none>
    Environment:  <none>
    Mounts:       <none>
  Volumes:        <none>
Events:
  Type    Reason            Age   From                   Message
  ----    ------            ----  ----                   -------
  Normal  SuccessfulCreate  32s   replicaset-controller  Created pod: webapp-5f2vd
  Normal  SuccessfulCreate  32s   replicaset-controller  Created pod: webapp-cgrz4

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl describe rs webapp
Name:         webapp
Namespace:    default
Selector:     app=webapp
Labels:       <none>
Annotations:  <none>
Replicas:     2 current / 2 desired
Pods Status:  2 Running / 0 Waiting / 0 Succeeded / 0 Failed
Pod Template:
  Labels:  app=webapp
  Containers:
   webapp:
    Image:        richardchesterwood/k8s-fleetman-webapp-angular:release0-5
    Port:         <none>
    Host Port:    <none>
    Environment:  <none>
    Mounts:       <none>
  Volumes:        <none>
Events:
  Type    Reason            Age   From                   Message
  ----    ------            ----  ----                   -------
  Normal  SuccessfulCreate  59s   replicaset-controller  Created pod: webapp-5f2vd
  Normal  SuccessfulCreate  59s   replicaset-controller  Created pod: webapp-cgrz4

```

Remove release tag in the service file

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl apply -f services.yaml
service/fleetman-webapp configured
service/fleetman-queue unchanged

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl get all
NAME               READY   STATUS    RESTARTS   AGE
pod/queue          1/1     Running   0          16m
pod/webapp-5f2vd   1/1     Running   0          16m
pod/webapp-cgrz4   1/1     Running   0          16m

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   15h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     16h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          16h

NAME                     DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp   2         2         2       16m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ minikube ip
192.168.49.2

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ minikube service fleetman-webapp
|-----------|-----------------|-------------|---------------------------|
| NAMESPACE |      NAME       | TARGET PORT |            URL            |
|-----------|-----------------|-------------|---------------------------|
| default   | fleetman-webapp | http/80     | http://192.168.49.2:30080 |
|-----------|-----------------|-------------|---------------------------|
* Starting tunnel for service fleetman-webapp.
|-----------|-----------------|-------------|------------------------|
| NAMESPACE |      NAME       | TARGET PORT |          URL           |
|-----------|-----------------|-------------|------------------------|
| default   | fleetman-webapp |             | http://127.0.0.1:54268 |
|-----------|-----------------|-------------|------------------------|
* Opening service default/fleetman-webapp in default browser...
! Because you are using a Docker driver on windows, the terminal needs to be open to run it.
```

![image-20210209154912480](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209154912480.png)

Reload page to see the result

Try to test

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl get all
NAME               READY   STATUS    RESTARTS   AGE
pod/queue          1/1     Running   0          16m
pod/webapp-5f2vd   1/1     Running   0          16m
pod/webapp-cgrz4   1/1     Running   0          16m

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   15h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     16h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          16h

NAME                     DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp   2         2         2       16m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl delete po webapp-cgrz4
pod "webapp-cgrz4" deleted

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl get all
NAME               READY   STATUS    RESTARTS   AGE
pod/queue          1/1     Running   0          23m
pod/webapp-5f2vd   1/1     Running   0          23m
pod/webapp-np59l   1/1     Running   0          44s

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   16h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     16h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          16h

NAME                     DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp   2         2         2       23m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl describe rs webapp
Name:         webapp
Namespace:    default
Selector:     app=webapp
Labels:       <none>
Annotations:  <none>
Replicas:     2 current / 2 desired
Pods Status:  2 Running / 0 Waiting / 0 Succeeded / 0 Failed
Pod Template:
  Labels:  app=webapp
  Containers:
   webapp:
    Image:        richardchesterwood/k8s-fleetman-webapp-angular:release0-5
    Port:         <none>
    Host Port:    <none>
    Environment:  <none>
    Mounts:       <none>
  Volumes:        <none>
Events:
  Type    Reason            Age    From                   Message
  ----    ------            ----   ----                   -------
  Normal  SuccessfulCreate  24m    replicaset-controller  Created pod: webapp-5f2vd
  Normal  SuccessfulCreate  24m    replicaset-controller  Created pod: webapp-cgrz4
  Normal  SuccessfulCreate  2m11s  replicaset-controller  Created pod: webapp-np59l
```

![image-20210209155459603](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209155459603.png)

Solution for downtime => 2 replicaset



## 9. Kubernetes Deployments
### 1. Deployments Overview

![image-20210209155938927](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209155938927.png)

> With zero downtime





```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl get all
NAME               READY   STATUS    RESTARTS   AGE
pod/queue          1/1     Running   0          39m
pod/webapp-5f2vd   1/1     Running   0          39m
pod/webapp-np59l   1/1     Running   0          17m

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   16h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     16h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          16h

NAME                     DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp   2         2         2       39m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl delete rs webapp
replicaset.apps "webapp" deleted

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl get all
NAME               READY   STATUS        RESTARTS   AGE
pod/queue          1/1     Running       0          39m
pod/webapp-5f2vd   0/1     Terminating   0          39m
pod/webapp-np59l   0/1     Terminating   0          17m

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   16h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     16h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          16h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl get all
NAME               READY   STATUS        RESTARTS   AGE
pod/queue          1/1     Running       0          39m
pod/webapp-5f2vd   0/1     Terminating   0          39m
pod/webapp-np59l   0/1     Terminating   0          17m

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   16h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     16h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          16h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 8 ReplicaSets
$ kubectl get all
NAME        READY   STATUS    RESTARTS   AGE
pod/queue   1/1     Running   0          39m

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   16h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     16h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          16h
```

Change context

D:\git-docs\docker\Source\Udemy - Kubernetes Hands-On - Deploy Microservices to the AWS Cloud\1. Introduction\Chapter 9 Deployments\pods.yaml

```ini
apiVersion: apps/v1
kind: Deployment # change
metadata:
  name: webapp
spec:
  # minReadySeconds: 30
  selector:
    matchLabels:
      app: webapp
  replicas: 2
  template: # template for the pods
    metadata:
      labels:
        app: webapp
    spec:
      containers:
      - name: webapp
        image: richardchesterwood/k8s-fleetman-webapp-angular:release0 # change
```

RUN

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl apply -f pods.yaml
deployment.apps/webapp created
pod/queue unchanged

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get all
NAME                          READY   STATUS    RESTARTS   AGE
pod/queue                     1/1     Running   0          43m
pod/webapp-77896f4bf8-bbzvb   1/1     Running   0          3s
pod/webapp-77896f4bf8-tc7lw   1/1     Running   0          3s

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   16h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     16h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          16h

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/webapp   2/2     2            2           3s

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp-77896f4bf8   2         2         2       3s

```

Version 0

![image-20210209164006429](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209164006429.png)



![image-20210209162050805](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209162050805.png)

![image-20210209162105699](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209162105699.png)

So we need to see then **how can we do a rolling deployment**
without needing to fiddle around with labels like we did before using this Kubernetes deployments?
And the answer is wonderfully simple.
As long as we're working with a different container image, when we make a change to the image
that is being used by a deployment and we re-deploy that deployment,
then Kubernetes will start a brand new replica set and the pods that that replica set are managing
will contain the updated image.
And once the pods in the new version of this replica set are responding to requests, then effectively,
the required number of replicas in the old replica set will be switched to zero.
And that will mean that **these old pods will be stopped**.



Now what I'm trying to illustrate here is that the old replica set is still there,
it's just that the number of replicas on it is now set to zero.
That's significant because it means that if we decide we need to roll back,
if something goes wrong with this deployment,
then we can resurrect the old version of the replica set by,
I'll show you how to do this, there's a special command for it (`kubectl rollout status deploy webapp`),
but we can effectively reset this number of replicas
back to two on the old replica set, that's if we want to go backwards.
So it's quite elegant and really quite simple.
So the important thing to recap then is this is all working on the container image,
the container image does need to change and we typically do that
by using different tags on the images.

https://kubernetes.io/docs/reference/kubernetes-api/workloads-resources/deployment-v1/

> **minReadySeconds** (int32)
>
> Minimum number of seconds for which a newly created pod should be ready without any of its container crashing, for it to be considered available. Defaults to 0 (pod will be considered available as soon as it is ready)

Add

```ini
spec:
  # add this one
  minReadySeconds: 30

   # ...

spec:
      containers:
      - name: webapp
        image: richardchesterwood/k8s-fleetman-webapp-angular:release0-5 # change
```

Run

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl rollout status deploy webapp
deployment "webapp" successfully rolled out

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get all
NAME                          READY   STATUS    RESTARTS   AGE
pod/queue                     1/1     Running   0          77m
pod/webapp-6ccdfd88cb-fnqns   1/1     Running   0          7m48s
pod/webapp-6ccdfd88cb-s445l   1/1     Running   0          7m47s

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   16h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     17h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          17h

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/webapp   2/2     2            2           34m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp-6ccdfd88cb   2         2         2       7m48s
replicaset.apps/webapp-77896f4bf8   0         0         0       34m
```

Change and click CTRL f5 to see the change

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl apply -f pods.yaml
deployment.apps/webapp configured
pod/queue unchanged

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get all
NAME                          READY   STATUS        RESTARTS   AGE
pod/queue                     1/1     Running       0          79m
pod/webapp-6ccdfd88cb-fnqns   0/1     Terminating   0          9m52s
pod/webapp-6ccdfd88cb-s445l   0/1     Terminating   0          9m51s
pod/webapp-77896f4bf8-8xsdw   1/1     Running       0          3s
pod/webapp-77896f4bf8-vmhcr   1/1     Running       0          4s

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   16h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     17h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          17h

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/webapp   2/2     2            2           36m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp-6ccdfd88cb   0         0         0       9m52s
replicaset.apps/webapp-77896f4bf8   2         2         2       36m

```

https://kubernetes.io/docs/concepts/workloads/controllers/deployment/

> To see the Deployment rollout status, run `kubectl rollout status deployment/nginx-deployment`.
>
> The output is similar to:
>
> ```
> Waiting for rollout to finish: 2 out of 3 new replicas have been updated...
> deployment "nginx-deployment" successfully rolled out
> ```

![image-20210209165203395](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209165203395.png)

You can see the new version



### 2. Managing Rollouts

![image-20210209165439495](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209165439495.png)

You can change file pods.yaml and run again to check status for deployment

In the meantime, you can visit the browser to see the old version since it go back in the history

![image-20210209165735076](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209165735076.png)

You can this flag because it always go back one version



![image-20210209165903064](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209165903064.png)

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl rollout history deploy webapp
deployment.apps/webapp
REVISION  CHANGE-CAUSE
2         <none>
3         <none>


Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl rollout undo deploy webapp
deployment.apps/webapp rolled back

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl rollout history deploy webapp
deployment.apps/webapp
REVISION  CHANGE-CAUSE
3         <none>
4         <none>


Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ minikube service fleetman-webapp
|-----------|-----------------|-------------|---------------------------|
| NAMESPACE |      NAME       | TARGET PORT |            URL            |
|-----------|-----------------|-------------|---------------------------|
| default   | fleetman-webapp | http/80     | http://192.168.49.2:30080 |
|-----------|-----------------|-------------|---------------------------|
* Starting tunnel for service fleetman-webapp.
|-----------|-----------------|-------------|------------------------|
| NAMESPACE |      NAME       | TARGET PORT |          URL           |
|-----------|-----------------|-------------|------------------------|
| default   | fleetman-webapp |             | http://127.0.0.1:51422 |
|-----------|-----------------|-------------|------------------------|
* Opening service default/fleetman-webapp in default browser...
! Because you are using a Docker driver on windows, the terminal needs to be open to run it.

```

![image-20210209170252476](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209170252476.png)

> We recommend this is used only in stressful emergency situations! Your
>
> YAML will now be out of date with the live deployment!

Use wrong image

```ini
    spec:
      containers:
      - name: webapp
        image: richardchesterwood/k8s-fleetman-webapp-angular:releasekjadhskjdfs0-5
```

You can check status

![image-20210209170856816](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209170856816.png)

webapp-64c.. is not ready and pod is not running

Run again

![image-20210209171059818](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209171059818.png)

Status is PullBackOff

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get all
NAME                          READY   STATUS    RESTARTS   AGE
pod/queue                     1/1     Running   0          103m
pod/webapp-77896f4bf8-kk7z2   1/1     Running   0          9m42s
pod/webapp-77896f4bf8-l5v4b   1/1     Running   0          9m43s

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   17h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     17h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          17h

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/webapp   2/2     2            2           60m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp-6ccdfd88cb   0         0         0       33m
replicaset.apps/webapp-77896f4bf8   2         2         2       60m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl apply -f pods.yaml
deployment.apps/webapp configured
pod/queue unchanged

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get all
NAME                          READY   STATUS              RESTARTS   AGE
pod/queue                     1/1     Running             0          104m
pod/webapp-588c8764bc-zvbnt   0/1     ContainerCreating   0          5s
pod/webapp-77896f4bf8-kk7z2   1/1     Running             0          9m54s
pod/webapp-77896f4bf8-l5v4b   1/1     Running             0          9m55s

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   17h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     17h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          17h

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/webapp   2/2     1            2           60m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp-588c8764bc   1         1         0       5s
replicaset.apps/webapp-6ccdfd88cb   0         0         0       33m
replicaset.apps/webapp-77896f4bf8   2         2         2       60m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get all
NAME                          READY   STATUS         RESTARTS   AGE
pod/queue                     1/1     Running        0          104m
pod/webapp-588c8764bc-zvbnt   0/1     ErrImagePull   0          11s
pod/webapp-77896f4bf8-kk7z2   1/1     Running        0          10m
pod/webapp-77896f4bf8-l5v4b   1/1     Running        0          10m

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   17h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     17h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          17h

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/webapp   2/2     1            2           60m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp-588c8764bc   1         1         0       11s
replicaset.apps/webapp-6ccdfd88cb   0         0         0       34m
replicaset.apps/webapp-77896f4bf8   2         2         2       60m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl describe po webapp-588c8764bc-zvbnt
Name:         webapp-588c8764bc-zvbnt
Namespace:    default
Priority:     0
Node:         minikube/192.168.49.2
Start Time:   Tue, 09 Feb 2021 17:12:57 +0700
Labels:       app=webapp
              pod-template-hash=588c8764bc
Annotations:  <none>
Status:       Pending
IP:           172.17.0.3
IPs:
  IP:           172.17.0.3
Controlled By:  ReplicaSet/webapp-588c8764bc
Containers:
  webapp:
    Container ID:
    Image:          richardchesterwood/k8s-fleetman-webapp-angular:releassdfsdfsdfe0-5
    Image ID:
    Port:           <none>
    Host Port:      <none>
    State:          Waiting
      Reason:       ImagePullBackOff
    Ready:          False
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-mxg8z (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             False
  ContainersReady   False
  PodScheduled      True
Volumes:
  default-token-mxg8z:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  default-token-mxg8z
    Optional:    false
QoS Class:       BestEffort
Node-Selectors:  <none>
Tolerations:     node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                 node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason     Age                 From               Message
  ----     ------     ----                ----               -------
  Normal   Scheduled  101s                default-scheduler  Successfully assigned default/webapp-588c8764bc-zvbnt to minikube
  Normal   Pulling    44s (x3 over 100s)  kubelet            Pulling image "richardchesterwood/k8s-fleetman-webapp-angular:releassdfsdfsdfe0-5"
  Warning  Failed     36s (x3 over 94s)   kubelet            Failed to pull image "richardchesterwood/k8s-fleetman-webapp-angular:releassdfsdfsdfe0-5": rpc error: code = Unknown desc = Error
 response from daemon: manifest for richardchesterwood/k8s-fleetman-webapp-angular:releassdfsdfsdfe0-5 not found: manifest unknown: manifest unknown
  Warning  Failed     36s (x3 over 94s)   kubelet            Error: ErrImagePull
  Normal   BackOff    9s (x4 over 94s)    kubelet            Back-off pulling image "richardchesterwood/k8s-fleetman-webapp-angular:releassdfsdfsdfe0-5"
  Warning  Failed     9s (x4 over 94s)    kubelet            Error: ImagePullBackOff

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments

```

Then we will delete manually 

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get all
NAME                          READY   STATUS    RESTARTS   AGE
pod/queue                     1/1     Running   0          113m
pod/webapp-77896f4bf8-kk7z2   1/1     Running   0          18m
pod/webapp-77896f4bf8-l5v4b   1/1     Running   0          18m

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   17h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     17h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          17h

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/webapp   2/2     2            2           69m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp-588c8764bc   0         0         0       9m5s
replicaset.apps/webapp-6ccdfd88cb   0         0         0       42m
replicaset.apps/webapp-77896f4bf8   2         2         2       69m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl delete rs webapp-588c8764bc
replicaset.apps "webapp-588c8764bc" deleted

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get all
NAME                          READY   STATUS    RESTARTS   AGE
pod/queue                     1/1     Running   0          113m
pod/webapp-77896f4bf8-kk7z2   1/1     Running   0          19m
pod/webapp-77896f4bf8-l5v4b   1/1     Running   0          19m

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   17h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     17h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          17h

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/webapp   2/2     2            2           70m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp-6ccdfd88cb   0         0         0       43m
replicaset.apps/webapp-77896f4bf8   2         2         2       70m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments

```





## 10. Networking and Service Discovery

### 1. Networking Overview in Kubernetes

![image-20210209182745306](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209182745306.png)

if you decided to deploy these two containers into a single pod, then things are very easy.
In fact, the two containers can see each other using localhost, so if I were writing any code
in this Java application I could just do a lookup of the address, localhost, colon,
and I would use the MySQL port 3306.



Having the database and an application running in the same pod would make this pod
much more complicated to manage. If this pod fails, then we're going to have to find
out if it's failed because of the database container or if it's failed because of the application container,
and generally, it just makes things more complicated.
I don't recommend, until you have some very specialist requirements, I don't recommend having multiple containers in a pod.

![image-20210209183423632](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209183423632.png)

Now, you will have noticed earlier on in the course that each of the services
is given it's own private IP address, an IP address that is only visible inside the Kubernetes cluster.
All we really need if we wanted to write some code in the application that wants to communicate
with the database is we just need to reference the IP address of the database service.
Of course, we're not going to know the IP address
of that service because these IP addresses are allocated dynamically by Kubernetes.
The next time that we run the Kubernetes cluster, there will probably be different IP addresses allocated to the services, and the solution is Kubernetes maintains its own private DNS service.
I don't know how familiar you are with DNS services, but the DNS service is basically a database
containing a set of key value pairs.





### 2. Namespaces - kube-system

![image-20210209184335093](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209184335093.png)

**I need to explain how namespaces work in Kubernetes.**
A namespace is a way of partitioning your resources in Kubernetes into separate areas.
As an example, imagine you're working on a system which has thousands of resources.
Let's for now just think about thousands of pods
and thousands of services, but actually everything I'm about to say also applies
to resources such as deployments and replica sets and so on.
I've only put a few on this picture for illustration, and I've made all of these names up.
We're going to be working on a real microservice architecture soon.
But if you can imagine working on this Kubernetes system,
remembers there's thousands of these pods.
It's going to be very difficult to work on that system because there are just too many pods.
So, the idea of a namespace is we can go through our pods and our services, and we can allocate them to namespaces.
So, in this very simple example, I might notice as the architect that, well, this pod,
and it would have an associated service, is a web container.

> And what happens when you don't specify a namespace is the resource is put into the default namespace.
> And whenever you issue a command like kubectl get all, if you don't specify a namespace,
> you only see the resources in the default namespace.



```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get all
NAME                          READY   STATUS    RESTARTS   AGE
pod/queue                     1/1     Running   0          3h9m
pod/webapp-77896f4bf8-kk7z2   1/1     Running   0          95m
pod/webapp-77896f4bf8-l5v4b   1/1     Running   0          95m

NAME                      TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
service/fleetman-queue    NodePort    10.100.41.19   <none>        8161:30010/TCP   18h
service/fleetman-webapp   NodePort    10.96.67.149   <none>        80:30080/TCP     19h
service/kubernetes        ClusterIP   10.96.0.1      <none>        443/TCP          19h

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/webapp   2/2     2            2           146m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp-6ccdfd88cb   0         0         0       119m
replicaset.apps/webapp-77896f4bf8   2         2         2       146m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get ns
NAME              STATUS   AGE
default           Active   19h
kube-node-lease   Active   19h
kube-public       Active   19h
kube-system       Active   19h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments

```



Now, if we want to see what's in those namespaces,
then we have to be specific. 

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get po
NAME                      READY   STATUS    RESTARTS   AGE
queue                     1/1     Running   0          3h18m
webapp-77896f4bf8-kk7z2   1/1     Running   0          103m
webapp-77896f4bf8-l5v4b   1/1     Running   0          103m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get po -n kube-system
NAME                               READY   STATUS    RESTARTS   AGE
coredns-74ff55c5b-9cmnq            1/1     Running   0          19h
etcd-minikube                      1/1     Running   0          19h
kube-apiserver-minikube            1/1     Running   0          19h
kube-controller-manager-minikube   1/1     Running   0          19h
kube-proxy-pf7n7                   1/1     Running   0          19h
kube-scheduler-minikube            1/1     Running   0          19h
storage-provisioner                1/1     Running   1          19h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get all -n kube-system
NAME                                   READY   STATUS    RESTARTS   AGE
pod/coredns-74ff55c5b-9cmnq            1/1     Running   0          19h
pod/etcd-minikube                      1/1     Running   0          19h
pod/kube-apiserver-minikube            1/1     Running   0          19h
pod/kube-controller-manager-minikube   1/1     Running   0          19h
pod/kube-proxy-pf7n7                   1/1     Running   0          19h
pod/kube-scheduler-minikube            1/1     Running   0          19h
pod/storage-provisioner                1/1     Running   1          19h

NAME               TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)                  AGE
service/kube-dns   ClusterIP   10.96.0.10   <none>        53/UDP,53/TCP,9153/TCP   19h

NAME                        DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR            AGE
daemonset.apps/kube-proxy   1         1         1       1            1           kubernetes.io/os=linux   19h

NAME                      READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/coredns   1/1     1            1           19h

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/coredns-74ff55c5b   1         1         1       19h


```

You can see `kube-dns`



```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get ns
NAME              STATUS   AGE
default           Active   20h
kube-node-lease   Active   20h
kube-public       Active   20h
kube-system       Active   20h

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl get all -n kube-public
No resources found in kube-public namespace.

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 9 Deployments
$ kubectl describe svc kube-dns -n kube-system
Name:              kube-dns
Namespace:         kube-system
Labels:            k8s-app=kube-dns
                   kubernetes.io/cluster-service=true
                   kubernetes.io/name=KubeDNS
Annotations:       prometheus.io/port: 9153
                   prometheus.io/scrape: true
Selector:          k8s-app=kube-dns
Type:              ClusterIP
IP:                10.96.0.10
Port:              dns  53/UDP
TargetPort:        53/UDP
Endpoints:         172.17.0.2:53
Port:              dns-tcp  53/TCP
TargetPort:        53/TCP
Endpoints:         172.17.0.2:53
Port:              metrics  9153/TCP
TargetPort:        9153/TCP
Endpoints:         172.17.0.2:9153
Session Affinity:  None
Events:            <none>

```



https://stackoverflow.com/questions/45929548/whats-the-kube-public-namespace-for

 You might be thinking, as I did at first, that kube-public is possibly
where you put your pods and resources, and kube-system is used
for the internal infrastructure of Kubernetes.



### 3. Accessing MySQL from a Pod

D:\devops-practices\k8s\Chapter 10 Networking\networking-tests.yaml

```ini
apiVersion: v1
kind: Pod
metadata:
  name: mysql
  labels:
    app: mysql
spec:
  containers:
   - name: mysql
     image: mysql:5
     env:
      # Use secret in real life
      - name: MYSQL_ROOT_PASSWORD
        value: password
      - name: MYSQL_DATABASE
        value: fleetman
---
kind: Service
apiVersion: v1
metadata:
  name: database
spec:
  selector:
    app: mysql
  ports:
  - port: 3306
  type: ClusterIP

```

https://github.com/DickChesterwood/k8s-fleetman

https://github.com/DickChesterwood/k8s-fleetman/blob/master/k8s-fleetman-webapp-angular/Dockerfile

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 10 Networking
$ ls
networking-tests.yaml  pods.yaml  services.yaml

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 10 Networking
$ kubectl apply -f networking-tests.yaml
pod/mysql created
service/database created

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 10 Networking
$ kubectl get all
NAME                          READY   STATUS              RESTARTS   AGE
pod/mysql                     0/1     ContainerCreating   0          8s
pod/queue                     1/1     Running             0          5h4m
pod/webapp-77896f4bf8-kk7z2   1/1     Running             0          3h29m
pod/webapp-77896f4bf8-l5v4b   1/1     Running             0          3h30m

NAME                      TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
service/database          ClusterIP   10.102.121.122   <none>        3306/TCP         8s
service/fleetman-queue    NodePort    10.100.41.19     <none>        8161:30010/TCP   20h
service/fleetman-webapp   NodePort    10.96.67.149     <none>        80:30080/TCP     20h
service/kubernetes        ClusterIP   10.96.0.1        <none>        443/TCP          20h

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/webapp   2/2     2            2           4h20m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp-6ccdfd88cb   0         0         0       3h54m
replicaset.apps/webapp-77896f4bf8   2         2         2       4h20m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 10 Networking
$ kubectl exec -it webapp-77896f4bf8-kk7z2 sh
kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
/ # exit

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 10 Networking
$ kubectl exec -it webapp-77896f4bf8-kk7z2 -- sh
/ # ls
bin    dev    etc    home   lib    media  mnt    proc   root   run    sbin   srv    sys    tmp    usr    var

```





### 4. Cygwin extra - fixing the terminal with winpty

https://github.com/rprichard/winpty/releases



![image-20210209210307613](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209210307613.png)

![image-20210209210438748](kubernetes-hands-on-deploy-microservices-to-the-aws-cloud.assets/image-20210209210438748.png)





### 5. Service Discovery

```shell
Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 10 Networking
$ kubectl exec -it webapp-77896f4bf8-kk7z2 -- sh
/ # ls
bin    dev    etc    home   lib    media  mnt    proc   root   run    sbin   srv    sys    tmp    usr    var
/ # cat /etc/resolv.conf
nameserver 10.96.0.10
search default.svc.cluster.local svc.cluster.local cluster.local
options ndots:5
/ # nslookup google.com
nslookup: can't resolve '(null)': Name does not resolve

Name:      google.com
Address 1: 74.125.24.138
Address 2: 74.125.24.102
Address 3: 74.125.24.101
Address 4: 74.125.24.113
Address 5: 74.125.24.139
Address 6: 74.125.24.100
Address 7: 2404:6800:4003:c04::66
Address 8: 2404:6800:4003:c04::65
Address 9: 2404:6800:4003:c04::8b
Address 10: 2404:6800:4003:c04::71
/ # nslookup database
nslookup: can't resolve '(null)': Name does not resolve

Name:      database
Address 1: 10.102.121.122 database.default.svc.cluster.local
/ # exit

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 10 Networking
$ kubectl get all
NAME                          READY   STATUS    RESTARTS   AGE
pod/mysql                     1/1     Running   0          43m
pod/queue                     1/1     Running   0          5h47m
pod/webapp-77896f4bf8-kk7z2   1/1     Running   0          4h13m
pod/webapp-77896f4bf8-l5v4b   1/1     Running   0          4h13m

NAME                      TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
service/database          ClusterIP   10.102.121.122   <none>        3306/TCP         43m
service/fleetman-queue    NodePort    10.100.41.19     <none>        8161:30010/TCP   21h
service/fleetman-webapp   NodePort    10.96.67.149     <none>        80:30080/TCP     21h
service/kubernetes        ClusterIP   10.96.0.1        <none>        443/TCP          21h

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/webapp   2/2     2            2           5h4m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/webapp-6ccdfd88cb   0         0         0       4h37m
replicaset.apps/webapp-77896f4bf8   2         2         2       5h4m

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 10 Networking

```



```shell

Admin@LAPTOP-QO8E8EAL /cygdrive/d/devops-practices/k8s/Chapter 10 Networking
$ kubectl exec -it webapp-77896f4bf8-kk7z2 -- sh
/ # apk update
fetch http://dl-cdn.alpinelinux.org/alpine/v3.7/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.7/community/x86_64/APKINDEX.tar.gz
v3.7.3-184-gffd32bfd09 [http://dl-cdn.alpinelinux.org/alpine/v3.7/main]
v3.7.3-183-gcc9ad2b48d [http://dl-cdn.alpinelinux.org/alpine/v3.7/community]
OK: 9070 distinct packages available
/ # apk add mysql-client
(1/6) Installing mariadb-common (10.1.41-r0)
(2/6) Installing ncurses-terminfo-base (6.0_p20171125-r1)
(3/6) Installing ncurses-terminfo (6.0_p20171125-r1)
(4/6) Installing ncurses-libs (6.0_p20171125-r1)
(5/6) Installing mariadb-client (10.1.41-r0)
(6/6) Installing mysql-client (10.1.41-r0)
Executing busybox-1.27.2-r7.trigger
OK: 53 MiB in 34 packages
/ # mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/run/mysqld/mysqld.sock' (2 "No such file or directory")

/ # mysql -h database -uroot -ppassword fleetman
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.7.33 MySQL Community Server (GPL)

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MySQL [fleetman]> create table testtable(test varchar(255));
Query OK, 0 rows affected (0.02 sec)

MySQL [fleetman]> show tables;
+--------------------+
| Tables_in_fleetman |
+--------------------+
| testtable          |
+--------------------+
1 row in set (0.01 sec)


```



### 6. Fully Qualified Domain Names (FQDN)



## 11. Microservice Architectures

### 1. WARNING - possible resource problems!.html

### 10. Deploying the Webapp

### 2. An Introduction to Microservices

### 3. Introduction to Microservices Part 2

### 4. Fleetman Microservices - setting the scene

### 5. Deploying the Queue

### 6. Deploying the Position Simulator

### 7. Inspecting Pod Logs

### 8. Deploying the Position Tracker

### 9. Deploying the API Gateway

## 12. Kubernetes Persistence and Volumes

### 1. Persistence

### 2. Upgrading to a Mongo Pod

### 3. Mongo Service

### 4. Expanding the Minikube VM

### 5. Volume Mounts

### 6. Volumes

### 7. PersistentVolumeClaims

### 8. StorageClasses and Binding

## 13. Running Kubernetes on the AWS Cloud

### 1. Warning.html

### 10. Setting up a real Domain Name

### 11. Surviving Node Failure

### 12. Replicating Pods in Kubernetes

### 2. Getting started with AWS

### 3. Introducing Kops - Kubernetes Operations

### 4. Installing the Kops Environment

### 5. Warning - EC2 Instance types across regions.html

### 6. Configuring your first cluster

### 7. Running the Cluster

### 8. Provisioning SSD drives with a StorageClass

### 9. Deploying the Fleetman Workload to Kubernetes

## 14. Deleting the Cluster

### 1. Deleting the Cluster

### 2. Restarting the Cluster

## 15. Extra - how to run Kubernetes in Google Cloud

### 1. How to deploy to Google Cloud Platform.html

## 16. Logging a Kubernetes Cluster

### 1. Introducing the ELK  ElasticStack

### 2. Installing the Stack to Kubernetes

### 3. Kibana - first look

### 4. Setting Filters and Refreshes

### 5. Demo analysing a system failure

### 6. Kibana Dashboards

## 17. Monitoring a Kubernetes Cluster with Prometheus and Grafana

### 1. Monitoring a Cluster

### 2. Helm Package Manager

### 3. Errata - steps needed to get a full set of data from Prometheus.html

### 4. Installing Prometheus Operator

### 5. Working with Grafana

## 18. The Alert Manager

### 1. Alerting

### 2. Setting up a Slack Channel

### 3. Configuring the AlertManager

### 4. Errata - different secret name.html

### 5. Applying the config with a Secret

### 6. Dealing with Alerts

### 7. What happens if the Master Node crashes

### 8. Case Study Troubleshooting a Delinquent node

## 19. Going Further with Kubernetes

### 1. Course Update 2019 Introduction to the Advanced Section

### 2. Code  files for this section.html



## 20. Kubernetes Requests and Limits

### 1. Memory requests

### 2. CPU Requests

### 3. Memory and CPU Limits

## 21. Metrics Profiling in Kubernetes

### 1. Enabling the Metrics Server

### 2. Viewing Metrics on the Dashboard

### 3. Tuning Java Spring Boot Applications, Heap restriction

### 4. Setting reasonable Requests

## 22. Horizontal Pod Autoscaling

### 1. Introducing Replication and Autoscaling

### 2. Testing Autoscaling

## 23. Readiness and Liveness Probes

### 1. Demo why readiness probes are needed

### 2. Applying Liveness and Readiness Probes

## 24. Quality of Service and Eviction

### 1. Understanding the scheduler

### 2. QoS labels

### 3. Evictions

### 4. Pod Priorities

## 25. RBAC (Role Based Access Control) on a Kubernetes cluster

### 1. Defining Roles

### 2. Defining RoleBindings

### 3. Setting up a context for the user

### 4. Issuing a Kubernetes signed X.509 certificate

### 5. Installing the user's certificate

### 6. Allocating Access to Users

### 7. ClusterRoles and ClusterRoleBindings

## 26. Kubernetes ConfigMaps and Secrets

### 1. Creating a ConfigMap

### 2. Consuming a ConfigMap as Environment Variables

### 3. Do changes to a ConfigMap get propagated

### 4. How to consume multiple envioronments variables with envFrom

### 5. Mounting ConfigMaps as Volumes

### 6. Creating Secrets

### 7. Using Secrets

### 8. Where have we already used ConfigMaps and Secrets

### 9. (extra) Using Spring Cloud Kubernetes to Hot Reload ConfigMaps.html

## 27. Ingress Controllers

### 1. Introducing Ingress

### 2. Defining Routing Rules

### 3. Adding Routes

### 4. Authentication

### 5. Running Ingress on AWS

### 6. Tesing the Ingress Rules

### 7. (Extra) setting up HTTPS with TLS termination at the load balancer.html

## 28. Other Workload Types

### 1. Batch Jobs

### 2. Cron Jobs

### 3. DaemonSets

### 4. StatefulSets Overview

### 5. StatefulSets for Database Replication

### 6. Demo Scaling out a Mongo Database

## 29. Continuous Deployment on a Kubernetes Cluster

### 1. Introducing CICD

### 2. Establishing a GitHub organization

### 3. Setting up a Basic Jenkins System

### 4. Defining a Pipeline

### 5. Running a Multibranch Pipeline

### 6. Reviewing Builds

### 7. Organization Pipelines

### 8. Continuous Deployment into a Cluster

## 30. Goodbye!

### 1. Goodbye!

### 2. Bonus Lecture links to other courses.html