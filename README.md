# kubernetes-handson-microservices
This is a projects for developing activities related to "Kubernetes Hands On - Deploy Microservices to the AWS Clound" Udemy Course.

## Section 1 - Introduction

## Section 2 - Welcome to Kubernetes

## Section 3 - Installing Minikube for local Kubernetes Development

### Minikube commands :
- minikube start -> starts minikube
- minikube stop  -> stops minikube
- minikube ip    -> retrieves minikube's IPm 

## Section 4 - Docker Quickstart

## Section 5 - Pods

"We treat pods like cattle, not like pets" - Richard Chesterwood

It means we do not care about the pod itself. Pods are created, destroy and restart very frequently and we usually do not handle pods by ourselfs.

A pod is the most basic concept of Kubernetes. A pod is kind like a wrapper to a container. For each cointainer we would have when using Docker we will have a pod on Kubernetes.
Inside a pod we could have - alongside with the microservice, a helper or sidecar cointainer like a agent for logging, for example.
We will NEVER have more than one microservice per pod.

Pods are not visible outside Kubernetes's cluster.

API documentation for pods : https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.16/#pod-v1-core

### kubectl pod commands :
- kubectl get pods -> list all pods
- kubectl get pods --show--labels -> list all pods and its labels
- kubectl get pods --show--labels -l label-name=label-value -> list all pods and its labels filtering by label
- kubectl describe pod pod-name -> give all information about the pod (including historical events)
- kubectl delete pod pod-name -> delete a pod by its name
- kubectl exec pod-name command -> execute a command into a pod

## Section 6 - Services

Services are long live entities with IP address and stable fixed pods. A service can be attach to pods. 
A service can expose Kubernets's cluster pods, so we can access a webapp pod from a browser through a service. 

We use service's selector to select/attach pods by pod's labels. The selector defines which pods are going to be represented by the service. The service becomes a network endpoint for either other services or external users (eg browser).

Labels and selector can be used to migrate versions, having 2 versions of the pod online and chaging the selection into the service definition. This is not the more efficient and elegant way to do it but it works. On later sections we have better ways to do this kind of migrations. 

### kubectl service commands :
- kubectl get services -> list all services
- kubectl describe service service-name -> give all information about the service, eg labels selected
- kubectl delete service service-name -> delete a service by its name

### Types of Services
- ClusterIP : service accessble only inside the cluster (eg regular microservices) 
- NodePort : expose pod through the node. We can define a nodePort (ports section) for wich the service will be exposed (only ports above 30000 are allowed by Kubernets).
- LoadBalancer : doesn't support local running

API documentation for services : https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.16/#service-v1-core

## Section 7 - Pod and Services Exercise

Creates a pod and a service to a ActiveMQ using richardchesterwood/k8s-fleetman-queue on release1. The container uses 8161 port and we want to expose port 30010 so we can access the message broker manager (admin/admin). 

## Section 8 - ReplicaSets

Even using Kubernetes with pods and services, we still have to manage it by ourselfs. If a pod stop working we have to manually start it again.

But with ReplicaSets, we define how many pods we want to still running and Kubernetes will do the managing for us. We don't need define the pod anymore, we define just a ReplicaSet, how many replicas of the pod we want and the  pod's template.

With ReplicaSets if any pod goes offline, one new one will be launch to always maintain the number of pods equals to the replicas from the ReplicaSet.

### kubectl replicaset commands :
- kubectl get replicaset -> list all replicaset
- kubectl describe replicaset replicaset-name -> give all information about the replicaset
- kubectl delete replicaset replicaset-name -> delete a replicaset by its name

API documentation for replicaset : 

## kubectl commands

- kubectl get all -> show everything defined on Kubernetes's cluster
- kubectl apply -f filename.yaml -> apply Kubernetes definitions from a file (create pods, services, etc)