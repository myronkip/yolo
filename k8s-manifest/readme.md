# Kubernetes GKE Deployment for E-commerce Application

This repository contains the Kubernetes manifests and configurations required to deploy an e-commerce application on **Google Kubernetes Engine (GKE)**. The deployment includes frontend and backend services, with a focus on using **StatefulSets** for persistent storage and exposing services via **LoadBalancer** for external access.

## Table of Contents
- [Deployment Architecture](#deployment-architecture)
- [Requirements](#requirements)
- [Setup and Deployment](#setup-and-deployment)
- [Exposing the Application](#exposing-the-application)
- [Accessing the Application](#accessing-the-application)
- [Git Workflow](#git-workflow)

## Deployment Architecture
- **Frontend**: Deployed as a stateless service.
- **Backend**: Deployed with a database (MongoDB) using a **StatefulSet** for persistent storage.
- **LoadBalancer**: Used to expose the frontend service to external traffic.

## Requirements
- A Google Cloud Platform account with **Google Kubernetes Engine (GKE)** enabled.
- `kubectl` configured to interact with your GKE cluster.
- `gcloud` CLI installed for managing GKE.
- Docker images available on DockerHub.

## Setup and Deployment

### 1. Clone the repository

```bash
git clone https://github.com/myronkip/yolo.git
checkout IP4



kubectl apply -f mongo-statefulset.yaml
kubectl apply -f mongo-services.yaml
kubectl apply -f backend-deployment.yaml
kubectl apply -f backend-service.yaml
kubectl aplly -f frontend-deployment.yaml
kubectl apply -f frontend-service.yaml

## Verify pods,services &deployment are running
kubectl get all

## To get external IP For the LoadBalancer

kubectl get services

## Application Url
http://34.55.81.102:80