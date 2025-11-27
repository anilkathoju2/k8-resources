**Kubernetes & EKS Hands-On Guide**

This repository contains Kubernetes resource manifests and step-by-step commands for working with Amazon EKS, creating namespaces, deploying pods, executing into containers, and troubleshooting using common kubectl commands.

📌 Table of Contents

Creating an EKS Cluster

Verifying Cluster Nodes

Working With Namespaces

Deploying Pods

Listing Pods

Describing Pods

Executing Into Containers

Checking Resource Usage

Useful Commands Summary

**Create the cluster**
eksctl create cluster --config-file=eks.yaml
**🖥 Verifying Cluster Nodes**

**Check if worker nodes are active:**

kubectl get nodes

**📁 Working With Namespaces**
List all namespaces
kubectl get namespace

**Create a new namespace**
kubectl create namespace <namespace>

**Apply namespace from YAML**
kubectl apply -f 00-namespace.yaml

**📦 Deploying Pods**

Apply a pod manifest:

kubectl apply -f 01-pod.yaml

**🟦 Listing Pods**
List pods in the default namespace
kubectl get pods


If you see:

No resources found in default namespace


It means no pods are deployed in the default namespace.

**List pods inside a specific namespace**
kubectl get pods -n <namespace>

🔎 Describing Pods
Describe a pod in the default namespace
kubectl describe pod frontend

Describe a pod in a custom namespace
kubectl describe pod frontend -n <project_name>

🛠 Executing Into Containers
Exec into a specific container inside a multi-container pod

nginx container

kubectl exec -it multi-container -c nginx -- bash


redis container

kubectl exec -it multi-container -c redis -- bash

Exec into a single-container pod
kubectl exec -it pod -- bash

📊 Checking Resource Usage

Requires Metrics Server installed.

List CPU and memory usage of pods
kubectl top pods

**✅ Useful Commands Summary**
**Action	Command**

**create EKS cluster	eksctl create cluster --config-file=eks.yaml**

**List nodes	kubectl get nodes**

**List namespaces	kubectl get namespace**

**Create namespace	kubectl create namespace <namespace>**

**Apply namespace	kubectl apply -f 00-namespace.yaml**

**Apply pod	kubectl apply -f 01-pod.yaml**

**List pods (default)	kubectl get pods**

**List pods (namespace)	kubectl get pods -n <namespace>**

**Exec into nginx container	kubectl exec -it multi-container -c nginx -- bash**

**Exec into redis container	kubectl exec -it multi-container -c redis -- bash**

**Exec into pod	kubectl exec -it pod -- bash**

**Describe pod	kubectl describe pod <pod>**

**Describe pod in namespace	kubectl describe pod <pod> -n <namespace>**

**Pod resource usage	kubectl top pods**

📚 Additional Notes

Ensure your AWS credentials are configured before creating the cluster.

The Metrics Server must be installed for kubectl top to work.

Manifests in this repository can be applied directly using kubectl apply -f <file>.