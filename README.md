# kubernetes-handson-microservices
This is a projects for developing activities related to "Kubernetes Hands On - Deploy Microservices to the AWS Clound" Udemy Course.

## Section 1 - Introduction

## Section 2 - Welcome to Kubernetes

## Section 3 - Installing Minikube for local Kubernetes Development

Minikube commands :
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

kubectl pod commands :
- kubectl describe pod pod-name -> give all information about the pod (including historical events)
- kubectl exec pod-name command -> execute a command into a pod

## Section 6 - Services

Services are long live entities with IP address and stable fixed pods. A service can be attach to pods. 
A service can expose Kubernets's cluster pods, so we can access a webapp pod from a browser through a service. 

We use service's selector to select/attach pods by pod's labels. The selector defines which pods are going to be represented by the service. The service becomes a network endpoint for either other services or external users (eg browser).

### Types of Services
- ClusterIP : service accessble only inside the cluster (eg regular microservices) 
- NodePort : expose pod through the node. We can define a nodePort (ports section) for wich the service will be exposed (only ports above 30000 are allowed by Kubernets).
- LoadBalancer : doesn't support local running

API documentation for services : https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.16/#service-v1-core

## kubectl commands

- kubectl get all -> show everything defined on Kubernetes's cluster
- kubectl apply -f filename.yaml -> apply Kubernetes definitions from a file (create pods, services, etc)