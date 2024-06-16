## Overview
This project involves creating a Spring Boot application that connects to a database to store user details. The application is deployed using Jenkins pipeline on a Kubernetes cluster.

![image](https://github.com/Loki-1/SpringBootApp/assets/134843197/3a6a4daa-95e6-4efb-9aec-9079fc1e65cf)


### Tools Used
- **Source Code Management:** GitHub
- **Build Tool:** Maven
- **Code Quality Analysis:** SonarQube
- **Artifact Repository:** Nexus
- **Continuous Integration:** Jenkins
- **Containerization:** Docker
- **Container Registry:** DockerHub
- **Container Orchestration:** Kubernetes


![image](https://github.com/Loki-1/SpringBootApp/assets/134843197/cefaa304-280b-4357-9867-052ad3200783)



### Application Components:
**Spring Boot Application:** Handles user input and interacts with the database.

**Database (e.g., MySQL, PostgreSQL):** Stores user information.

### Deployment Architecture:

**Kubernetes Cluster:** Orchestrates containers.

***Pods:***
* One for the database (e.g., MySQL, PostgreSQL).
* One for the Spring Boot application.

***Services:***
- To expose the Spring Boot application internally or externally.
- **External url :** [http://localhost:<node_port>/](http://localhost:<node_port>/)
  
![image](https://github.com/Loki-1/SpringBootApp/assets/134843197/988338b5-ed31-4980-a2bb-a6eb7c6ec15b)

### Development Workflow
#### Source Code Management:
Code is managed in GitHub repositories.

#### Build and Package:
Maven is used to build packages (pom.xml manages dependencies and build configurations).

#### Code Quality Analysis:
SonarQube is integrated to analyze code quality and identify issues.
![image](https://github.com/Loki-1/SpringBootApp/assets/134843197/6a38b2c6-a1d1-4cc9-ae84-91dd4b76c16d)
![image](https://github.com/Loki-1/SpringBootApp/assets/134843197/8b18a98e-b7b2-4d89-99d3-33b9eac5bc7d)

#### Artifact Repository:
Nexus serves as the artifact repository for storing Maven packages.
![image](https://github.com/Loki-1/SpringBootApp/assets/134843197/d65f9747-90e5-49c0-8c12-4a394538ae1c)

#### Continuous Integration:
Jenkins pipeline automates the CI/CD process.
**Stages:**
Build: Maven builds the application.
SonarQube Scan: Code quality analysis.
Nexus Repo storage: store atifacts inti nexus repo
Docker Build: Build Docker images.
Docker Push: Push Docker images to Docker Hub.
Kubernetes Deployment: Deploy to Kubernetes cluster.

![image](https://github.com/Loki-1/SpringBootApp/assets/134843197/683110c3-0d48-4641-a920-5a4e01e569ef)

#### Containerization:
Docker is used to containerize the application.
Dockerfiles define the container images and we store those images on dockerhub.
![image](https://github.com/Loki-1/SpringBootApp/assets/134843197/bf15e7b5-01fa-4996-94b1-38cbf02d1423)

### Prerequisites:
- Kubernetes cluster setup.
- Jenkins installation and configuration.
- Docker and Docker Hub accounts.

### Configuration Files:
- `pom.xml`: Maven build configuration.
- `Dockerfile`: Docker image configuration.
- `Jenkinsfile`: Jenkins pipeline groovy script
- **Kubernetes Manifests:**
  - `deployment.yaml`: Deployment configuration.
  - `service.yaml`: Service configuration.

### Troubleshooting and Monitoring
- **Logging:**
  - Utilize Kubernetes logging (e.g., Fluentd, Elasticsearch, Kibana stack).
- **Monitoring:**
  - Use Kubernetes monitoring tools (e.g., Prometheus, Grafana).

### Future Improvements
- Implement CI/CD pipelines for feature branches.
- Enhance Kubernetes deployment with Helm charts.
- Integrate automated testing (unit, integration, E2E).


