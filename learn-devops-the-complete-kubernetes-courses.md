

## 001 Course Introduction
### 001 Course Introduction
### 002 Support and Course Materials
### 003 Procedure Document.html

#### Kubernetes Procedure Document

#### Github repository [Read this first]

- Download all the course material from: https://github.com/wardviaene/kubernetes-course

#### Questions?

- Send me a message
- Use Q&A
- Join our facebook group: https://www.facebook.com/groups/840062592768074/

#### Download Kubectl

- Linux: https://storage.googleapis.com/kubernetes-release/release/v1.6.1/bin/linux/amd64/kubectl
- MacOS: https://storage.googleapis.com/kubernetes-release/release/v1.6.1/bin/darwin/amd64/kubectl
- Windows:
  https://github.com/eirslett/kubectl-windows/releases/download/v1.6.3/kubectl.exe

#### Minikube

- Project URL: https://github.com/kubernetes/minikube
- Latest Release and download instructions: https://github.com/kubernetes/minikube/releases
- VirtualBox: http://www.virtualbox.org

#### Minikube on windows:

- Download the latest minikube-version.exe
- Rename the file to minikube.exe and put it in C:\minikube
- Open a cmd (search for the app cmd or powershell)
- Run: cd C:\minikube and enter minikube start

#### Test your cluster commands

Make sure your cluster is running, you can check with **minikube status\**.\****

If your cluster is not running, enter **minikube start** first.

kubectl run hello-minikube --image=gcr.io/google_containers/echoserver:1.4 --port=8080
kubectl expose deployment hello-minikube --type=NodePort

minikube service hello-minikube --url

<open a browser and go to that url>

#### Kops

#### Project URL

- https://github.com/kubernetes/kops

#### Free DNS Service

- Sign up at http://freedns.afraid.org/

- - Choose for subdomain hosting
  - Enter the AWS nameservers given to you in route53 as nameservers for the subdomain

- http://www.dot.tk/ provides a free .tk domain name you can use and you can point it to the amazon AWS nameservers

\###h2

- Namecheap.com often has promotions for tlds like .co for just a couple of bucks





Cluster Commandskops create cluster --name=kubernetes.newtech.academy --state=s3://kops-state-b429b --zones=eu-west-1a --node-count=2 --node-size=t2.micro --master-size=t2.micro --dns-zone=kubernetes.newtech.academykops update cluster kubernetes.newtech.academy --yes --state=s3://kops-state-b429bkops delete cluster --name kubernetes.newtech.academy --state=s3://kops-state-b429bkops delete cluster --name kubernetes.newtech.academy --state=s3://kops-state-b429b --yesKubernetes from scratch







- You can setup your cluster manually from scratch

- If youre planning to deploy on AWS / Google / Azure, use the tools that are fit for these platforms

- If you have an unsupported cloud platform, and you still want Kubernetes, you can install it manually

- 

  CoreOS + Kubernetes: ###a href="https://coreos.com/kubernetes/docs/latest/getting-started.html">https://coreos.com/kubernetes/docs/latest/getting-started.html

#### Docker

- You can download Docker Engine for:

