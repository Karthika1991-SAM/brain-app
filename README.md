1. Project Overview

This project is a React application deployed in a production-ready environment using:

Docker – containerizes the app

AWS ECR – stores Docker images

AWS EKS – Kubernetes cluster for running the app

CodeBuild – CI/CD pipeline that builds, pushes, and deploys automatically

Key features:

React app runs on port 3000

Fully automated deployment via CodeBuild (no CodeDeploy needed)

LoadBalancer exposes the app externally

CloudWatch monitors build logs and app logs

2. Deployment Architecture

 +----------+       +-----------+       +--------+       +---------+       +--------------+
|  GitHub  | --->  | CodeBuild | --->  |  ECR   | --->  |  EKS    | --->  | LoadBalancer |
+----------+       +-----------+       +--------+       +---------+       +--------------+


Pipeline Steps:

Developer pushes code to GitHub

CodeBuild triggers automatically:

Installs dependencies

Builds Docker image

Pushes image to ECR

Deploys/updates Kubernetes deployment in EKS

LoadBalancer exposes the application externally

Logs and metrics are available via CloudWatch

3. Prerequisites

AWS free-tier account

AWS CLI installed and configured

IAM role for CodeBuild with permissions:

AmazonEKSClusterPolicy

AmazonEC2ContainerRegistryFullAccess

AmazonEKSWorkerNodePolicy

EKS cluster created and running

ECR repository created

4. Setup Instructions

 1. Clone Repository
 2. Build Docker Locally
 3. Push Docker Image to AWS ECR
 4. Kubernetes Deployment
 5. CodeBuild Setup
 6. codePipeline setup
 7. Access Application
 8. Monitoring
 
