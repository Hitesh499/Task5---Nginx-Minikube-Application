# 🚀 Minikube NGINX Deployment Project

This repository contains configuration files and documentation for **Task 5: Building a Local Kubernetes Cluster with Minikube**.

The goal of this project is to **set up a local, single-node Kubernetes cluster** using **Minikube (with Docker as the driver)** and to perform key Kubernetes operations such as **deployment, service exposure, and scaling** using `kubectl`.

---

## 🧰 Prerequisites

Before running this project, ensure you have the following tools installed:

| Tool | Purpose |
|------|----------|
| 🐳 **Docker** | Acts as the container runtime and driver for Minikube |
| ☸️ **Minikube** | Runs a local single-node Kubernetes cluster |
| 💻 **kubectl** | Command-line tool to interact with the Kubernetes cluster |

---

## ⚙️ Setup & Deployment Guide

Follow the steps below to create the Minikube cluster and deploy the NGINX application.

### **1️⃣ Start the Minikube Cluster**

Start the local Kubernetes environment using Docker as the driver:
```bash
minikube start --driver=docker

### **2️⃣ Verify the Cluster**

Check that the Kubernetes node is running and ready:
```bash
kubectl get nodes

### **3️⃣ Deploy the NGINX Application**

This step deploys 2 replicas of the standard nginx:latest image.
Apply the deployment manifest:
```bash
kubectl apply -f deployment.yml

Verify that the pods are running:
```bash
kubectl get pods

### **4️⃣ Expose the Application**

The service.yml file defines a NodePort Service to expose NGINX outside the cluster.
Apply the service configuration:
```bash
kubectl apply -f service.yml

Check the service status:
```bash
kubectl get services

To access the app in your browser:
```bash
minikube service nginx-service --url

### **5️⃣ Scale the Deployment**

Increase the number of running NGINX pods from 2 to 5:
```bash
kubectl scale deployment nginx-deployment --replicas=5

Verify that all five pods are up and running:
```bash
kubectl get pods

### **6️⃣ Cleanup**

Once done experimenting, delete the Minikube cluster to free up resources:
```bash
minikube delete

🧩 Project Structure
├── deployment.yml # Kubernetes deployment configuration
├── service.yml # Kubernetes service configuration
├── Images/ # Folder containing project screenshots and visuals
└── README.md # Project documentation