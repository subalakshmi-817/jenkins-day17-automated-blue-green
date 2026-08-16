# 🚀 Jenkins Day 17 – Automated Blue-Green Deployment

## 📌 Project Overview

This project demonstrates an automated Blue-Green Deployment workflow using GitHub, Jenkins, Docker, and Nginx.

The project extends the Blue-Green Deployment concept from Day 16 by introducing automation through Jenkins and GitHub Webhooks.

The complete workflow is:

Developer → GitHub → Webhook → Jenkins → Docker → Blue-Green Deployment → Health Check → Verification

The goal is to create a practical CI/CD deployment pipeline where a GitHub code change can automatically trigger Jenkins.

---

## 🎯 Objectives

The objectives of this project are:

- Understand automated Blue-Green Deployment.
- Integrate GitHub with Jenkins.
- Configure Jenkins Pipeline.
- Build Docker images automatically.
- Deploy Blue and Green environments.
- Perform automated health checks.
- Understand GitHub Webhooks.
- Understand CI/CD automation.
- Manage Docker containers using Jenkins.
- Verify application availability.
- Practice DevOps workflow on Linux.

---

## ❗ Problem Statement

Manual deployment requires developers or administrators to execute multiple commands.

A typical manual deployment process involves:

1. Pull source code.
2. Build application.
3. Build Docker image.
4. Stop old containers.
5. Start new containers.
6. Test application.
7. Verify deployment.

Manual processes can cause:

- Human errors
- Deployment delays
- Configuration mistakes
- Downtime
- Inconsistent deployments

This project automates the process using Jenkins.

---

## 💡 Proposed Solution

GitHub is used as the source code repository.

Jenkins monitors or receives GitHub webhook events.

When a developer pushes new code:

GitHub
↓
Webhook
↓
Jenkins
↓
Checkout
↓
Build Docker Images
↓
Deploy Blue
↓
Health Check
↓
Deploy Green
↓
Health Check
↓
Verify

This creates an automated CI/CD workflow.

---

## 🔵 Blue Environment

Blue represents the stable/current application version.

Docker image:

day17-blue

Container:

day17-blue-container

Port:

8091

URL:

http://localhost:8091

---

## 🟢 Green Environment

Green represents the new application version.

Docker image:

day17-green

Container:

day17-green-container

Port:

8092

URL:

http://localhost:8092

---

## 🏗️ Architecture

Developer
↓
GitHub
↓
GitHub Webhook
↓
Jenkins
↓
Docker
↓
Blue + Green Containers
↓
Health Checks
↓
Deployment Verification

---

## 📁 Project Structure

