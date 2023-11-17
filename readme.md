# Deploying Simple App to Azure using Docker and AKS

This guide outlines the steps to deploy a Dockerized application to Azure Container Registry (ACR) and Azure Kubernetes Service (AKS).

## Prerequisites

Before starting, ensure you have the following tools installed and configured:

- Docker
- Azure CLI
- Kubernetes CLI (`kubectl`)
- Azure Kubernetes Service (AKS) cluster

## Step 1: Build Docker Image

```bash
docker build -f simple-app:1.0 .
```

This command builds a Docker image using the specified Dockerfile (`simple-app:1.0`). Make sure to run this command in the root directory of your application.

## Step 2: Login to Azure

```bash
az login --name mrdev
```

Make sure you are logged in to the correct Azure subscription.

## Step 3: Tag and Push Docker Image to Azure Container Registry

```bash
docker tag simple-app:1.0 mrdev.azurecr.io/simple-app:1.0
docker push mrdev.azurecr.io/simple-app:1.0
```

Tag the Docker image with your Azure Container Registry (ACR) information and push it to ACR.

## Step 4: Install AKS CLI (if not installed)

```bash
az aks install-cli
```

Ensure the AKS CLI is installed on your machine.

## Step 5: Get AKS Credentials

```bash
az aks get-credentials --resource-group az-learning-rg --name simple-app-aks
```

This command retrieves the AKS cluster credentials, allowing you to interact with the cluster using `kubectl`.

## Step 6: Deploy Application to AKS

```bash
kubectl apply -f deployment.yaml
```

Replace `deployment.yaml` with the actual name of your Kubernetes configuration file. This file defines how your application should run in the Kubernetes cluster.

Congratulations! Your application is now deployed and running in your Azure Kubernetes Service.

```

Make sure to replace `deployment.yaml` with the actual name of your Kubernetes configuration file, and ensure that the file exists in your project directory.
