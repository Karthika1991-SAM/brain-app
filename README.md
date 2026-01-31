Brain Tasks App – Production Deployment on AWS EKS
1. 📘 Project Overview

This project is a React application deployed in a production-ready environment using modern DevOps tools and AWS cloud services.

🛠️ Technologies Used

Docker – Containerizes the application

AWS ECR – Stores Docker images

AWS EKS – Kubernetes cluster for running the application

AWS CodeBuild – CI/CD pipeline to build, push, and deploy automatically

✅ Key Features

React application runs on port 3000

Fully automated CI/CD deployment using CodeBuild (no CodeDeploy required)

Application is exposed externally using a Kubernetes LoadBalancer

CloudWatch is used to monitor build logs and application logs

2. 🏗️ Deployment Architecture


+----------+       +-----------+       +--------+       +---------+       +--------------+
|  GitHub  | --->  | CodeBuild | --->  |  ECR   | --->  |  EKS    | --->  | LoadBalancer |
+----------+       +-----------+       +--------+       +---------+       +--------------+



🔄 Pipeline Flow
    -Developer pushes code to GitHub
    -CodeBuild is triggered automatically:
    -Installs dependencies
    -Builds Docker image
    -Pushes Docker image to ECR
    -Deploys / updates the application in EKS using kubectl
    -LoadBalancer exposes the application to the internet
    -Logs and build details are available in CloudWatch

3. 📋 Prerequisites
   -AWS Free Tier account
   -AWS CLI installed and configured
   -IAM role for CodeBuild with the following permissions:
       -AmazonEKSClusterPolicy
       -AmazonEC2ContainerRegistryFullAccess
       -AmazonEKSWorkerNodePolicy
    -An EKS cluster created and running
    -An ECR repository created

4. ⚙️ Setup Instructions

4.1 Clone the Repository
4.2 Build Docker Image Locally 
4.3 Open in browser :http://localhost:3000
4.4 Push Docker Image to AWS ECR
4.5 Kubernetes Deployment
4.6 Kubernetes Services
4.7 Note the EXTERNAL-IP (LoadBalancer DNS) to access the application.
4.8 CodeBuild Setup
    -Create a CodeBuild project
    -Connect it to your GitHub repository
    -Use environment image: aws/codebuild/standard:7.0
    -Enable Privileged Mode (for Docker)
    -Add environment variables:
4.9 The pipeline will:
   - Build Docker image
   -Push image to ECR
   -Deploy/update application in EKS using kubectl

5 CodePipeline Setup (Optional)
   -Pipeline stages:
   -Source: GitHub
   -Build & Deploy: CodeBuild
   -On every commit, the application is automatically built and deployed to EKS.
   -Access the Application  using command kubectl get svc brain-tasks-service
   -loadbalancer url -aa5ab7cc27de14fc8b2a95f67023ed7a-305417844.ap-south-1.elb.amazonaws.com

6. 📊 Monitoring
    -CodeBuild Logs → Available in AWS CloudWatch

