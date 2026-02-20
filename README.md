

# 🚀 DevOps Full CI/CD Pipeline Project

## 📌 Project Overview

This project demonstrates a complete end-to-end DevOps pipeline:

Developer Push → GitHub Actions CI → Docker Build → DockerHub Push → Kubernetes Deployment → Monitoring with Prometheus

The application is a Python Flask app containerized using Docker, deployed to Kubernetes, and monitored using Prometheus metrics.

This project showcases real-world DevOps practices including CI/CD, containerization, orchestration, and monitoring.

---

# 🛠 Tech Stack

- Python (Flask)
- Prometheus Client
- Docker
- DockerHub
- GitHub Actions (CI/CD)
- Kubernetes (Minikube)
- kubectl

---

# 🏗 Architecture Flow

1. Developer pushes code to GitHub
2. GitHub Actions triggers CI pipeline
3. Docker image is built automatically
4. Image is pushed to DockerHub
5. Kubernetes pulls the image
6. Deployment creates replicas
7. Service exposes application
8. Prometheus scrapes application metrics

---

# 📂 Project Structure

```
devops-full-pipeline-project/
│
├── app.py
├── requirements.txt
├── Dockerfile
├── .dockerignore
├── .gitignore
│
├── k8s/
│   ├── namespace.yaml
│   ├── deployment.yaml
│   ├── service.yaml
│
├── monitoring/
│   └── prometheus.yaml
│
└── .github/
    └── workflows/
        └── ci-cd.yml
```

---

# ⚙️ Step 1: Clone Repository

```
git clone https://github.com/<your-username>/devops-full-pipeline-project.git
cd devops-full-pipeline-project
```

---

# 🐳 Step 2: Test Application Locally

### Build Docker Image

```
docker build -t <your-dockerhub-username>/devops-full-pipeline .
```

### Run Container

```
docker run -p 5000:5000 <your-dockerhub-username>/devops-full-pipeline
```

Open in browser:

```
http://localhost:5000
http://localhost:5000/metrics
```

If working, stop container (Ctrl+C).

---

# 📦 Step 3: Push Docker Image to DockerHub

Login first:

```
docker login
```

Push image:

```
docker push <your-dockerhub-username>/devops-full-pipeline
```

---

# ☸️ Step 4: Start Kubernetes (Minikube)

Start cluster:

```
minikube start
```

Check nodes:

```
kubectl get nodes
```

---

# 🚀 Step 5: Deploy to Kubernetes

Apply namespace:

```
kubectl apply -f k8s/namespace.yaml
```

Deploy application:

```
kubectl apply -f k8s/deployment.yaml
```

Create service:

```
kubectl apply -f k8s/service.yaml
```

Check pods:

```
kubectl get pods -n devops
```

Check service:

```
kubectl get svc -n devops
```

---

# 🌐 Step 6: Access Application

```
minikube service flask-service -n devops
```

Browser will open automatically.

Refresh page multiple times to generate metrics.

---

# 📊 Step 7: Monitoring (Prometheus Configuration)

The application exposes metrics at:

```
/metrics
```

Prometheus configuration file:

```
monitoring/prometheus.yaml
```

This file tells Prometheus to scrape the Flask service inside Kubernetes.

To extend this project, install Prometheus and Grafana inside your cluster.

---

# 🔄 Step 8: GitHub Actions CI/CD Setup

## Add GitHub Secrets

Go to:

Repository → Settings → Secrets and variables → Actions

Add:

Name: DOCKER_USERNAME  
Value: Your DockerHub username  

Name: DOCKER_PASSWORD  
Value: DockerHub Access Token (recommended)

---

## Push Code to Trigger CI

```
git add .
git commit -m "Initial Full DevOps Pipeline"
git push origin main
```

Go to:

GitHub → Actions Tab

You will see:

- Docker image builds automatically
- Image pushes to DockerHub

---

# 📈 Scaling the Application

Increase replicas:

```
kubectl scale deployment flask-app --replicas=4 -n devops
```

Verify:

```
kubectl get pods -n devops
```

---

# 🧠 DevOps Concepts Demonstrated

- Continuous Integration (CI)
- Containerization (Docker)
- Container Registry (DockerHub)
- Kubernetes Deployments
- ReplicaSets
- Services (NodePort)
- Namespace isolation
- Metrics exposure
- Monitoring fundamentals
- Automated image build pipeline

---

# 🏆 Resume Description

Implemented an end-to-end DevOps pipeline with GitHub Actions, Docker, and Kubernetes. Automated Docker image builds and deployment, configured replica scaling, and exposed application metrics for Prometheus monitoring.

---

# 🔥 Future Improvements

- Add Helm charts
- Deploy to AWS EKS
- Add Grafana dashboards
- Implement Continuous Deployment (CD) to auto-deploy to Kubernetes
- Add Terraform for infrastructure provisioning

---

# ✅ Requirements

- Docker installed
- Minikube installed
- kubectl installed
- GitHub repository
- DockerHub account

---

# 🎯 Final Result

You now have a production-style DevOps pipeline including:

✔ CI/CD automation  
✔ Docker containerization  
✔ Kubernetes orchestration  
✔ Monitoring ready architecture  

This project is beyond basic fresher level and demonstrates strong DevOps fundamentals.

---
