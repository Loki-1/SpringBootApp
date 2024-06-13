## Overview
This project involves creating a Spring Boot application that connects to a database to store user details. The application is deployed using Jenkins pipeline on a Kubernetes cluster.
![image](https://github.com/Loki-1/SpringBootApp/assets/134843197/336fd659-b823-4141-86e0-cc6645a3ca22)
### Tools Used
**Source Code Management:** GitHub, 
**Build Tool:** Maven, 
**Code Quality Analysis:** SonarQube, 
**Artifact Repository:** Nexus, 
**Continuous Integration:** Jenkins, 
**Containerization:** Docker, 
**Container Registry:** Docker Hub, 
**Container Orchestration:** Kubernetes.
![image](https://github.com/Loki-1/SpringBootApp/assets/134843197/da0df3ec-e3ad-42ca-8c4d-5d1ee6a76708)

### Architecture

### Application Components:
**Spring Boot Application:** Handles user input and interacts with the database.

**Database (e.g., MySQL, PostgreSQL):** Stores user information.

### Deployment Architecture:

**Kubernetes Cluster:** Orchestrates containers.

**Pods:**
* One for the database (e.g., MySQL, PostgreSQL).
* One for the Spring Boot application.

**Services:**
To expose the Spring Boot application internally or externally.
         **External url :** http://<local_host>:<NodePort_num>/


### Development Workflow
#### Source Code Management:
Code is managed in GitHub repositories.

#### Build and Package:
Maven is used to build packages (pom.xml manages dependencies and build configurations).

Code Quality Analysis:

SonarQube is integrated to analyze code quality and identify issues.
Artifact Repository:

Nexus serves as the artifact repository for storing Maven packages.
Continuous Integration:

Jenkins pipeline automates the CI/CD process.
Stages:
Build: Maven builds the application.
SonarQube Scan: Code quality analysis.
Docker Build: Build Docker images.
Docker Push: Push Docker images to Docker Hub.
Kubernetes Deployment: Deploy to Kubernetes cluster.
Containerization:

Docker is used to containerize the application.
Dockerfiles define the container images.
Deployment to Kubernetes:

Jenkins pipeline manages deployment to Kubernetes.
Kubernetes manifests (deployment.yaml, service.yaml) define resources and configurations.
Deployment Process
Jenkins Pipeline:
Triggered on code push to GitHub or manually.
Builds the application using Maven.
Runs SonarQube analysis for code quality.
Builds Docker image and pushes to Docker Hub.
Deploys application to Kubernetes cluster using Kubernetes manifests.
Setup and Configuration
Prerequisites:

Kubernetes cluster setup.
Jenkins installation and configuration.
Docker and Docker Hub accounts.
Configuration Files:

pom.xml: Maven build configuration.
Dockerfile: Docker image configuration.
Kubernetes Manifests:
deployment.yaml: Deployment configuration.
service.yaml: Service configuration.
Troubleshooting and Monitoring
Logging:

Utilize Kubernetes logging (e.g., Fluentd, Elasticsearch, Kibana stack).
Monitoring:

Use Kubernetes monitoring tools (e.g., Prometheus, Grafana).
Future Improvements
Implement CI/CD pipelines for feature branches.
Enhance Kubernetes deployment with Helm charts.
Integrate automated testing (unit, integration, E2E).
References
GitHub repository link.
Jenkins pipeline scripts.
Kubernetes manifests.


![image](https://github.com/Loki-1/SpringBootApp/assets/134843197/c52a215d-0ca5-4a0d-9216-61708cf944a3)

![image](https://github.com/Loki-1/SpringBootApp/assets/134843197/336fd659-b823-4141-86e0-cc6645a3ca22)

