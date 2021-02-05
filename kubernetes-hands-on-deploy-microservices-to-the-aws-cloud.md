

## 1. Introduction
### 1. Introduction to Kubernetes Microservices course
### 1.2 K8S Command Reference.pdf.pdf



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
### 2. (Windows 10 Professional Only) Setting up Hyper-V
### 3. Installing kubectl and minikube
### 4. Troubleshooting Minikube


## 4. (optional) Docker Quickstart
### 1. Docker Overview
### 2. Docker Containers vs Images
### 3. Running Containers from DockerHub
## 5. Kubernetes Pods
### 1. Pods Overview
### 2. Writing a Pod
### 3. Running a Pod
## 6. Services in Kubernetes
### 1. Services
### 2. NodePort and ClusterIP
### 3. Pod Selection with Labels
## 7. Exercise Deploy ActiveMQ as a Pod and Service to Kubernetes
### 1. Exercise Deploy ActiveMQ as a Pod and Service
### 1.2 K8S-Command-Reference.pdf.pdf
## 8. Kubernetes ReplicaSets
### 1. ReplicaSets
### 2. Writing a ReplicaSet
### 3. Applying a ReplicaSet to Kubernetes
## 9. Kubernetes Deployments
### 1. Deployments Overview
### 2. Managing Rollouts



## 10. Networking and Service Discovery

### 1. Networking Overview in Kubernetes

### 2. Namespaces - kube-system

### 3. Accessing MySQL from a Pod

### 4. Cygwin extra - fixing the terminal with winpty

### 5. Service Discovery

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