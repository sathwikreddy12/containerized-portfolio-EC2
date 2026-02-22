~                                                                                                                                                                                                              
🚀 CI/CD Automated Deployment to AWS EC2
Containerized Portfolio with Nginx Reverse Proxy
📌 Project Overview

This project demonstrates a complete end-to-end CI/CD pipeline for deploying a Dockerized web application to an AWS EC2 instance using GitHub Actions.

The system automatically:

Builds Docker images

Pushes them to Docker Hub

Connects to EC2 via SSH

Pulls the latest image

Restarts the container

Serves traffic through Nginx reverse proxy

All deployments are fully automated and require zero manual intervention.

🏗 Architecture Overview
Developer
   ↓
GitHub Repository
   ↓
GitHub Actions (CI/CD)
   ↓
Docker Hub
   ↓
AWS EC2 (via SSH)
   ↓
Docker Container (Port 8081)
   ↓
Nginx Reverse Proxy (Port 80)
   ↓
End User
🐳 Docker Configuration

The application is containerized using Docker.

Build Image
docker build -t sathwik1reddy/portfolio:latest .
Run Container
docker run -d -p 8081:80 --name portfolio-app sathwik1reddy/portfolio:latest

The container runs on port 8081 internally.

🌐 Nginx Reverse Proxy Configuration

Nginx is configured to forward traffic from port 80 to the Docker container.

File:

/etc/nginx/sites-available/default

Configuration:

server {
    listen 80;

    location / {
        proxy_pass http://localhost:8081;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}

This allows users to access the website using:

http://<Elastic-IP>

without specifying port 8081.

⚙️ CI/CD Pipeline (GitHub Actions)

Workflow Location:

.github/workflows/docker-deploy.yml
Pipeline Steps:

Trigger on push to main

Checkout repository

Login to Docker Hub

Build Docker image

Push image to Docker Hub

SSH into EC2

Pull latest Docker image

Stop old container

Start updated container

Deployment happens automatically after every push.

🔐 GitHub Secrets Used

The following repository secrets are configured securely:

DOCKER_USERNAME

DOCKER_PASSWORD

EC2_HOST

EC2_USER

EC2_SSH_KEY

No credentials are exposed in the workflow file.

☁ AWS Infrastructure Setup

AWS EC2 (Ubuntu)

Elastic IP (static public IP)

Docker installed

Nginx installed

Security Group allows HTTP (Port 80)

🔄 Automated Deployment Flow

Whenever changes are pushed to the main branch:

GitHub Actions builds a new Docker image

Image is pushed to Docker Hub

GitHub connects to EC2 via SSH

EC2 pulls the latest image

Old container is stopped and removed

New container is started

Website updates automatically

No manual SSH access is required.

✅ Final Outcome

✔ Fully automated CI/CD pipeline
✔ Dockerized application
✔ Nginx reverse proxy configuration
✔ Secure SSH-based deployment
✔ Elastic IP-based static access
✔ Zero-touch production updates

📚 Technologies Used

Docker

GitHub Actions

AWS EC2

Elastic IP

Nginx

SSH Key Authentication

🎯 Key Learning Outcomes

Implemented end-to-end CI/CD pipeline

Automated Docker-based deployments

Configured reverse proxy with Nginx

Managed secure secrets in GitHub

Designed production-style deployment architecture

👨‍💻 Author
Sathwik Reddy DevOps & Data Engineering Enthusiast

