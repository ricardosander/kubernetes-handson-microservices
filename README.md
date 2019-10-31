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

A pod is the most basic concept of Kubernetes. A pod is kind like a wrapper to a container. For each cointainer we would have when using Docker we will have a pod on Kubernetes.
Inside a pod we could have - alongside with the microservice, a helper or sidecar cointainer like a agent for logging, for example.
We will NEVER have more than one microservice per pod.

Pods are not visible outside Kubernetes's cluster.

API documentation for pods : https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.16/#pod-v1-core

kubectl pod commands :
- kubectl describe pod pod-name -> give all information about the pod (including historical events)
- kubectl exec pod-name command -> execute a command into a pod

## kubectl commands

- kubectl get all -> show everything defined on Kubernetes's cluster
- kubectl apply -f filename.yaml -> apply Kubernetes definitions from a file (create pods, services, etc)