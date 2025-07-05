# Enterprise Java CI/CD Pipeline

This repository contains the source code and CI/CD pipeline for a production-ready Java microservice, built with Spring Boot and Maven, and deployed using a fully automated DevOps workflow.

## 🚀 Project Overview

- **Language/Framework:** Java 17, Spring Boot
- **Build Tool:** Maven
- **CI/CD:** Jenkins
- **Code Quality:** SonarQube
- **Containerization:** Docker
- **Image Registry:** AWS ECR
- **Deployment:** Kubernetes (EKS) via GitOps (Argo CD)
- **Monitoring:** Prometheus & Grafana

## 📦 Repository Structure

app/ # Java Spring Boot application code

src/

pom.xml

Dockerfile

README.md

cicd/ # Jenkins pipeline and automation scripts

Jenkinsfile

docs/ # Documentation and diagrams


## ⚙️ How the Pipeline Works

1. **Code Commit:**  
   Developers push code to this repository (main branch).

2. **Jenkins Pipeline:**  
   - Triggers on code push.
   - Runs Maven build and tests.
   - Performs static code analysis with SonarQube.
   - Builds a Docker image and pushes it to AWS ECR.
   - Updates the image tag in the [GitOps repo](https://github.com/HeenaDania/enterprise-java-gitops).

3. **Argo CD (in EKS):**  
   - Watches the GitOps repo for changes.
   - Automatically deploys the new image to the Kubernetes cluster.

4. **Monitoring:**  
   - Application exposes Prometheus metrics at `/actuator/prometheus`.
   - Metrics are visualized in Grafana.

## 🛠️ Key Files

- `app/Dockerfile` – Containerizes the Spring Boot app.
- `cicd/Jenkinsfile` – Defines the Jenkins pipeline.
- `app/pom.xml` – Maven dependencies and plugins.

## 📝 How to Run Locally

cd app
mvn clean package
docker build -t myapp:latest .
docker run -p 8080:8080 myapp:latest
Visit [http://localhost:8080](http://localhost:8080)

## 🧪 Testing

Run unit tests with: mvn test


## 🧹 Code Quality

SonarQube is integrated. To analyze code locally:

mvn sonar:sonar

(Requires SonarQube server running)

## 📈 Monitoring

After deployment, Prometheus scrapes `/actuator/prometheus` for metrics.  
Grafana dashboards visualize application and cluster health.

## 📚 Documentation

- [Project Report](../docs/Project_Report.md)
- [System Architecture](../docs/Architecture.png)

---

**Questions or contributions? Open an issue or pull request!**
