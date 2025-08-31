# Solar System Workflow Project

![CI/CD Pipeline](https://github.com/AbdullahWahdan/GitAction_SolarSystem/actions/workflows/docker.yaml/badge.svg)

![Docker](https://img.shields.io/badge/Docker-Ready-blue?logo=docker)
![Helm](https://img.shields.io/badge/Helm-Charts-blue?logo=helm)
![Terraform](https://img.shields.io/badge/Terraform-Infrastructure-blueviolet?logo=terraform)
![ArgoCD](https://img.shields.io/badge/GitOps-ArgoCD-brightgreen?logo=argo)


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
- Integrate **observability and monitoring** with **Prometheus and Grafana**.
- Provide a **reproducible, production-like setup** that demonstrates the complete DevOps lifecycle.

---

## ✨ Key Features
- ✅ End-to-end CI/CD pipeline using GitHub Actions.  
- ✅ Application containerization and registry integration.  
- ✅ Kubernetes deployment with Helm charts.  
- ✅ GitOps-powered continuous delivery via ArgoCD.  
- ✅ Real-time monitoring & metrics collection with Prometheus and Grafana.  
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

diagram place///


1. Developer pushes code changes to GitHub.
2. GitHub Actions runs automated workflows:
   - Build and test the app.
   - Containerize the app with Docker.
   - Push the image to the registry.
   - Package Helm charts for deployment.
3. ArgoCD continuously monitors the GitOps repo and syncs manifests to the EKS cluster.
4. The Solar System app is deployed inside Kubernetes pods.
5. Prometheus scrapes metrics from the cluster and Grafana visualizes them.

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

---

## 📂 Repository Structure

The repository is organized to separate concerns between the **application code** and the **DevOps workflows**.  
Below is a high-level view of the repo:

GitAction_SolarSystem/
```
├── .github/
│ └── workflows/
│ └── main_pipeline.yaml
│ └── unit-test.yaml
│ └── coverage.yaml
│ └── docker.yaml
│ └── trivy.yaml
│ └── terraform.yaml
│ └── deploy.yaml
│ └── observability.yaml
│ └── argocd-deploy.yaml
├── Terraform/
│ └── infastructure-modules
│ └── team-01
├── argo/
│ └── application.yaml
├── helm/
│ └── solar-system-chart/
│ └── .helmignore
│ └── Chart.yaml
│ └── values.yaml
│ └── templates/
│ └────  _helpers.tpl
│ └────  NOTES.txt
│ └────  deployment.yaml
│ └────  hpa.yaml
│ └────  ingress.yaml
│ └────  service.yaml
│ └────  serviceaccount.yaml
│ └────  tests \
│ └───────  test-connection.yaml
├── images/
│ └── pictures
├── app.js
├── app-test.js
├── app-controller.js
├── .gitignore # Git ignore rules
├── Dockerfile
├── index.html
├── .dockerignore
├── package.json # npm dependencies and scripts
├── package-lock.json # Lock file for dependencies
└── README.md # Project documentation
```

---

## 📖 Folder / Component Details

- **`.github/workflows/`**  
  GitHub Actions workflow files and reusable workflows for CI/CD. (Workflows live here; some pipeline helpers/workflow files may also be present as top-level workflow YAMLs.)

- **`docker.yaml` (root)**  
  A workflow visible in the repository used to build and push Docker images. See the repo root for its YAML. :contentReference[oaicite:10]{index=10}

- **`Dockerfile` (root)**  
  Builds the Solar System sample application image.

- **Application files (root)**  
  `app.js`, `app-controller.js`, `app-test.js`, `index.html`, `package.json` — the sample application's code and tests live at repository root (not inside `app/`). :contentReference[oaicite:11]{index=11}

- **`helm/solar-system-chart/`**  
  Helm chart for deploying the application. Contains `Chart.yaml`, `values.yaml`, and `templates/`. :contentReference[oaicite:12]{index=12}

- **`Terraform/team-01/`**  
  Terraform code used to provision cloud infrastructure (EKS/VPC/IAM, etc.). :contentReference[oaicite:13]{index=13}

- **`images/`**  
  Diagram files and other documentation assets (place architecture diagram here as `images/architecture.png`). :contentReference[oaicite:14]{index=14}

---

## ⚙️ CI/CD Workflow with GitHub Actions

This repository uses GitHub Actions for CI/CD and security scanning. Workflow files are primarily located under `.github/workflows/`. In addition, a `docker.yaml` workflow is present in the repo root and is used for image build/push steps. See the repository tree for the exact, current workflow filenames and contents. :contentReference[oaicite:17]{index=17}


---

### 🏗️ Workflows Overview

- **`main_pipeline.yaml`** → Orchestrates all jobs (build, test, scan, deploy).
- **`docker.yaml`** → Builds and pushes Docker images to both Docker Hub and GitHub Container Registry (GHCR).
- **`coverage.yaml`** → Runs test coverage analysis on the application.
- **`trivy.yml`** → Scans for vulnerabilities in dependencies and Docker images.
- **`argocd-deploy.yaml`** → Triggers ArgoCD sync to deploy Helm charts to Kubernetes.
- **`terraform.yaml`** → Provisions AWS infrastructure (e.g., EKS cluster, VPCs, IAM roles) using Terraform.

---

### 🧩 Workflow Stages (as executed in `main_pipeline.yaml`)

1. **Checkout Code**
   - Uses `actions/checkout` to pull the latest source code.

2. **Build & Test**
   - Runs application unit tests and coverage (`coverage.yaml`).

3. **Docker Build & Push**
   - Builds Docker image from `app/Dockerfile`.
   - Runs a live container smoke test (`/live` endpoint).
   - Pushes image to:
     - **Docker Hub** (credentials from secrets `DOCKER_USERNAME`, `DOCKER_PASSWORD`)
     - **GitHub Container Registry (GHCR)** (credentials from `GHCR_USERNAME`, `GHCR_TOKEN`)

4. **Security Scanning with Trivy**
   - Scans both source code and Docker images for vulnerabilities.
   - Fails the pipeline if critical CVEs are found.

5. **Helm Chart Packaging**
   - Packages Kubernetes manifests from the `helm/` directory.

6. **ArgoCD Sync**
   - Deploys updated Helm chart to Amazon EKS via `argocd-deploy.yaml`.

7. **Terraform Infrastructure**
   - Optionally provisions AWS resources (`Terraform/team-01`) before application deployment.

---

### 🔒 Secrets Used

- `DOCKER_USERNAME`, `DOCKER_PASSWORD` → Docker Hub credentials  
- `GHCR_USERNAME`, `GHCR_TOKEN` → GitHub Container Registry credentials  
- `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `AWS_REGION` → AWS credentials for Terraform & EKS  
- `ARGOCD_SERVER`, `ARGOCD_AUTH_TOKEN` → ArgoCD API access for GitOps sync  
  

## 🔐 Security Scanning (Trivy)

This repository runs container and dependency vulnerability scanning with **Trivy** as part of CI/CD.

- **Where it lives:** `.github/workflows/trivy.yml`
- **How it runs:** Called from the main pipeline as a reusable workflow (see `.github/workflows/main_pipeline.yaml`, job `security`).
- **What it scans:**
  - The **repository filesystem** (dependencies / IaC) for known CVEs.
  - The **Docker image** built for this commit before publishing.
- **Outcome:** Scan results are attached as workflow artifacts; if critical issues are detected (as configured in `trivy.yml`), the pipeline fails and downstream jobs are blocked.

### View results in GitHub Actions
1. Go to **Actions → Main Pipeline** for the commit.
2. Open the **security** job.
3. Download the attached Trivy report artifacts if present.


---
## ☸️ Kubernetes & Helm Deployment

The **deployment stage** of the pipeline is handled using **Helm**, which simplifies Kubernetes resource management.  
Instead of manually applying multiple YAML manifests, Helm packages them into a reusable **chart**.

---

### 📦 Helm Chart Structure
```
helm/
├── Chart.yaml # Metadata about the chart (name, version, description)
├── values.yaml # Default values (e.g., image tag, replica count, service type)
└── templates/ # Kubernetes manifest templates (deployment, service, ingress, etc.)
├── deployment.yaml
├── service.yaml
└── ingress.yaml
```

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
This project integrates **Prometheus** and **Grafana** to provide monitoring and visualization of the Solar System app and Kubernetes cluster.

---

### 📡 Prometheus (Metrics Collection)
- Scrapes metrics from Kubernetes pods, services, and nodes.  
- Collects key time-series data such as CPU usage, memory consumption, request latency, and error rates.  
- Uses exporters like **kube-state-metrics** and **node-exporter** for cluster-level health.  

---

### 📈 Grafana (Visualization & Dashboards)
- Connects to Prometheus as a data source.  
- Provides interactive dashboards for:
  - Application response times  
  - Pod CPU/memory usage  
  - EKS cluster health  
  - Request success vs failure rates  
- Can be configured with **alerts** to detect anomalies (e.g., high error rate, resource saturation).  

---

### 🧩 Workflow
1. The application is deployed into EKS via Helm/ArgoCD.  
2. Prometheus scrapes metrics from workloads and cluster components.  
3. Grafana queries Prometheus and visualizes data on dashboards.  

---

### 🔑 Benefits
- **Real-time monitoring** of workloads and cluster health.  
- **Historical analysis** of performance and reliability trends.  
- **Proactive alerting** to detect issues early.  
- **Single-pane visibility** across app and infrastructure metrics.  

---

📚 Additional Resources & References

Here are some resources and documentation links that can help you understand the tools, frameworks, and practices used in this project:

🔹 Core Technologies

Kubernetes Documentation https://kubernetes.io/docs/home/
 – Official documentation for Kubernetes cluster orchestration.

Amazon EKS Documentation https://docs.aws.amazon.com/eks/
 – AWS-managed Kubernetes service.

Docker Documentation https://docs.docker.com/?
 – Building, running, and managing containerized applications.

Helm Documentation https://helm.sh/docs/
 – Package manager for Kubernetes deployments.

ArgoCD Documentation https://argo-cd.readthedocs.io/en/stable/
 – GitOps continuous delivery for Kubernetes.

🔹 CI/CD & Automation

GitHub Actions Documentation https://docs.github.com/en/actions
 – Automating workflows directly from GitHub.

CI/CD Best Practices https://martinfowler.com/articles/continuousIntegration.html
 – Guide by Martin Fowler on CI/CD principles.

🔹 Observability

Prometheus Documentation https://prometheus.io/docs/introduction/overview/
 – Monitoring and alerting toolkit.

Grafana Documentation https://grafana.com/docs/
 – Visualization and analytics platform.

🔹 GitOps Principles

GitOps Guide https://opengitops.dev/
 – Best practices and principles for GitOps.

Weaveworks GitOps https://www.weave.works/technologies/gitops/
 – GitOps pioneer resources.

 ---
