# 🚀 AWS Portfolio Deployment using Docker

## 📌 Project Overview

This project demonstrates **containerization and cloud deployment** of a portfolio website using **Docker and AWS EC2**.

The application is packaged into a Docker container and deployed on a cloud virtual machine, making it accessible via a public IP address.

---

## 🛠️ Technologies Used

* HTML, CSS, JavaScript
* Docker
* AWS EC2 (Ubuntu)
* Git & GitHub

---


## 🐳 Docker Setup

### 1️⃣ Build Docker Image

```
docker build -t aws-portfolio .
```

### 2️⃣ Run Docker Container

```
docker run -d -p 8080:80 aws-portfolio
```

### 3️⃣ Access Locally

```
http://localhost:8080
```

---

## ☁️ AWS EC2 Deployment

### 1️⃣ Launch EC2 Instance

* OS: Ubuntu
* Instance Type: t2.micro (Free Tier)
* Security Group: Allow HTTP (Port 80)

---

### 2️⃣ Connect to EC2

```
ssh -i your-key.pem ubuntu@YOUR_PUBLIC_IP
```

---

### 3️⃣ Install Docker

```
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
```

---

### 4️⃣ Clone Project

```
git clone https://github.com/YOUR_USERNAME/aws-portfolio.git
cd aws-portfolio
```

---

### 5️⃣ Build Docker Image on EC2

```
sudo docker build -t aws-portfolio .
```

---

### 6️⃣ Run Container

```
sudo docker run -d -p 80:80 aws-portfolio
```

---

### 7️⃣ Access Website

```
http://YOUR_PUBLIC_IP
```

---
