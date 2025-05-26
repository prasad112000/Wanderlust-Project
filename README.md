# 🌍 Wanderlust – End-to-End DevSecOps + GitOps Project on AWS

![Wanderlust](https://github.com/user-attachments/assets/1d05c851-1fcc-4e38-a2d6-34bd307fcf6c)

## 📌 Overview

Wanderlust is a cloud-native travel blog web application built using the **MERN stack (MongoDB, Express.js, React.js, Node.js)** and deployed using a full **DevSecOps and GitOps pipeline on AWS**. This project demonstrates real-world implementation of CI/CD, container security, Git-based deployments, infrastructure as code, and monitoring on AWS EKS.

![DevSecOps-GitOps Flowchart](https://github.com/user-attachments/assets/f2e798cc-3ad4-45b8-99b6-29d30d7c5a89)

---

## 🚀 Key Highlights

* Built and deployed a scalable MERN application on AWS EKS.
* Implemented CI/CD using Jenkins, with integrated code quality and security checks.
* Integrated **Trivy**, **SonarQube**, and **OWASP Dependency-Check** for DevSecOps.
* Managed Kubernetes deployments using **Helm** and **GitOps via ArgoCD**.
* Provisioned infrastructure using **eksctl** and monitored workloads using **Prometheus + Grafana**.

---

## 🧰 Tech Stack & Tools

### 🖥 Application Stack

* Frontend: React.js
* Backend: Node.js + Express.js
* Database: MongoDB

### ⚙ DevOps & Security Tools

* Docker – Containerization
* Jenkins – CI/CD automation (CI & CD Pipelines)
* Trivy – Docker image vulnerability scanner
* SonarQube – Static code analysis
* OWASP Dependency-Check – Scan open-source dependencies
* Helm – Kubernetes packaging and deployment
* ArgoCD – GitOps-based continuous delivery
* eksctl – EKS cluster & node provisioning
* AWS CLI – AWS resource configuration
* Prometheus + Grafana – Monitoring & alerting

---

## ☸️ AWS Infrastructure Setup

* **EC2 (t2.large)** as Jenkins master (with Docker, Trivy, SonarQube, AWS CLI, kubectl, eksctl)
* Created EKS Cluster: `wanderlust` in `us-east-2` region
* Node group with 2x t2.large instances and 29 GB volume
* Security Group Rules Opened:

  * 22 (SSH), 80 (HTTP), 443 (HTTPS), 6443 (K8s API), 6379 (Redis), 30000–32767 (NodePorts)
  * 25 (SMTP), 465 (SMTPS), 31000 (Frontend NodePort), 31100 (Backend NodePort)

---

## 🔄 CI/CD Pipeline Breakdown

### ✅ CI Pipeline (Jenkins)

1. Validate build parameters
2. Clean workspace
3. Checkout code from GitHub
4. Scan with Trivy
5. Dependency check via OWASP
6. SonarQube analysis & quality gate check
7. Inject instance ID to frontend/backend scripts
8. Build & push Docker images to DockerHub
9. Trigger CD pipeline

### ✅ CD Pipeline (Jenkins)

1. Clean workspace and pull latest code
2. Update image tags in Kubernetes manifests
3. Git push changes to GitHub
4. ArgoCD detects changes and syncs deployments
5. Email notifications sent via Gmail integration

> 🔁 Jenkins shared library used: [Jenkins\_SharedLib](https://github.com/prasad112000/Jenkins_SharedLib.git)

---

## 🔧 ArgoCD Setup & GitOps

* Installed in `argocd` namespace via official manifest
* ArgoCD CLI installed and server service patched to NodePort
* Cluster added using `argocd cluster add` with context
* Application created with:

  * Name: `wanderlust`, Namespace: `wanderlust`
  * Sync Policy: auto-sync, prune, self-heal, auto namespace create
  * Repo: [Wanderlust-Project](https://github.com/prasad112000/Wanderlust-Project-.git), Path: `kubernetes`, Branch: `main`

---

## 📊 Monitoring with Prometheus & Grafana

* Installed using `kube-prometheus-stack` via Helm
* Exposed Prometheus and Grafana via NodePorts
* Accessed Prometheus and Grafana dashboards externally
* Fetched Grafana admin password from Kubernetes secret
* Dashboards used to monitor pods, nodes, network packets, and targets

---

## 📸 Screenshots

### Frontend UI

![frontend-ui](https://github.com/user-attachments/assets/5e6b7584-8383-43f2-b4ae-a5917c8ba0ac)

### Backend API

![Backend API Access](https://github.com/user-attachments/assets/f5f5d28c-f6cb-432c-871d-48cbcc0ab4e8)

### ArgoCD Deployment

![Argocd-app-connect](https://github.com/user-attachments/assets/f2211ea2-829a-4f0e-bb2d-00023cdf4c82)

https://github.com/user-attachments/assets/eb769c7f-678d-4686-9d89-f261077bbb26

![argocd-tree-view](https://github.com/user-attachments/assets/f3678f6d-c6ad-48e6-9012-c25cca7d9b5b)

### DockerHub Push

![dockerhub](https://github.com/user-attachments/assets/b2106220-ca93-4bb4-9c08-cb1ce09569a2)

### Grafana Monitoring

![Grafana Dashboard](https://github.com/user-attachments/assets/6879339f-3cd8-498b-bf41-8cde0b32e0f9)

### Prometheus Targets

![Prometheus ](https://github.com/user-attachments/assets/2175d24c-6112-4cfa-81d9-04cd921f8e96)

### SonarQube Report

![SonarQube](https://github.com/user-attachments/assets/b8a6df4b-f310-444e-b008-ca9bbc002bfb)

### Gmail Message 

![Gmail](https://github.com/user-attachments/assets/80910b6d-4027-41a2-b827-14b8174e091e)

### Project Run Sucessfully 

![Project Completed Succesfully ](https://github.com/user-attachments/assets/5bf61da6-fdf6-4ba0-bad6-f77adb7cb26f)

---

## 📁 Repository Structure

```
Wanderlust-Project-
├── frontend/                # React app
├── backend/                 # Express API
├── kubernetes/              # K8s manifests (frontend, backend)
├── Automations/             # Scripts to inject env/instance data
├── Jenkinsfile-CI           # CI pipeline config
├── Jenkinsfile-CD           # CD pipeline config
└── README.md                # Project documentation
```

---

## 👨‍💻 Author

**Prasad Vinod Pardeshi**
[LinkedIn](https://www.linkedin.com/in/prasad-pardeshi11/) • [GitHub](https://github.com/prasad112000)
📧 [pardeshiprasad42@gmail.com](mailto:pardeshiprasad42@gmail.com)

---

