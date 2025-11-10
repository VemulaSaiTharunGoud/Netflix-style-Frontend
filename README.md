# 🎬 Netflix-Style Frontend — Deployed on Kubernetes

This is a **Netflix-style frontend web application** built with **React.js**.  
It provides a clean, responsive, and modern UI inspired by Netflix’s design — showcasing movies, series, and a simple registration interface.

> ⚠️ Note: This is a **frontend-only deployment** for demonstration purposes — it does **not** include a backend or database connection.

## 🚀 Live Demo
**Deployed Link:**  
👉 [http://3.12.152.209:30080](http://3.12.152.209:30080)

This link points to the live frontend served via **Kubernetes NodePort** on an AWS EC2 instance.

<img width="1919" height="923" alt="image" src="https://github.com/user-attachments/assets/1e4704a2-800c-4e34-8ca2-428ecb8ef9bb" />
*(Screenshot of deployed frontend UI running on K8s)*

## 🧱 Tech Stack
| Layer | Technology |
|-------|-------------|
| Frontend | React.js, HTML5, CSS3 |
| Containerization | Docker |
| Orchestration | Kubernetes (MicroK8s single-node cluster) |
| Cloud | AWS EC2 (Ubuntu Server) |

## ⚙️ Deployment Overview
This frontend was containerized and deployed on a **single-node Kubernetes cluster** running on an AWS EC2 Ubuntu server.

### 🧩 Deployment Steps Summary
1. **Cloned** the open-source Netflix-style UI from GitHub.  
2. **Updated Dockerfile** to use Node 18 for Vite build compatibility.  
3. **Built Docker image** and pushed (optional) to Docker Hub.  
4. **Created Kubernetes manifests** (`Deployment` + `Service`) with NodePort (30080).  
5. **Deployed on EC2** using MicroK8s and verified the live URL.  
6. **Exposed Service** via EC2 public IP & security group rule for port 30080.

### 🐳 Dockerfile (Simplified)
```dockerfile
FROM node:18 AS build
WORKDIR /app
COPY . .
RUN npm install && npm run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 3000





