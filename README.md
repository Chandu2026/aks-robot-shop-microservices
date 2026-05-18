# aks-robot-shop-microservices
Deployed a microservices-based ecommerce application on Azure Kubernetes Service (AKS) using Kubernetes, Helm, Docker, Redis, RabbitMQ, and MySQL.
# AKS Robot Shop Microservices Deployment

## Project Overview

This project demonstrates the deployment of Stan's Robot Shop microservices application on Azure Kubernetes Service (AKS) using Kubernetes and Helm.

The application consists of multiple microservices communicating with each other inside a Kubernetes cluster. The deployment includes backend services such as Redis, RabbitMQ, and MySQL along with frontend and API services.

---

## Technologies Used

- Azure Kubernetes Service (AKS)
- Kubernetes
- Helm
- Docker
- Azure CLI
- Redis
- RabbitMQ
- MySQL
- Azure Application Gateway / LoadBalancer
- Linux

---

## Architecture

Internet  
↓  
Ingress / LoadBalancer  
↓  
Web Service  
↓  
Microservices  
(cart, catalogue, user, dispatch, payment)  
↓  
Redis / RabbitMQ / MySQL  

---

## AKS Cluster Configuration

- Region: Central India
- Kubernetes Version: 1.34.6
- Node Pool: 2 Nodes
- VM Size: D2as_v5
- Network: Azure CNI Overlay

---

## Deployment Steps

### Connect to AKS Cluster

```bash
az aks get-credentials --resource-group ecommerce-demo --name three-tier
```

### Create Namespace

```bash
kubectl create namespace robot-shop
```

### Deploy Application Using Helm

```bash
helm install robot-shop ./ -n robot-shop
```

### Verify Pods

```bash
kubectl get pods -n robot-shop
```

### Scale Node Pool

```bash
az aks nodepool scale \
--resource-group ecommerce-demo \
--cluster-name three-tier \
--name agentpool \
--node-count 2
```

---

## Challenges Faced

- AKS quota limitations
- Pending pods due to insufficient memory
- 502 Bad Gateway issues
- Application Gateway ingress troubleshooting
- Backend database connectivity issues
- Resource allocation and scheduling problems

---

## Solutions Implemented

- Increased AKS node count from 1 to 2
- Monitored pod scheduling using kubectl
- Verified service communication between microservices
- Debugged Kubernetes events and pod logs
- Configured ingress and LoadBalancer networking

---

## Screenshots

### AKS Cluster
<img width="1912" height="947" alt="image" src="https://github.com/user-attachments/assets/5026516c-8b5c-47c5-ad51-eb1395f4ffba" />

### Kubernetes Pods
<img width="720" height="232" alt="image" src="https://github.com/user-attachments/assets/0b08bd56-d9e0-4883-a34e-cb44825d03da" />

### Robot Shop Application
<img width="1871" height="935" alt="image" src="https://github.com/user-attachments/assets/c06dd7a6-a043-4b1a-becf-019fc313f1ef" />


### Azure Portal AKS Overview
<img width="1886" height="957" alt="image" src="https://github.com/user-attachments/assets/43bfb8cf-7661-4e63-a73a-5b81ec95cbf4" />



---

## Learning Outcomes

- Kubernetes pod scheduling
- Helm deployments
- AKS scaling
- Microservices architecture
- Kubernetes networking and ingress
- Troubleshooting Kubernetes workloads
- Azure cloud infrastructure management

---

## Future Improvements

- CI/CD using GitHub Actions
- Monitoring with Prometheus and Grafana
- Infrastructure as Code using Terraform
- GitOps with ArgoCD

---

# Note

This project was implemented for learning and hands-on practice purposes by following DevOps/Kubernetes learning resources and tutorials.

I personally configured the CI/CD workflow, worked on troubleshooting issues, deployed the application on AKS, and integrated ArgoCD for Continuous Delivery to improve my practical DevOps skills.

GitHub:https://github.com/Chandu2026/aks-robot-shop-microservices
LinkedIn:https://www.linkedin.com/in/chandra-sekhar-chilakapati-81024b383/
