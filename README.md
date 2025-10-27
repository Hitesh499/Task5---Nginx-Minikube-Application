# 🚀 Minikube NGINX Deployment Project

This repository contains the configuration files and documentation for **Task 5: Building a Local Kubernetes Cluster with Minikube**.

The objective of this project was to establish a functional, single-node Kubernetes cluster on a local machine (using Docker as the driver) and practice the fundamental operations of deployment, service exposure, and scaling using `kubectl`.

---

## 🛠️ Prerequisites

To run this project, you must have the following tools installed on your system:

1.  **Docker:** Used as the container runtime and the driver for Minikube.
2.  **Minikube:** The tool used to run a local Kubernetes cluster.
3.  **kubectl:** The command-line interface for interacting with the Kubernetes cluster.

---

## 💡 How to Run This Application

Follow these steps in your terminal (preferably the VS Code integrated terminal) to recreate the environment and deploy the NGINX application.

## 1. Start the Minikube Cluster

This command boots up the local Kubernetes environment inside a Docker container:
minikube start --driver=docker

## 2. Verify the Cluster
Check that the Kubernetes node is running and ready:
kubectl get nodes

## 3. Deploy the Application
This deployment specifies that we want 2 replicas of the standard nginx:latest image.
### Apply the deployment defined in deployment.yml
kubectl apply -f deployment.yml

### Verify the two pods are running
kubectl get pods

## 4. Expose the Application
The service.yaml file creates a NodePort Service to expose the application outside the cluster.
### Apply the service definition
kubectl apply -f service.yml

### Check the service status
kubectl get services

### To access the app in your browser, run:
minikube service nginx-service --url

## 5. Scale the Application
We practiced manual scaling by increasing the number of running NGINX pods from 2 to 5.
### Scale the deployment to 5 replicas
kubectl scale deployment nginx-deployment --replicas=5

### Verify all five pods are running
kubectl get pods

## 6. Cleanup
Once you are done experimenting, delete the Minikube cluster to free up system resources:
minikube delete