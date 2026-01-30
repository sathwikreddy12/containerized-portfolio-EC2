# 🚀 Portfolio Website Deployment using Docker & AWS EC2

## 📌 Project Overview

This project demonstrates how a static portfolio website can be containerized using Docker and deployed on an AWS EC2 instance.
The website is served using **Nginx inside a Docker container** and made publicly accessible by configuring **EC2 Security Group inbound rules**.

This project was completed as part of a **Cloud Computing & DevOps task**, focusing on real-world deployment challenges such as:
- Port conflicts
- Container networking
- Cloud security configurations

---

## 🛠️ Tech Stack Used

- **Docker** – Containerization  
- **Nginx** – Web server  
- **AWS EC2 (Ubuntu)** – Cloud compute  
- **Linux** – Server environment  
- **HTML / CSS** – Static website content  

---

## 📂 Project Structure

```
portfolio/
│
├── Dockerfile
├── index.html
├── style.css
├── assets/        # images, icons (if any)
└── README.md
```

---

## 🐳 Dockerfile

```dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html/
```

### Explanation:
- Uses a lightweight **Nginx Alpine** base image  
- Copies all website files (HTML, CSS, assets) to Nginx’s default serving directory  

---

## ⚙️ Steps to Run the Project

### 1️⃣ Build the Docker Image
```bash
docker build -t task2-portfolio .
```

### 2️⃣ Run the Docker Container
```bash
docker run --name portfolio-website -d -p 8081:80 task2-portfolio
```

> Port **8081** is used to avoid conflicts with existing services like **Jenkins (8080)** and host **Nginx (80)**.

---

### 3️⃣ Configure AWS EC2 Security Group

Add the following **Inbound Rule**:

| Type       | Protocol | Port | Source     |
|------------|----------|------|------------|
| Custom TCP | TCP      | 8081 | 0.0.0.0/0  |

⚠️ This step is mandatory to allow public access.

---

## 🌐 Access the Website

```
http://<EC2-Public-IP>:8081
```

### Example:
```
http://3.17.57.129:8081
```

---

## 🧠 Key Learnings

- Docker containerization of static websites  
- Understanding **host vs container port mapping**  
- Handling **port conflicts** on Linux servers  
- Configuring **AWS EC2 Security Groups**  
- Deploying applications in a **cloud environment**  
- Real-world **DevOps debugging and troubleshooting**  

---

## 🎯 Outcome

✔ Successfully hosted a portfolio website as a Docker container  
✔ Deployed on AWS EC2  
✔ Accessible publicly via a custom port  
✔ Followed DevOps best practices  

---

## 📌 Future Enhancements

- Add HTTPS using **AWS ALB / CloudFront**  
- Push Docker image to **Docker Hub / Amazon ECR**  
- Automate deployment using **Jenkins CI/CD pipeline**  
- Use **Docker Compose** for better service management  

---

## 👤 Author

**Sathwik Reddy**  
DevOps & Cloud Enthusiast
