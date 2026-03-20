# 🚀 CI/CD Pipeline 


TechFlow CI/CD Project – Python App Deployment with Docker & GitHub Actions
📌 Overview
This project demonstrates a complete CI/CD pipeline for deploying a Python Flask application using modern DevOps tools and practices.
The pipeline automatically:
•	Builds a Docker image
•	Pushes it to DockerHub
•	Deploys it to an AWS EC2 instance
•	Performs a health check
•	Rolls back to a previous version if deployment fails
________________________________________
 Architecture
Developer → GitHub → GitHub Actions → DockerHub → AWS EC2 → Docker Container
________________________________________
⚙️ Tech Stack
•	Python (Flask) – Web application
•	Docker – Containerisation
•	GitHub Actions – CI/CD automation
•	DockerHub – Container registry
•	AWS EC2 – Deployment server
•	SSH – Secure remote deployment
•	curl – Health check validation
________________________________________


CI/CD Pipeline Flow
1.	Code is pushed to GitHub
2.	GitHub Actions workflow is triggered
3.	Dependencies are installed and tests executed
4.	Docker image is built
5.	Image is tagged (latest + commit SHA)
6.	Image is pushed to DockerHub
7.	EC2 server pulls the new image
8.	Existing container is stopped and removed
9.	New container is started
10.	Health check is performed
11.	If failed → automatic rollback to previous version
________________________________________
Docker Commands Used
Build image:
docker build -t <docker-username>/techflow-project:latest .
Push image:
docker push <docker-username>/techflow-project:latest
Run container:
docker run -d -p 5000:5000 --name techflow-container <docker-username>/techflow-project:latest
________________________________________
Deployment (EC2)
The application is deployed to an AWS EC2 instance via SSH using GitHub Actions.
Access the app:
http://<EC2-PUBLIC-IP>:5000
________________________________________
🔐 Secrets Management
Sensitive credentials are securely stored using GitHub Secrets:
•	DOCKER_USERNAME
•	DOCKER_PASSWORD
•	EC2_HOST
•	EC2_SSH_KEY
________________________________________
Rollback Strategy
•	The current running image is saved before deployment
•	After deployment, a health check is performed
•	If the health check fails:
o	The new container is stopped
o	The previous image is redeployed automatically
________________________________________
📁 Project Structure
.
├── app.py
├── requirements.txt
├── Dockerfile
├── .github/
│   └── workflows/
│       └── python-app.yml
└── README.md
________________________________________


✅ Features
•	Automated CI/CD pipeline
•	Dockerised application
•	Versioned image tagging
•	Cloud deployment (AWS EC2)
•	Automated rollback on failure
•	Secure credential handling
________________________________________
 Future Improvements
•	Add Nginx reverse proxy and HTTPS
•	Implement Infrastructure as Code (Terraform)
•	Add monitoring (Prometheus/Grafana)
•	Use Kubernetes for orchestration
•	Implement Blue-Green deployment strategy
________________________________________
Key Learnings
•	End-to-end CI/CD pipeline design
•	Container lifecycle management
•	Secure deployment practices
•	Automated failure recovery (rollback)
•	Real-world DevOps workflow implementation
________________________________________
👤 AuthorBabatola Adeniyi
DevOps / Cloud Engineer
GitHub: https://github.com/Babatee23