```text
jenkins-day17-automated-blue-green/
│
├── blue/
│   ├── Dockerfile
│   └── index.html
│
├── green/
│   ├── Dockerfile
│   └── index.html
│
├── screenshots/
│
├── Jenkinsfile
├── README.md
└── notes.txt
🛠️ Technologies Used
Ubuntu Linux
Git
GitHub
Jenkins
Docker
Nginx
HTML
Jenkins Declarative Pipeline
GitHub Webhook
🐳 Docker Commands

Build Blue:

docker build -t day17-blue ./blue

Build Green:

docker build -t day17-green ./green

Run Blue:

docker run -d --name day17-blue-container -p 8091:80 day17-blue

Run Green:

docker run -d --name day17-green-container -p 8092:80 day17-green

Check containers:

docker ps

Check images:

docker images
❤️ Health Checks

Blue:

curl -f http://localhost:8091

Green:

curl -f http://localhost:8092

A successful response confirms that the application is reachable.

⚙️ Jenkins Pipeline

The Jenkins Pipeline contains:

Checkout
Build Blue Image
Build Green Image
Remove Old Containers
Deploy Blue
Health Check Blue
Deploy Green
Health Check Green
Verify Deployment
🔔 GitHub Webhook

GitHub Webhook is used to notify Jenkins about repository changes.

Workflow:

git push
   ↓
GitHub
   ↓
Webhook
   ↓
Jenkins
   ↓
Pipeline

This removes the need to manually start Jenkins for every source-code change, when the webhook and Jenkins trigger are correctly configured.

🔧 Jenkins Configuration

Job:

Day17-Automated-Blue-Green

Pipeline:

Pipeline script from SCM

SCM:

Git

Repository:

https://github.com/subalakshmi-817/jenkins-day17-automated-blue-green.git

Branch:

*/main

Script:

Jenkinsfile
🧪 Testing

Testing is performed at multiple levels.

Docker Test
docker images
Container Test
docker ps
Blue Application Test
curl http://localhost:8091
Green Application Test
curl http://localhost:8092
Jenkins Test

Run the Jenkins Pipeline.

Webhook Test

Push a new commit to GitHub and verify that Jenkins receives the event.

🔁 Blue-Green Deployment Concept

Blue:

Version 1.0

Green:

Version 2.0

Green is tested before becoming the active environment.

If Green is successful:

Production → Green

If Green fails:

Production → Blue

This provides a rollback option.

✅ Advantages
Automated deployment
Reduced manual work
Safer releases
Easy rollback
Separate environments
Automated health checks
CI/CD integration
GitHub integration
Jenkins automation
Docker isolation
⚠️ Limitations
Requires additional resources.
Requires Docker.
Jenkins needs Docker access.
GitHub Webhook requires Jenkins to be reachable by GitHub.
Production traffic switching requires additional infrastructure.
Database migrations need careful handling.
🐞 Troubleshooting
Docker permission problem
groups jenkins

Jenkins may need Docker group access:

sudo usermod -aG docker jenkins

Restart Jenkins:

sudo systemctl restart jenkins
Check Docker
sudo systemctl status docker
Check Jenkins
sudo systemctl status jenkins
Check containers
docker ps -a
Check logs
docker logs day17-blue-container
docker logs day17-green-container
📸 Screenshots

The screenshots folder contains implementation evidence for:

GitHub repository
Project structure
Docker image build
Docker containers
Applications
Health checks
Git configuration
Jenkins configuration
Jenkins Pipeline
GitHub Webhook
Final deployment
🎓 Learning Outcomes

After completing Day 17, the following concepts are understood:

Git
GitHub
Jenkins
Docker
Dockerfile
Nginx
CI/CD
Jenkins Pipeline
GitHub Webhooks
Blue-Green Deployment
Health Checks
Container Management
Automated Deployment
Linux DevOps workflow
🚀 Future Enhancements

Future versions can include:

Nginx Reverse Proxy
Automatic traffic switching
Docker Compose
Prometheus
Grafana
Kubernetes
AWS EC2
Automatic rollback
Slack notifications
Email notifications
Automated testing
Docker security scanning
HTTPS
Load balancing
🏆 Project Result

The final workflow is:

Developer
   ↓
GitHub
   ↓
GitHub Webhook
   ↓
Jenkins
   ↓
Docker Build
   ↓
Blue Environment
   ↓
Green Environment
   ↓
Health Check
   ↓
Verification
   ↓
SUCCESS
👩‍💻 Author

Subalakshmi K

Computer Science Engineering Student

DevOps / Cloud / Linux Enthusiast

Project:

Jenkins Day 17 – Automated Blue-Green Deployment

⭐ Conclusion

Jenkins Day 17 extends the Blue-Green Deployment project by introducing automated CI/CD integration between GitHub and Jenkins.

The project demonstrates how a developer's GitHub push can trigger an automated Jenkins Pipeline, build Docker images, deploy Blue and Green environments, perform health checks, and verify the deployment.

This project provides practical experience in real-world DevOps automation and creates a foundation for advanced topics such as Kubernetes, cloud deployment, monitoring, load balancing, and automated rollback.
