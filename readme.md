# Kubernetes Demo API

This project demonstrates deploying a Node.js API to **Kubernetes** using **Minikube** and Docker.

---

## Table of Contents

* [Project Overview](#project-overview)
* [Prerequisites](#prerequisites)
* [Setup & Deployment](#setup--deployment)
* [Verify Deployment](#verify-deployment)
* [Project Structure](#project-structure)
* [Scripts](#scripts)
* [Kubernetes Concepts Used](#kubernetes-concepts-used)

---

## Project Overview

This project showcases how to:

* Containerize a Node.js application using Docker.
* Deploy the application to a local Kubernetes cluster (Minikube).
* Expose the app using a **NodePort** service.
* Use **readiness** and **liveness probes** to monitor pod health.

---

## Prerequisites

* Docker installed and running
* Minikube installed
* kubectl installed
* Node.js and npm

---

## Setup & Deployment

1. **Start Minikube**

   ```bash
   minikube start
   ```

2. **Build and deploy using the deploy script**

   ```bash
   npm run deploy
   ```

   This will:

   * Build the Docker image
   * Push it to Docker Hub
   * Apply Kubernetes manifests (Deployment & Service)
   * Show the pods and services

3. **Access the application**

   ```bash
   minikube service kubernetes-demo-api-service
   ```

   This opens the app in your browser.

---

## Verify Deployment

* Check nodes:

  ```bash
  kubectl get nodes
  ```
* Check cluster info:

  ```bash
  kubectl cluster-info
  ```
* Watch pods:

  ```bash
  kubectl get pods -w
  ```
* Check services:

  ```bash
  kubectl get services
  ```

---

## Project Structure

```
k8s/
 ├─ deployment.yaml   # Deployment manifest
 ├─ service.yaml      # Service manifest

deploy.sh             # Script to build, push, and deploy
package.json          # Contains deploy script
```

---

## Scripts

* **deploy**: Build Docker image, push to Docker Hub, apply Kubernetes manifests, and watch pods & services.

```bash
npm run deploy
```

* **deploy.sh**: Handles the deployment steps automatically.

---

## Kubernetes Concepts Used

* **Deployment**: Manages pods and replicas.
* **Service (NodePort)**: Exposes the application externally.
* **Readiness & Liveness Probes**: Ensure pods are healthy and ready to receive traffic.
* **Minikube**: Local Kubernetes cluster for development/testing.
* **Docker**: Containerizes the application for deployment.

---

## Notes

* Ensure your app listens on `0.0.0.0:3000` so Kubernetes can route traffic correctly.
* The deployment script assumes Docker Hub login credentials are already configured.
* Minikube may assign a different NodePort each time; use `minikube service` to get the correct URL.

---

**Author:** Habeebu Rahman CA
