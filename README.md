# Production-Ready DevOps Web Application Deployment on AWS

A complete end-to-end DevOps project demonstrating deployment, automation, monitoring, and security best practices using AWS Free Tier services.

## Project Overview

This project showcases a production-like deployment pipeline for a Dockerized Flask web application hosted on AWS EC2. The infrastructure includes automated CI/CD with Jenkins, containerization using Docker, monitoring using Prometheus and Grafana, AWS CloudWatch integration, secure access control, and performance testing.

The objective is to demonstrate a real-world DevOps workflow from source code management to deployment and monitoring.

---

## Architecture

```
                            Developer
                                │
                                │ Git Push
                                ▼
                        GitHub Repository
                                │
                        GitHub Webhook
                                │
                                ▼
                         Jenkins Pipeline
                    (CI/CD Automation Server)
                                │
               ┌────────────────┴────────────────┐
               │                                 │
        Build Docker Image              Push Image to Docker Hub
               │                                 │
               └────────────────┬────────────────┘
                                │
                                ▼
                         AWS EC2 Instance
                                │
               Pull Latest Docker Image
                                │
                                ▼
                    Docker Container (Flask App)
                                │
                                ▼
                     Portfolio Web Application
                                │
         ┌──────────────────────┼───────────────────────┐
         │                      │                       │
         ▼                      ▼                       ▼
   Node Exporter          cAdvisor Metrics       Jenkins Metrics
         │                      │                       │
         └───────────────┬──────┴───────────────┬───────┘
                         ▼                      │
                    Prometheus Server           │
                         │                      │
                         └──────────────┬───────┘
                                        ▼
                                Grafana Dashboard

──────────────────────────────────────────────────────────────

          AWS CloudWatch         Amazon S3
                │                   │
        EC2 Monitoring        Backup Storage
```

---

## Tech Stack

### Cloud

- AWS EC2
- AWS IAM
- AWS CloudWatch
- AWS S3 (Backup & Storage)

### DevOps

- Jenkins
- Docker
- Docker Hub
- Git
- GitHub

### Monitoring

- Prometheus
- Grafana
- Node Exporter
- cAdvisor

### Load Testing

- k6

### Application

- Python
- Flask

---

## Features

- Dockerized Flask application
- Automated CI/CD pipeline using Jenkins
- GitHub webhook integration
- Automatic Docker image build and deployment
- Docker Hub image registry
- Monitoring with Prometheus and Grafana
- Container monitoring using cAdvisor
- Server monitoring using Node Exporter
- CloudWatch dashboard and alarms
- S3 backup storage
- IAM least-privilege implementation
- Security Group configuration
- Performance testing using k6

---

## Project Structure

```
.
├── app.py
├── requirements.txt
├── Dockerfile
├── Jenkinsfile
├── prometheus.yml
├── docker-compose.yml
├── load-test/
│   └── script.js
├── screenshots/
├── docs/
└── README.md
```

---

## Deployment Workflow

1. Developer pushes code to GitHub.
2. GitHub webhook triggers Jenkins pipeline.
3. Jenkins pulls the latest source code.
4. Docker image is built.
5. Docker image is pushed to Docker Hub.
6. EC2 server pulls the latest image.
7. Existing container is replaced with the latest version.
8. Application becomes available to users.
9. Prometheus collects metrics.
10. Grafana visualizes infrastructure and application performance.
11. CloudWatch monitors AWS resources and triggers alarms.

---

## CI/CD Pipeline

The Jenkins pipeline performs the following stages:

- Clone Repository
- Install Dependencies
- Build Docker Image
- Push Docker Image
- Pull Latest Image on EC2
- Deploy Container
- Verify Deployment

---

## Monitoring

Infrastructure monitoring includes:

- CPU Usage
- Memory Usage
- Disk Utilization
- Network Statistics
- Docker Container Metrics
- Application Availability

Tools used:

- Prometheus
- Grafana
- Node Exporter
- cAdvisor
- AWS CloudWatch

---

## Security

The project follows security best practices:

- IAM Least Privilege Principle
- Security Groups configured with minimal required ports
- Docker container isolation
- SSH access restricted
- CloudWatch monitoring
- Secure Docker image deployment

---

## Load Testing

Performance testing was conducted using k6.

Metrics collected:

- Response Time
- Throughput
- Requests Per Second
- Error Rate
- CPU Utilization
- Memory Utilization

---

## AWS Services Used

- EC2
- IAM
- CloudWatch
- S3

---

## Monitoring Dashboard

The Grafana dashboard includes:

- CPU Utilization
- Memory Usage
- Disk Usage
- Network Traffic
- Docker Container Metrics
- System Health

---

## Screenshots

The repository contains screenshots demonstrating:

- AWS EC2
- Jenkins Pipeline
- Docker Containers
- GitHub Repository
- Grafana Dashboard
- Prometheus Targets
- CloudWatch Dashboard
- Load Testing Results
- Application Deployment

---

## Future Improvements

- HTTPS using Let's Encrypt
- Reverse Proxy using Nginx
- Infrastructure as Code using Terraform
- Kubernetes Deployment
- AWS ECR Integration
- Auto Scaling
- Load Balancer
- Blue-Green Deployment

---

## Author

Aditya M Khiroji

DevOps | Cloud | AWS | Docker | Jenkins | Monitoring
