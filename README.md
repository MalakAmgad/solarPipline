# Solar System Workflow Project

## Overview
This project demonstrates a fully automated **CI/CD pipeline** integrated with **GitOps principles** for managing Kubernetes workloads.  
The focus of the repository is not the application itself, but the **DevOps workflow** that builds, tests, deploys, and monitors the application in a cloud-native environment.

The included **Solar System web application** acts as a sample workload to validate and showcase the pipeline. Through this project, we simulate how real-world DevOps engineers set up infrastructure and workflows for production-ready applications.

---

## 🎯 Objectives
- Automate application **build, test, and deployment** using **GitHub Actions**.
- **Containerize** the application with **Docker** and publish images to a container registry.
- Manage workloads on **Amazon EKS (Elastic Kubernetes Service)** using **Helm charts**.
- Adopt **GitOps practices** with **ArgoCD**, enabling declarative and version-controlled deployments.
- Integrate **observability and monitoring** with **Prometheus, Grafana, and OpenTelemetry**.
- Provide a **reproducible, production-like setup** that demonstrates the complete DevOps lifecycle.

---

## ✨ Key Features
- ✅ End-to-end CI/CD pipeline using GitHub Actions.  
- ✅ Application containerization and registry integration.  
- ✅ Kubernetes deployment with Helm charts.  
- ✅ GitOps-powered continuous delivery via ArgoCD.  
- ✅ Real-time monitoring & metrics collection with Prometheus and Grafana.  
- ✅ Traceability and observability with OpenTelemetry.  
- ✅ Clear documentation and reproducible steps for learning and demonstration.

---

## 📂 What This Project Covers
1. **Continuous Integration (CI)**: Linting, testing, and building Docker images.  
2. **Continuous Deployment (CD)**: Automated deployment to Kubernetes through GitHub Actions.  
3. **Infrastructure as Code (IaC)**: Using Helm charts to define Kubernetes manifests.  
4. **GitOps**: Syncing manifests with ArgoCD for declarative deployments.  
5. **Monitoring & Observability**: Collecting metrics and logs for visibility.  

---

## 🔑 Why This Project Matters
Modern software teams require **reliable, automated pipelines** that reduce human error and accelerate delivery. This project demonstrates how different DevOps tools combine to create a scalable, resilient, and observable software delivery process.  
By following the documentation, you will learn how to:
- Set up pipelines from scratch.
- Deploy applications in Kubernetes clusters.
- Apply GitOps workflows.
- Monitor and observe cloud-native systems.

---

part for the diagram

## 🏗️ Architecture

The workflow integrates multiple DevOps tools and services into a unified pipeline.  
The following diagram illustrates the high-level architecture of the system:

![Architecture Diagram](./docs/architecture.png)


1. Developer pushes code changes to GitHub.
2. GitHub Actions runs automated workflows:
   - Build and test the app.
   - Containerize the app with Docker.
   - Push the image to the registry.
   - Package Helm charts for deployment.
3. ArgoCD continuously monitors the GitOps repo and syncs manifests to the EKS cluster.
4. The Solar System app is deployed inside Kubernetes pods.
5. Prometheus scrapes metrics from the cluster and Grafana visualizes them.
6. OpenTelemetry collects logs and traces for deeper observability.

---

## 🛠️ Tech Stack & Tools

This project integrates several DevOps tools and cloud-native technologies.  
Each component plays a critical role in building, deploying, and managing the Solar System application.

| Tool | Purpose | Why It’s Used |
|------|----------|---------------|
| **GitHub Actions** | Continuous Integration & Continuous Deployment (CI/CD) | Automates build, test, and deployment workflows directly from the GitHub repository. |
| **Docker** | Containerization | Packages the application into lightweight, portable containers for consistency across environments. |
| **Amazon EKS (Elastic Kubernetes Service)** | Kubernetes Cluster | Manages containerized workloads in a scalable and highly available cloud environment. |
| **Helm** | Kubernetes Package Manager | Simplifies deployment and management of Kubernetes manifests using reusable charts. |
| **ArgoCD** | GitOps Continuous Delivery | Automates deployment by syncing manifests from GitHub to the Kubernetes cluster. |
| **Prometheus** | Monitoring | Collects real-time metrics from Kubernetes workloads and infrastructure. |
| **Grafana** | Visualization | Provides interactive dashboards and alerts based on Prometheus metrics. |
| **OpenTelemetry** | Observability | Enables distributed tracing and logging for deeper visibility into system performance. |

---

## 🔧 Additional Utilities
- **Kubernetes CLI (kubectl)** → For direct interaction with the cluster.  
- **AWS CLI** → For managing AWS resources.  
- **Docker Hub / Amazon ECR** → For storing container images.  
- **draw.io / Excalidraw** → For visual diagrams included in documentation.  

---

