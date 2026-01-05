🚀 **Dockerized Nginx Deployment on AWS EC2 (Ubuntu)**
📌 Project Overview

<img width="1256" height="682" alt="ArchitectureDiagram" src="https://github.com/user-attachments/assets/04d01f95-48fe-4dfd-9c46-6fc6a07e4322" />

<img width="1133" height="625" alt="ArchitectureDiagram1" src="https://github.com/user-attachments/assets/6e93f492-6231-447b-b2f5-f13eccf3c856" />


This project demonstrates an end-to-end Docker deployment of an Nginx web server on an AWS EC2 Ubuntu instance.
It covers the complete workflow from Docker image creation to cloud deployment, simulating a real-world DevOps use case.

The project is intentionally kept simple (no application framework) to focus on containerization, cloud infrastructure, and deployment fundamentals.

🧰 **Tech Stack**

Cloud Provider: AWS

Compute Service: EC2

Operating System: Ubuntu 22.04

Containerization: Docker

Web Server: Nginx

📁 Project Structure
docker-nginx-project/
│
├── Dockerfile
└── index.html

📝 **Application Details**

The container serves a static HTML page using Nginx, displaying a confirmation message that Docker is successfully running on AWS EC2.

🐳 **Dockerfile**

FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80

🌐 **index.html**

<!DOCTYPE html>
<html>
<head>
  <title>Docker on AWS EC2</title>
</head>
<body>
  <h1>🚀 Docker Nginx Deployed on AWS EC2</h1>
  <p>DevOps | Docker | AWS</p>
</body>
</html>

☁️ **AWS EC2 Setup**

AMI: Ubuntu 22.04 LTS

Instance Type: t2.micro (Free Tier)

Security Group Rules:

SSH (22) – My IP

HTTP (80) – Anywhere

🔐 **Connect to EC2**

chmod 400 mykey.pem
ssh -i mykey.pem ubuntu@<EC2_PUBLIC_IP>

🛠 **Install Docker on EC2**

sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ubuntu
exit

Reconnect after logout.

📂 **Copy Project to EC2**

scp -i mykey.pem -r docker-nginx-project ubuntu@<EC2_PUBLIC_IP>:/home/ubuntu/

🔨 **Build Docker Image**

cd docker-nginx-project
docker build -t nginx-docker-demo .


Verify:

**docker images**

▶️ **Run Docker Container**

docker run -d -p 80:80 --name nginx-container nginx-docker-demo


**Check running containers:**

docker ps

**🌍 Access the Application**

**Open your browser:**

http://<EC2_PUBLIC_IP>

You should see:

Docker Nginx Deployed on AWS EC2

**📊 DevOps Concepts Demonstrated**

Docker image creation using Dockerfile

Container lifecycle management

AWS EC2 provisioning

Linux server administration

Port mapping & networking

Cloud-ready container deployment

**🔮 Future Enhancements**

Push image to Docker Hub

Docker Compose setup

HTTPS using Nginx

Reverse proxy configuration

CI/CD pipeline using Jenkins or GitHub Actions

Kubernetes deployment (EKS)

Browser output

👤 Author

Vardhan Kandregula
DevOps Engineer | AWS | Docker | Kubernetes | CI/CD

📌 This project is part of my DevOps learning and portfolio.

⭐ If you like this project

Give it a ⭐ on GitHub and feel free to fork or contribute!
