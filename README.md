~                                                                                                                                                                                                              
🚀 Containerized Portfolio Website --- CI Pipeline using GitHub Actions & Docker

📌 Task Overview
This project demonstrates the implementation of a Continuous Integration (CI) pipeline that automatically builds and pushes a Docker image of a portfolio website whenever code changes are pushed to GitHub.
🎯 Task Deliverables Covered
GitHub repository with CI workflow
Screenshot of successful GitHub Actions run
Docker Hub image link
README explaining CI process

🛠️ Technologies Used
HTML
CSS
Docker
GitHub Actions
Docker Hub
AWS EC2 (Ubuntu Linux)

📁 Project Structure

containerized-portfolio-EC2/
│
├── Dockerfile
├── index.html
├── styles.css
├── README.md
└── .github/workflows/docker-deploy.yml

🐳 Docker Configuration
Build Image:

docker build -t portfolio .
Run Container:

docker run -d -p 8081:80 portfolio
⚙️ GitHub Actions CI Workflow

Trigger: Code push to main branch
Steps:
Checkout Repository
Login to Docker Hub
Build Docker Image
Push Image to Docker Hub
🔐 GitHub Secrets Used
DOCKER_USERNAME
DOCKER_PASSWORD

🐳 Docker Hub Image
https://hub.docker.com/repository/docker/sathwik1reddy/portfolio/general

☁️ Deployment on AWS EC2

docker pull sathwik1reddy/portfolio:latest
docker run -d -p 8081:80 --name portfolio-website sathwik1reddy/portfolio:latest

Access:

http://18.221.252.136:8081/
👨‍💻 Author
Sathwik Reddy DevOps & Data Engineering Enthusiast

