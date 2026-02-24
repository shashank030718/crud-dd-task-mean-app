# 🚀 Full Stack MEAN Application with CI/CD & Cloud Deployment

## 📌 Project Overview

This project demonstrates the complete DevOps lifecycle of deploying a full-stack MEAN (MongoDB, Express, Angular, Node.js) application using:

- Docker & Docker Compose
- AWS EC2 (Ubuntu)
- GitHub Actions (CI/CD)
- Docker Hub
- Nginx Reverse Proxy

The application supports full CRUD functionality for managing tutorials and is deployed in a production-style architecture with automated build and deployment.

---

# 🏗 System Architecture
            Internet
                │
                ▼
          Nginx (Port 80)
                │
    ┌───────────┴───────────┐
    ▼                       ▼
    Frontend (Angular) Backend (Node.js)
    │
    ▼
    MongoDB



# 📦 Project Structure


crud-dd-task-mean-app/
│
├── backend/
│ ├── Dockerfile
│ └── application source code
│
├── frontend/
│ ├── Dockerfile
│ └── Angular source code
│
├── nginx/
│ └── default.conf
│
├── docker-compose.yml
│
├── .github/
│ └── workflows/
│ └── deploy.yml
│
└── README.md


---

# 🐳 Containerization

## Backend Dockerfile
Located in:

backend/Dockerfile


Builds Node.js application and exposes port 8080.

## Frontend Dockerfile
Located in:

frontend/Dockerfile


Builds Angular production build and serves via Nginx.

## Docker Compose Services

- mongodb
- backend
- frontend
- nginx

The services are networked internally using Docker bridge networking.

---

# ☁ Cloud Deployment (AWS EC2)

## EC2 Configuration

- OS: Ubuntu
- Instance Type: t3.micro
- Open Ports:
  - 22 (SSH)
  - 80 (HTTP)

Docker and Docker Compose installed manually.

Application deployed using:


docker-compose up -d


---

# 🔁 CI/CD Pipeline (GitHub Actions)

Workflow File:

.github/workflows/deploy.yml


## Pipeline Process

On every push to `main` branch:

1. Checkout code
2. Login to Docker Hub (using GitHub Secrets)
3. Build backend image
4. Build frontend image
5. Push images to Docker Hub
6. SSH into EC2 instance
7. Pull latest images
8. Restart containers

This ensures fully automated deployment without manual intervention.

---

# 🔐 Secrets Management

The following GitHub Secrets are configured:

- DOCKER_USERNAME
- DOCKER_PASSWORD (Docker Hub Access Token)
- EC2_HOST
- EC2_SSH_KEY

Sensitive data is never stored directly in the repository.

---

# 🌐 Nginx Reverse Proxy

Nginx is configured as a reverse proxy:

- `/` routes to frontend
- `/api` routes to backend
- Exposes only port 80 to public

Configuration file:

nginx/default.conf


This provides clean routing and production-style architecture.

---

# 🗄 Database Setup

MongoDB runs as a Docker container inside the same Docker network.

Backend connects using:


mongodb://mongodb:27017/dd_db


MongoDB is isolated from public exposure.


---

# 🚀 Live Application

Application is accessible at:


http://13.201.79.211


# 📌 Assignment Requirements 

| Requirement           | Status |
|-------------          |--------|
| GitHub Repository     | ✅ Completed |
| Dockerfiles           | ✅ Completed |
| Docker Compose        | ✅ Completed |
| Docker Hub Images     | ✅ Completed |
| AWS EC2 Deployment    | ✅ Completed |
| MongoDB Setup         | ✅ Completed |
| CI/CD Pipeline        | ✅ Completed |
| Nginx Reverse Proxy   | ✅ Completed |
