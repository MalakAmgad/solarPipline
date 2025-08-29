# GitAction_SolarSystem

The **GitAction_SolarSystem** project is a DevOps-focused implementation that uses a Solar System sample application to demonstrate end-to-end automation.  
It shows how modern DevOps practices can be applied around a simple web app using CI/CD, containerization, Kubernetes, GitOps, and monitoring.

---

## 🚀 Project Overview

This repository contains a Node.js based **Solar System web application** along with the complete DevOps toolchain needed to:

- **Develop & Test** the application.
- **Containerize** it with Docker.
- **Automate pipelines** using GitHub Actions.
- **Provision infrastructure** with Terraform.
- **Deploy** with Helm charts and ArgoCD.
- **Monitor & visualize** with Prometheus and Grafana.

The repo is structured so that each major DevOps component is isolated in its own directory or file.

---

## 🏗️ Architecture

```
Developer → GitHub → GitHub Actions → Docker Image Registry → Helm Chart → ArgoCD → EKS Cluster → Solar System App
                                         ↓
                              (Helm + ArgoCD deploy to Kubernetes)
                                         ↓
                           Prometheus scrapes metrics → Grafana dashboards
```

- **GitHub Actions**: Triggers on code changes and builds/test the app.  
- **Docker**: Packages the app into a container.  
- **Terraform**: Manages infrastructure provisioning (e.g., AWS EKS cluster).  
- **Helm**: Packages Kubernetes manifests for easy deployment.  
- **ArgoCD**: Automates continuous delivery with GitOps.  
- **Prometheus & Grafana**: Provide monitoring and observability.  

---

## 🛠️ Technology Stack

| Category                | Tools / Technologies                         |
|-------------------------|----------------------------------------------|
| Application             | Node.js (JavaScript)                        |
| CI/CD                   | GitHub Actions (`.github/workflows/`)       |
| Containerization        | Docker (`Dockerfile`)                       |
| Infrastructure as Code  | Terraform (`Terraform/`)                    |
| Package Manager         | Helm (`helm/solar-system-chart/`)           |
| GitOps                  | ArgoCD                                      |
| Monitoring              | Prometheus & Grafana (diagrams available)   |
| Configuration           | YAML (for Helm & workflows)                 |

---

## 📂 Repository Structure

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

### 🔹 Root-level files
- **app.js** → Main application entry point.  
- **app-controller.js** → Handles application logic.  
- **app-test.js** → Unit tests for the application.  
- **index.html** → Frontend interface for the Solar System app.  
- **package.json & package-lock.json** → Node.js dependencies and project metadata.  
- **Dockerfile** → Defines containerization steps.  
- **docker.yaml** → GitHub Actions workflow to build & push Docker images.  
- **.gitignore / .dockerignore** → Ignore unnecessary files in Git and Docker.  

### 🔹 `.github/workflows/`
Contains GitHub Actions pipelines for building, testing, and deploying.  

### 🔹 `helm/solar-system-chart/`
Helm chart for Kubernetes deployment:  
- `Chart.yaml` → Metadata for the Helm chart.  
- `values.yaml` → Default configuration values.  
- `templates/` → Kubernetes manifest templates.  

### 🔹 `Terraform/`
Contains Terraform configuration for infrastructure provisioning (e.g., EKS, networking).  

### 🔹 `images/`
Contains diagrams and visual assets (pipeline architecture, infrastructure, monitoring setup).  

---

## ⚙️ Installation & Local Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/AbdullahWahdan/GitAction_SolarSystem.git
   cd GitAction_SolarSystem
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Run the application locally**
   ```bash
   npm start
   ```
   Then open your browser at `http://localhost:3000` (or the port defined in the app).

4. **Run tests**
   ```bash
   npm test
   ```

---

## 🐳 Docker Usage

1. **Build the image**
   ```bash
   docker build -t solar-system-app .
   ```

2. **Run the container**
   ```bash
   docker run -p 3000:3000 solar-system-app
   ```

3. Access the app at: [http://localhost:3000](http://localhost:3000)

---

## 🔄 CI/CD Workflow (GitHub Actions)

The repository includes GitHub Actions workflows located in `.github/workflows/`.

- **On push/PR** → Run tests (`app-test.js`).  
- **Build & Push** → Creates Docker image via `Dockerfile` and pushes to registry.  
- **Deploy** → Uses Helm chart & ArgoCD to update Kubernetes cluster.  

---

## 🎛️ Helm Deployment

The Helm chart under `helm/solar-system-chart/` is responsible for Kubernetes deployments.

### Install/Upgrade Release
```bash
helm upgrade --install solar-system helm/solar-system-chart/
```

### Configuration
- Default values are in `values.yaml`.  
- Modify parameters (replicas, image version, ports) as needed.  

---

## 🌍 Infrastructure (Terraform)

The `Terraform/` directory defines cloud infrastructure:  
- **Cluster provisioning** (EKS or similar).  
- **Networking components**.  
- **IAM roles/policies**.  

### Usage
```bash
cd Terraform
terraform init
terraform plan
terraform apply
```

---

## 📊 Monitoring & Observability

- **Prometheus** scrapes metrics from the app and Kubernetes cluster.  
- **Grafana** provides dashboards for visualization.  
- Architecture and monitoring diagrams are available under `images/`.

---

## 🖼️ Visual Assets

The `images/` directory contains diagrams illustrating:  
- CI/CD pipeline flow.  
- Infrastructure architecture.  
- Monitoring setup.  

Embed them in documentation as needed, for example:  

```markdown
![Architecture Diagram](images/architecture.png)
```

---

## 🤝 Contribution

1. Fork the repo.  
2. Create a new branch (`feature/your-feature`).  
3. Commit changes.  
4. Push and open a Pull Request.  

---

## 📌 Summary

This repository is a complete DevOps demonstration around a Solar System app. It provides a hands-on example of:

- Building a Node.js application  
- Automating pipelines with GitHub Actions  
- Containerizing with Docker  
- Deploying with Helm & ArgoCD  
- Provisioning with Terraform  
- Monitoring with Prometheus & Grafana  

---
