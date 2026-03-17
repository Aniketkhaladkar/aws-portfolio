# 🚀 AWS Portfolio Deployment with Docker & CI/CD

## 📌 Project Overview

This project demonstrates **end-to-end DevOps implementation**:

* **Task-2:** Containerization using Docker and deployment on AWS EC2
* **Task-3:** CI/CD automation using GitHub Actions to build and push Docker images

The portfolio website is containerized, deployed on a cloud server, and automated using a CI/CD pipeline.

---

## 🛠️ Technologies Used

* HTML, CSS, JavaScript
* Docker
* AWS EC2 (Ubuntu)
* Git & GitHub
* GitHub Actions (CI/CD)
* Docker Hub

---

## 📂 Project Structure

```bash
aws-portfolio/
│
├── index.html
├── css/
├── js/
├── images/
├── Dockerfile
├── README.md
│
└── .github/
      └── workflows/
            └── docker-ci.yml
```

---

# 🐳 TASK-2: Docker & AWS Deployment

## 🔹 Step 1: Build Docker Image

```bash
docker build -t aws-portfolio .
```

## 🔹 Step 2: Run Container Locally

```bash
docker run -d -p 8080:80 aws-portfolio
```

## 🔹 Access Local Website

```
http://localhost:8080
```

---

## ☁️ AWS EC2 Deployment

### 🔹 Launch EC2 Instance

* OS: Ubuntu
* Instance Type: t2.micro (Free Tier)
* Security Group: Allow HTTP (Port 80)

---

### 🔹 Connect to EC2

```bash
ssh -i your-key.pem ubuntu@YOUR_PUBLIC_IP
```

---

### 🔹 Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
```

---

### 🔹 Clone Project

```bash
git clone https://github.com/YOUR_USERNAME/aws-portfolio.git
cd aws-portfolio
```

---

### 🔹 Build & Run on EC2

```bash
sudo docker build -t aws-portfolio .
sudo docker run -d -p 80:80 aws-portfolio
```

---

### 🔹 Access Live Website

```
http://YOUR_PUBLIC_IP
```

---

# ⚙️ TASK-3: CI/CD using GitHub Actions

## 🔹 CI/CD Workflow

This project uses GitHub Actions to:

* Automatically build Docker image
* Push image to Docker Hub
* Trigger on every push to main branch

---

## 🔹 Workflow File Location

```
.github/workflows/docker-ci.yml
```

---

## 🔹 Workflow Code

```yaml
name: Docker CI Pipeline

on:
  push:
    branches:
      - main

jobs:
  docker-build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Code
      uses: actions/checkout@v3

    - name: Login to Docker Hub
      uses: docker/login-action@v2
      with:
        username: ${{ secrets.DOCKER_USERNAME }}
        password: ${{ secrets.DOCKER_PASSWORD }}

    - name: Build Docker Image
      run: docker build -t ${{ secrets.DOCKER_USERNAME }}/aws-portfolio:latest .

    - name: Push Docker Image
      run: docker push ${{ secrets.DOCKER_USERNAME }}/aws-portfolio:latest
```

---

## 🔐 GitHub Secrets

Configured in repository:

* `DOCKER_USERNAME` → Docker Hub username
* `DOCKER_PASSWORD` → Docker Hub password

---

## 🐳 Docker Hub Repository

```
https://hub.docker.com/r/YOUR_USERNAME/aws-portfolio
```

---

## 🧪 Test Docker Image

```bash
docker pull YOUR_USERNAME/aws-portfolio:latest
docker run -d -p 80:80 YOUR_USERNAME/aws-portfolio
```

---

## 📸 Output Screenshots

* Docker container running locally (`docker ps`)
* Website running on localhost
* AWS EC2 deployed website (Public IP)
* GitHub repository
* GitHub Actions pipeline success
* Docker Hub image

---

## 🎯 Learning Outcomes

* Docker containerization and image creation
* Cloud deployment using AWS EC2
* CI/CD pipeline using GitHub Actions
* Secure credential management using secrets
* Automation of build and deployment process

---

## 👨‍💻 Author

**Aniket Khaladkar**

---

## 🌟 Conclusion

This project demonstrates a complete DevOps workflow — from local development to cloud deployment and CI/CD automation, ensuring scalability, reliability, and efficiency.
