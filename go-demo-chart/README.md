# Demo Go App Deployment using Helm Charts

#### This is a simple helm chart that deploys a Go application to a Kubernetes cluster. It also enables NodePort service to access the application from outside the cluster.

## Prerequisites

1. Docker
2. Minikube (or any other Kubernetes cluster)
3. Helm

## Steps to deploy the application

1. [Clone the repository](#1-clone-the-repository)
2. [Build the docker image](#2-build-the-docker-image)
3. [Push the docker image to a docker registry](#3-push-the-docker-image-to-a-docker-registry)
4. [Create the Helm Chart](#4-create-the-helm-chart)
5. [Deploy the helm chart](#5-deploy-the-helm-chart)
6. [Access the application](#6-access-the-application)
7. [Clean up](#7-clean-up)

### 1. Clone the repository

```bash
git clone git@github.com:Dev-Destructor/helm_charts.git
```

### 2. Build the docker image

```bash
cd go-demo-chart/go_app
docker build -t <docker-username>/go_app:v1 .
```

### 3. Push the docker image to a docker registry

```bash
docker push <docker-username>/go_app:v1
```

### 4. Create the helm chart

#### Note: Change the image name and tag in the values.yaml file

```bash
cd go-demo-chart/chart
helm package .
```

### 5. Deploy the helm chart

```bash
helm install <deployment-version> <chart-package-name>
```

### 6. Access the application

##### Get the NodePort of the service

```bash
kubectl get services
```

##### Access the application using the NodePort

```bash
curl <node-ip>:<node-port>
```

### 7. Clean up

```bash
helm uninstall <deployment-version>
```