- - Windows:[ https://docs.docker.com/engine/installation/windows/](https://docs.docker.com/engine/installation/windows/)
  - MacOS:[ https://docs.docker.com/engine/installation/mac/](https://docs.docker.com/engine/installation/mac/)
  - Linux:[ https://docs.docker.com/engine/installation/linux/](https://docs.docker.com/engine/installation/linux/)

#### DevOps box

- Virtualbox: http://www.virtualbox.org

- Vagrant: http://www.vagrantup.com

- DevOps box: https://github.com/wardviaene/devops-box

- Launch commands (in terminal / cmd / powershell):

- - cd devops-box/
  - vagrant up

- Launch commands for a plain ubuntu box:

- - mkdir ubuntu
  - vagrant init ubuntu/xenial64
  - vagrant up

#### Docker commands

| **Description**     | **Command**                                  |
| ------------------- | -------------------------------------------- |
| Build image         | docker build .                               |
| Build & Tag         | docker build -t wardviaene/k8s-demo:latest . |
| Tag image           | docker tag imageid wardviaene/k8s-demo       |
| Push image          | docker push wardviaene/k8s-demo              |
| List images         | docker images                                |
| List all containers | docker ps -a                                 |

#### Kubernetes commands

| **Command**                                                  | **Description**                                         |
| ------------------------------------------------------------ | ------------------------------------------------------- |
| kubectl get pod                                              | Get information about all running pods                  |
| kubectl describe pod <pod>                                   | Describe one pod                                        |
| kubectl expose pod <pod> --port=444--name=frontend           | Expose the port of a pod (creates a new service)        |
| kubectl port-forward <pod> 8080                              | Port forward the exposed pod port to your local machine |
| kubectl attach <podname> -i                                  | Attach to the pod                                       |
| kubectl exec <pod> -- command                                | Execute a command on the pod                            |
| kubectl label pods <pod> mylabel=awesome                     | Add a new label to a pod                                |
| kubectl run -i --tty busybox --image=busybox--restart=Never -- sh | Run a shell in a pod - very useful for debugging        |
| kubectl get deployments                                      | Get information on current deployments                  |
| kubectl get rs                                               | Get information about the replica sets                  |
| kubectl get pods --show-labels                               | get pods, and also show labels attached to those pods   |
| kubectl rollout status deployment/helloworld-deployment      | Get deployment status                                   |
| kubectl set image deployment/helloworld-deploymentk8s-demo=k8s-demo:2 | Run k8s-demo with the image label version 2             |
| kubectl edit deployment/helloworld-deployment                | Edit the deployment object                              |
| kubectl rollout status deployment/helloworld-deployment      | Get the status of the rollout                           |
| kubectl rollout history deployment/helloworld-deployment     | Get the rollout history                                 |
| kubectl rollout undo deployment/helloworld-deployment        | Rollback to previous version                            |
| kubectl rollout undo deployment/helloworld-deployment --to-revision=n | Rollback to any version version                         |

#### AWS Commands

- aws ec2 create-volume --size 10 --region us-east-1 --availability-zone us-east-1a --volume-type gp2

#### Certificates

- Creating a new key for a new user: openssl genrsa -out myuser.pem 2048
- Creating a certificate request: openssl req -new -key myuser.pem -out myuser-csr.pem -subj "/CN=myuser/O=myteam/"
- Creating a certificate: openssl x509 -req -in myuser-csr.pem -CA /path/to/kubernetes/ca.crt -CAkey /path/to/kubernetes/ca.key -CAcreateserial -out myuser.crt -days 10000

## 01 Introduction to Kubernetes
### 004 Kubernetes Introduction
### 005 Containers Introduction
### 006 Kubernetes Setup
### 007 Local Setup with minikube
### 008 Demo_ Minikube
### 009 Introduction to Kops
### 010 Demo_ Preparing kops install
### 011 Demo_ Preparing AWS for kops install
### 012 Demo_ Cluster setup on AWS using kops
### 013 Building docker containers
### 014 Demo_ Building docker containers
### 015 Docker Image Registry
### 016 Demo_ Pushing Docker Image
### 017 Running first app on Kubernetes
### 018 Demo_ Running first app on Kubernetes
### 019 Demo_ Useful commands
### 020 Service with LoadBalancer
### 021 Demo_ Service with AWS ELB LoadBalancer
## 02 Kubernetes Basics
### 022 Node Architecture
### 023 Replication Controller
### 024 Demo_ Replication Controller
### 025 Deployments
### 026 Demo_ Deployments
### 027 Services
### 028 Demo_ Services
### 029 Labels
### 030 Demo_ NodeSelector using Labels
### 031 Healthchecks
### 032 Demo_ Healthchecks
### 033 Secrets
### 034 Demo_ Credentials using Volumes
### 035 Demo_ Running Wordpress on Kubernetes
### 036 WebUI
### 037 Demo_ WebUI
## 03 Advanced Topics
### 038 Service Discovery
### 039 Demo_ Service Discovery
### 040 ConfigMap
### 041 Demo_ ConfigMap
### 042 Ingress Controller
### 043 Demo_ Ingress Controller
### 044 Volumes
### 045 Demo_ Volumes
### 046 Volumes Autoprovisioning
### 047 Demo_ Wordpress With Volumes
### 048 Pet Sets
### 049 Daemon Sets
### 050 Resource Usage Monitoring
### 051 Demo_ Resource Usage Monitoring
### 052 Autoscaling
### 053 Demo_ Autoscaling
## 04 Kubernetes Administration
### 054 The Kubernetes Master Services
### 055 Resource Quotas
### 056 Namespaces
### 057 Demo_ Namespace quotas
### 058 User Management
### 059 Demo_ Adding Users
### 060 Networking
### 061 Node Maintenance
### 062 Demo_ Node Maintenance
### 063 High Availability
### 064 Demo_ High Availability
## 05 Course Completion
### 065 Congratulations
### 066 Bonus Lecture_ Advanced Kubernetes Usage Course
