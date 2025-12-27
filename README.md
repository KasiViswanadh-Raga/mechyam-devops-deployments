🚀 DevOps + AWS Deployment Task – Mechyam Application
📌 Task Objective
The objective of this task is to deploy a Frontend (React.js) and Backend (Spring Boot) application on AWS EC2 using Docker and Jenkins CI/CD pipeline, ensuring automated build and deployment.
🔗 Given Source Code
Backend (Spring Boot):
https://github.com/nebulytixtechnologies-web/Mechyam-Backend.git
Frontend (React.js):
https://github.com/Tejassoni05/frontend-mechyam.git
🛠 Tools & Technologies Used
AWS EC2 (Free Tier)
Docker
Jenkins
Git & GitHub
Spring Boot
React.js
Nginx (Frontend Server)
🧱 Architecture Overview
Jenkins is installed on an AWS EC2 instance
Jenkins pipeline automates:
Code checkout
Application build
Docker image creation
Deployment
Backend runs as a Spring Boot Docker container
Frontend is served using Nginx Docker container
Applications are accessed using EC2 Public IP
📂 Repository Structure
Copy code

mechyam-devops-ci-cd/
├── backend/
│   └── Dockerfile
├── frontend/
│   └── Dockerfile
├── Jenkinsfile
├── screenshots/
│   ├── jenkins-pipeline-success.png
│   └── backend-running.png
└── README.md
⚙️ Deployment Process (Step-by-Step)
1️⃣ AWS EC2 Setup
Created an EC2 Free Tier instance
Opened required ports in Security Group:
22 – SSH
80 – Frontend
8080 / 8081 – Backend
8080 / 8081 – Jenkins
2️⃣ Install Required Software
Docker
Jenkins
Git
Java (for Jenkins & Spring Boot)
3️⃣ Jenkins Configuration
Jenkins installed and configured on EC2
Pipeline created using Jenkinsfile
GitHub repository integrated with Jenkins
🔄 Jenkins Pipeline Stages
🔹 Stage 1: Git Checkout
Jenkins clones:
Frontend repository
Backend repository
🔹 Stage 2: Build
Backend built using Maven
Frontend built using npm
🔹 Stage 3: Docker Image Creation
Docker image created for backend using Spring Boot JAR
Docker image created for frontend and served via Nginx
🔹 Stage 4: Deployment
Old containers stopped and removed
New containers started with updated images
Applications deployed automatically on EC2
*Applicatin Access
.Frontend Application
http://3.239.242.21
.Backend Application:
http://3.239.242.21:8081
*Screenshots
Jenkins pipeline-Success
![Jenkins pipeline-Success](Jenkins pipeline-success-screenshot1.png)
![Jenkins pipeline-Success](Jenkins-pipeline-success-screenshot2.png)
