# Sample Spring Boot CI/CD Pipeline with Jenkins

This repository contains a sample Spring Boot application integrated with a CI/CD pipeline
using Jenkins. The pipeline automates the build, test, and deployment processes, including
OWASP Dependency Check, SonarQube Analysis, Docker image creation, vulnerability scanning,
and deployment to a staging environment.

# Jenkins Pipeline Overview

The Jenkins pipeline is defined in the Jenkinsfile. It consists of the following stages:

1. **Code Checkout**: Clones the repository to the Jenkins workspace.
   
2. **OWASP Dependency Check**: Performs a security audit of project dependencies using OWASP Dependency Check.
   
3. **SonarQube Analysis**: Analyzes the code quality using SonarQube.
   
4. **Clean & Package**: Cleans the project and packages it into a JAR file.
   
5. **Docker Build & Push**: Builds a Docker image of the application, tags it with latest, and pushes it to DockerHub.
    
6. **Vulnerability Scanning**: Scans the Docker image for vulnerabilities using Trivy.
    
7. **Staging**: Deploys the application and its dependencies using Docker Compose to a staging environment.

# Prerequisites

Before running the pipeline, ensure the following prerequisites are met:

- Jenkins is set up and configured with necessary plugins (e.g., Docker Pipeline, SonarQube Scanner).
- SonarQube server is running and configured in Jenkins.
- Docker is installed on the Jenkins agent.
- DockerHub credentials are configured in Jenkins for pushing Docker images.
