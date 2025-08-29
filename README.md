# GitAction_SolarSystem

A Solar System sample application used to demonstrate a fully automated DevOps pipeline. This repository showcases CI/CD practices, GitOps, infrastructure as code, containerization, and observability—all applied to a simple web app.

---

## Project Overview

This project uses a Solar System web application as the workload to illustrate a complete DevOps lifecycle, highlighting:

- Automated build, test, and deployment using **GitHub Actions**
- Containerization with **Docker**
- Kubernetes deployment via **Helm** charts
- GitOps with **ArgoCD**
- Infrastructure provisioning using **Terraform**
- Monitoring via **Prometheus** and **Grafana**

---

## Architecture Overview

```
Developer → GitHub → GitHub Actions → Docker image registry → Helm chart → ArgoCD → EKS cluster → Solar System App
                                         ↓
                              (Helm + ArgoCD deploy to Kubernetes)
                                         ↓
                            Prometheus scrapes metrics → Grafana dashboards
```

---

## Technology Stack

| Category              | Tools / Technologies                         |
|-----------------------|----------------------------------------------|
| CI/CD                 | GitHub Actions (including `docker.yaml`)     |
| Containerization      | Docker, Dockerfile                           |
| Infrastructure as Code| Terraform (under `Terraform/`)               |
| Package Manager       | Helm (chart in `helm/solar-system-chart/`)   |
| GitOps                | ArgoCD                                       |
| Deployment Target     | Kubernetes on AWS EKS (assumed)              |
| Monitoring            | Prometheus & Grafana (diagrams present)      |

---

## Repository Structure

```
.gitignore
.dockerignore
Dockerfile
docker.yaml
app.js
app-controller.js
app-test.js
index.html
package.json
package-lock.json

.github/
└── workflows/

helm/
└── solar-system-chart/

Terraform/

images/
```

- **`.github/workflows/`**: GitHub Actions workflows.  
- **`docker.yaml`**: Workflow to build and push Docker images.  
- **`Dockerfile`**: Defines how the Solar System app is containerized.  
- **Application code and tests**: Root-level files (`app.js`, `app-controller.js`, `app-test.js`, `index.html`, `package.json`, etc.).  
- **`helm/solar-system-chart/`**: Helm chart with chart metadata, values, and Kubernetes templates.  
- **`Terraform/`**: Terraform code to provision AWS infrastructure.  
- **`images/`**: Visual assets such as architecture diagrams.  

---

## CI/CD Workflow

- **Build & Test**: Application tests run via GitHub Actions.  
- **Docker Build & Push**: Container images are built using `Dockerfile` and pushed via `docker.yaml`.  
- **Terraform**: Provision infrastructure (EKS, networking, etc.) with Terraform.  
- **Helm Deployment**: Package and deploy Kubernetes workloads using the Helm chart.  
- **ArgoCD**: Sync Helm manifests to the cluster for GitOps-driven deployment.  

---

## Monitoring & Observability

The `images/` folder contains diagrams that show the integration of **Prometheus** and **Grafana** for observability.

---

## Visual Assets

Refer to the `images/` folder for architecture and workflow diagrams illustrating the CI/CD pipeline, containerization, infrastructure setup, and GitOps deployment flow.

---
