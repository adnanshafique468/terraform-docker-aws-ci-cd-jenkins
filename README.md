# 🚀 Terraform + Docker + Jenkins CI/CD Pipeline

This repository demonstrates a **complete DevOps CI/CD workflow** using Terraform, Docker, Jenkins, and GitHub Webhooks.  
It is designed for beginners to understand **infrastructure provisioning, containerization, and automated deployment**.

---

## 🌟 Features

- **Infrastructure as Code**: Automatically create an Ubuntu EC2 instance using Terraform (Free Tier compatible).  
- **Dockerized Application**: Node.js website containerized with Docker for portability and consistency.  
- **CI/CD Pipeline**: Jenkins pipeline automates build, test, and deployment.  
- **GitHub Webhook Integration**: Code pushes automatically trigger Jenkins pipeline.  
- **Email Notifications**: Notify team on deployment success or failure.

---

## 🏗️ Project Structure

```text
terraform-docker-jenkins-ci-cd
│
├── app
│   ├── package.json
│   ├── server.js
│   └── public/index.html
│
├── docker
│   └── Dockerfile
├── terraform
│   ├── main.tf
│   ├── variables.tf
│   └── outputs.tf
├── Jenkinsfile
├── .gitignore
├── .dockerignore
└── README.md

⚙️ Technologies Used

Terraform – Infrastructure provisioning

AWS EC2 – Cloud virtual machine

Docker – Containerization

Node.js & Express – Backend application

Jenkins – CI/CD automation

GitHub Webhooks – Pipeline triggers

Email Notifications – Build status alerts

📝 Prerequisites

AWS Account with permissions to create EC2 and Security Groups

Git installed locally

Node.js (for local testing)

Docker installed (if testing locally)

Jenkins (optional local testing before EC2 deployment)

🚀 Deployment Steps
1. Terraform – Provision EC2
cd terraform
terraform init
terraform plan
terraform apply
# Type 'yes' to confirm

EC2 will be created with latest Ubuntu AMI

Security Group opens SSH(22), HTTP(80), Jenkins(8080)

2. SSH into EC2
ssh -i jenkins-key.pem ubuntu@<EC2_PUBLIC_IP>
3. Docker Build & Run Application
docker build -t node-cicd-app -f docker/Dockerfile .
docker rm -f node-app || true
docker run -d -p 80:3000 --name node-app node-cicd-app

Website accessible at: http://<EC2_PUBLIC_IP>

4. Jenkins Setup

Access Jenkins: http://<EC2_PUBLIC_IP>:8080

Create a Pipeline Job using Jenkinsfile from this repository

GitHub Webhook triggers automatic builds

5. GitHub Webhook Setup

Go to repository → Settings → Webhooks → Add webhook

Payload URL: http://<JENKINS_IP>:8080/github-webhook/

Content type: application/json

Events: Just push events

6. Email Notifications

Jenkins pipeline is configured to send email on success or failure

Configure SMTP settings in Jenkins → Email Extension Plugin

💡 Best Practices

Always keep Terraform variables in variables.tf for flexibility

Use Free Tier compatible EC2 (t3.micro) to avoid billing issues

Keep .gitignore and .dockerignore updated to avoid unnecessary files in repo

Automate Security Group creation to ensure all required ports are open

📌 License

This project is open source and free to use.

📧 Author / Contact

Name: Adnan Shafiq

Email: adnanshafiq476@gmail.com