## 🌐 References
- [GitHub Actions Docs](https://docs.github.com/actions)  
- [Docker Documentation](https://docs.docker.com/)  
- [Amazon EKS](https://aws.amazon.com/eks/)  
- [Helm](https://helm.sh/docs/)  
- [ArgoCD](https://argo-cd.readthedocs.io/en/stable/)  
- [Prometheus](https://prometheus.io/docs/introduction/overview/)  
- [Grafana](https://grafana.com/docs/)  
- [OpenTelemetry](https://opentelemetry.io/docs/)  

---

## 📂 Repository Structure

The repository is organized to separate concerns between the **application code** and the **DevOps workflows**.  
Below is a high-level view of the repo:

.
├── .github/workflows/ # GitHub Actions pipelines (CI/CD workflows)
├── app/ # Solar System sample application (frontend/backend)
│ ├── Dockerfile # Dockerfile for containerizing the app
│ └── src/ # Application source code
├── helm/ # Helm charts for Kubernetes deployments
│ ├── Chart.yaml # Helm chart metadata
│ ├── values.yaml # Default configuration values
│ └── templates/ # Kubernetes manifest templates
├── docs/ # Documentation assets (architecture diagrams, images, etc.)
├── .gitignore # Ignored files in Git
└── README.md # Project documentation


---

## 📖 Folder/Component Details
- **`.github/workflows/`**  
  Contains YAML files defining GitHub Actions pipelines for building, testing, and deploying the app.

- **`app/`**  
  Sample Solar System application code. Used as a practical workload to demonstrate the pipeline.

- **`helm/`**  
  Helm chart used to package and deploy the application to Kubernetes.

- **`docs/`**  
  Documentation files like architecture diagrams or setup guides.

- **`.gitignore`**  
  Specifies which files and folders to ignore in version control.

- **`README.md`**  
  Main documentation file (this file).

---

## ⚙️ CI/CD Workflow with GitHub Actions

This project uses **GitHub Actions** to implement Continuous Integration (CI) and Continuous Deployment (CD).  
Whenever code is pushed or a Pull Request is created, the pipeline is automatically triggered.

---

### 🏗️ Workflow Stages

1. **Checkout Code**
   - Uses the `actions/checkout` action to pull the latest code into the workflow runner.

2. **Build & Test**
   - Installs dependencies and runs tests (if defined for the app).
   - Ensures that the application is stable before containerization.

3. **Docker Build & Push**
   - Builds a Docker image from the application `Dockerfile`.
   - Tags the image with version and commit hash.
   - Pushes the image to a container registry (e.g., Docker Hub or AWS ECR).

4. **Helm Chart Packaging**
   - Packages Kubernetes manifests into a Helm chart.
   - Ensures deployment files are ready for Kubernetes.

5. **Deployment to Kubernetes**
   - Uses `kubectl` and/or ArgoCD to deploy the Helm chart into the EKS cluster.
   - Deployment is fully automated after pipeline success.

---
------------------
---
🔑 Key Features of the Pipeline

Automated: Every push/PR triggers validation and deployment.

Secure: Uses GitHub Secrets for Docker credentials and Kubernetes authentication.

Reproducible: Same workflow runs across environments, ensuring consistency.

Scalable: Can be extended with jobs for linting, security scans, or integration tests.

🔒 Secrets Used

DOCKER_USERNAME – Docker Hub or ECR username.

DOCKER_PASSWORD – Docker Hub or ECR password/token.

KUBE_CONFIG or AWS_CREDENTIALS – For authenticating with the EKS cluster.

---
## ☸️ Kubernetes & Helm Deployment

The **deployment stage** of the pipeline is handled using **Helm**, which simplifies Kubernetes resource management.  
Instead of manually applying multiple YAML manifests, Helm packages them into a reusable **chart**.

---

### 📦 Helm Chart Structure

helm/
├── Chart.yaml # Metadata about the chart (name, version, description)
├── values.yaml # Default values (e.g., image tag, replica count, service type)
└── templates/ # Kubernetes manifest templates (deployment, service, ingress, etc.)
├── deployment.yaml
├── service.yaml
└── ingress.yaml


---

### 🧩 Deployment Workflow
1. **Build & Push Docker Image**  
   The application is containerized and stored in a registry (Docker Hub or ECR).  

2. **Update Helm Values**  
   The pipeline updates the `values.yaml` file with the new Docker image tag.  

3. **Install/Upgrade Release**  
   Helm is used to either install the app (first time) or upgrade it (subsequent runs).  

---

🌐 Accessing the Application

The Helm chart defines a Service (ClusterIP / NodePort / LoadBalancer).

If using a LoadBalancer service (AWS EKS default), an external endpoint will be provisioned.

---

🔑 Benefits of Using Helm

Reusability → Charts can be reused across environments (dev, staging, prod).

Scalability → Easily adjust replicas, resources, and configs.

Versioning → Each release is tracked, enabling rollbacks if needed.

Simplicity → One command (helm upgrade) updates the entire deployment.

---

## 🔄 GitOps with ArgoCD

This project follows **GitOps principles** for managing Kubernetes deployments.  
Instead of applying changes directly to the cluster, all configurations are stored in **Git**, and **ArgoCD** ensures the cluster state matches the repository state.

---

### 🧭 What is GitOps?
- **Declarative**: Infrastructure and application definitions are written as code (YAML/Helm).  
- **Version-Controlled**: All manifests are stored in Git, providing full history and audit trails.  
- **Automated**: A GitOps operator (ArgoCD) continuously syncs the cluster with the Git repository.  
- **Reliable**: Any drift (difference between repo and cluster) is detected and can be auto-corrected.

---

### 🛠️ ArgoCD in This Project
1. Watches the **GitHub repository** for changes to manifests/Helm charts.  
2. Syncs changes automatically to the **Amazon EKS cluster**.  
3. Provides a **web UI and CLI** for monitoring, rollbacks, and manual syncs.  

---

🚀 GitOps Workflow

Developer commits code → triggers GitHub Actions.

CI builds & pushes Docker image → updates Helm values in Git.

ArgoCD detects changes in Git → applies updated Helm chart to EKS.

Application is redeployed automatically → cluster state always matches Git.

---

🎨 ArgoCD UI

ArgoCD provides a visual dashboard where you can:

View application health and sync status.

Compare live vs desired state.

Roll back to previous versions.

Trigger manual syncs if needed.

---

🔑 Benefits of GitOps in This Project

Full Traceability → Every deployment is linked to a Git commit.

Consistency → Same manifests are applied across environments.

Self-Healing → If cluster drifts from desired state, ArgoCD restores it.

Separation of Concerns → CI builds artifacts; CD (via ArgoCD) applies manifests.

---

## 📊 Monitoring & Observability

A critical part of DevOps pipelines is ensuring that applications are **observable** once deployed.  
This project integrates **Prometheus, Grafana, and OpenTelemetry** to provide full-stack monitoring.

---

### 📡 Prometheus (Metrics Collection)
- Scrapes metrics from Kubernetes pods, services, and nodes.  
- Stores time-series data such as CPU usage, memory, request latency, and error rates.  
- Uses exporters like **kube-state-metrics** and **node-exporter** to collect cluster health data.  

---

📈 Grafana (Visualization & Dashboards)

Connects to Prometheus as a data source.

Provides rich, interactive dashboards.

Can set up alerts for abnormal behaviors (e.g., high error rate, high latency).

✅ Example Dashboards:

Application response times.

Pod CPU/memory usage.

EKS cluster health.

Request success vs failure rates.

---
🔎 OpenTelemetry (Tracing & Logs)

Collects distributed traces across services (important for microservices).

Provides logs and spans to track how requests flow through the system.

Integrates with backends like Jaeger or Grafana Tempo for trace visualization.


🧩 Workflow

Application deployed on EKS exposes metrics and traces.

Prometheus scrapes metrics → stored in time-series DB.

Grafana queries Prometheus → shows dashboards and alerts.

OpenTelemetry collects traces/logs → provides request-level visibility.

🔑 Benefits

Real-time monitoring of application and cluster health.

Historical analysis of performance trends.

Proactive alerting on anomalies.

End-to-end visibility across metrics, logs, and traces.

---

📚 Additional Resources & References

Here are some resources and documentation links that can help you understand the tools, frameworks, and practices used in this project:

🔹 Core Technologies

Kubernetes Documentation https://kubernetes.io/docs/home/?utm_source=chatgpt.com
 – Official documentation for Kubernetes cluster orchestration.

Amazon EKS Documentation https://docs.aws.amazon.com/eks/?utm_source=chatgpt.com
 – AWS-managed Kubernetes service.

Docker Documentation https://docs.docker.com/?utm_source=chatgpt.com
 – Building, running, and managing containerized applications.

Helm Documentation https://helm.sh/docs/?utm_source=chatgpt.com
 – Package manager for Kubernetes deployments.

ArgoCD Documentation https://argo-cd.readthedocs.io/en/stable/?utm_source=chatgpt.com
 – GitOps continuous delivery for Kubernetes.

🔹 CI/CD & Automation

GitHub Actions Documentation https://docs.github.com/en/actions?utm_source=chatgpt.com
 – Automating workflows directly from GitHub.

CI/CD Best Practices https://martinfowler.com/articles/continuousIntegration.html?utm_source=chatgpt.com
 – Guide by Martin Fowler on CI/CD principles.

🔹 Observability

Prometheus Documentation https://prometheus.io/docs/introduction/overview/?utm_source=chatgpt.com
 – Monitoring and alerting toolkit.

Grafana Documentation https://grafana.com/docs/?utm_source=chatgpt.com
 – Visualization and analytics platform.

OpenTelemetry Documentation https://opentelemetry.io/docs/?utm_source=chatgpt.com
 – Standard for observability instrumentation.

🔹 GitOps Principles

GitOps Guide https://opengitops.dev/?utm_source=chatgpt.com
 – Best practices and principles for GitOps.

Weaveworks GitOps https://www.weave.works/technologies/gitops/?utm_source=chatgpt.com
 – GitOps pioneer resources.

 ---
