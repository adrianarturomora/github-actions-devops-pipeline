# GitHub Actions DevOps Pipeline
A full DevOps CI/CD pipeline demonstrating automated build, security scanning, Docker image management, and deployment to Azure Kubernetes Service (AKS) using GitHub Actions.

## Project Overview
This project showcases my ability to implement end-to-end DevOps automation for a Node.js web application. 

The pipeline covers:

- Continuous Integration (CI) using GitHub Actions
- Automated testing and dependency management
- Containerization using Docker
- Vulnerability scanning with Trivy
- Version tagging of Docker images
- Deployment to Azure Kubernetes Service (AKS)
- Monitoring deployment status and service availability

This project highlights practical skills in CI/CD, cloud deployment, and DevOps best practices, making it a strong demonstration of my DevOps and cloud engineering capabilities.

## Features

**1. Continuous Integration with GitHub Actions**
- Automated workflow triggers on `push` and `pull_request` events
- Installs Node.js dependencies and runs unit tests
- Ensures code quality before building the Docker image

**2. Docker Containerization**
- Packages the Node.js app into a Docker container
- Uses a `Dockerfile` optimized for Node.js
- Tags images automatically with `latest` and Git commit SHA

**3. Security Scanning with Trivy**
- Automatically scans Docker images for vulnerabilities
- Reports any findings while allowing the pipeline to continue for development purposes

**4. Deployment to Azure Kubernetes Service (AKS)**
- Deploys the Docker image to a fully managed AKS cluster
- Creates a LoadBalancer service to expose the application publicly
- Monitors pods to ensure the app is running successfully

**5. Automated Docker Image Management**
- Pushes Docker images to GitHub Container Registry (GHCR)
- Uses commit SHA for unique versioning of images
- Ensures consistent and reproducible deployments

## Project Walkthrough

**1. Repository Setup**
- I created a GitHub repository `github-actions-devops-pipeline` and cloned it locally.

**2. Node.js Application**
- I initialized a Node.js project and created a simple HTTP server.
- I added basic tests to validate functionality.
  
**3. GitHub Actions CI Pipeline**
- I created `.github/workflows/ci.yml` for the CI/CD workflow.
- Configured steps for:
    * Code checkout
    * Node.js setup
    * Dependency installation
    * Running tests
    * Docker image build
    * Trivy vulnerability scanning
    * GHCR login and image push

**4. Docker Containerization**
- I wrote a `Dockerfile` for the Node.js app.
- Built and tested the Docker image locally.
- Pushed the image to GHCR.

**5. Trivy Security Scan**
- I added Trivy scanning in the CI pipeline.
- Configured exit code to allow the workflow to continue while reporting vulnerabilities.

**6. Deployment to AKS**
- I created an AKS cluster in Azure.
- Wrote Kubernetes manifests (`deployment.yaml` and `service.yaml`) for the app.
- Applied manifests with `kubectl` to deploy the app.
- Verified pods are running and exposed via a LoadBalancer.

**7. End-to-End CI/CD**
- Any push to the `main` branch automatically builds, scans, and pushes a new Docker image.
- Deployment to AKS can also be automated via GitHub Actions.

## Tech Stack & Tools

- Languages & Frameworks: Node.js, JavaScript
- CI/CD & DevOps: GitHub Actions, Docker, Trivy
- Cloud & Orchestration: Azure Kubernetes Service (AKS), kubectl
- Container Registry: GitHub Container Registry (GHCR)
- Testing & Quality: npm test, automated workflow checks

## How to Run Locally

1. Clone the repository:
```plaintext
git clone https://github.com/adrianarturomora/github-actions-devops-pipeline.git
cd github-actions-devops-pipeline
```
2. Install dependencies:
```plaintext
npm install
```
3. Run the app:
```plaintext
npm start
```
Access the app at `http://localhost:3000/`.

## How to Deploy on AKS

1. Create an AKS cluster:
```plaintext
az aks create \
  --resource-group devops-rg \
  --name devops-aks \
  --node-count 1 \
  --generate-ssh-keys
```

2. Get AKS credentials:
```plaintext
az aks get-credentials --resource-group devops-rg --name devops-aks
```

3. Apply Kubernetes manifests:
```plaintext
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```
4. Get the external IP:
```plaintext
kubectl get svc devops-demo-service
```
5. Open the external IP in your browser.

## Outcome
By completing this project, I demonstrated:
- Full CI/CD automation with GitHub Actions
- Containerization best practices using Docker
- Automated security scanning with Trivy
- Deployment and scaling on Azure Kubernetes Service
- Practical knowledge of modern DevOps workflows

This project showcases my ability to build production-ready pipelines for modern cloud applications.
