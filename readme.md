# Advanced CI/CD Pipelines

This repository contains intricate CI/CD pipelines designed for various scenarios and technologies, showcasing advanced features and practices in Azure Pipelines. Each pipeline is crafted with best practices in mind, optimizing for performance, security, and maintainability.

## 1. **Maven and SonarCloud Analysis Pipeline**

### Overview
- **Triggers**: On changes to `master` branch, excluding `README.md`.
- **Build**: Utilizes Maven to build the project, skipping tests, and prepares for SonarCloud analysis.
- **Analysis**: Analyzes the project with SonarCloud and publishes code coverage results using JaCoCo.
- **Post Analysis**: Sends a notification upon successful analysis.

### Detailed Stages
#### Build and Analyze Stage
- **Build Job**:
  - Checkout repository
  - Maven build and verify, skipping tests
  - Prepare SonarCloud analysis
  - Analyze with SonarCloud
  - Publish code coverage results using JaCoCo

#### Post Analysis Stage
- **Notify Job**:
  - Send notification upon successful analysis

## 2. **DotNet Build and Deploy Pipeline**

### Overview
- **Triggers**: On changes to `master` branch, excluding `README.md`.
- **Build**: Restores, builds, and tests the project, publishing code coverage results.
- **Deploy**: Publishes the project and deploys it to a Production environment, with pre-deploy artifact downloading.

### Detailed Stages
#### Build Stage
- **Build Job**:
  - Checkout repository
  - Cache NuGet packages
  - Restore, build, and test the project
  - Publish code coverage results

#### Deploy Stage
- **Deploy Job**:
  - Pre-deploy: Download artifacts
  - Deploy: Publish the project and deploy to a Production environment

## 3. **Node.js and Docker Pipeline**

### Overview
- **Triggers**: On changes to `master` branch, excluding `README.md`.
- **Build**: Installs dependencies, runs tests, builds a Docker image, performs a security scan on the image, and pushes it to Docker Hub.

### Detailed Stages
#### Build Stage
- **Build Job**:
  - Checkout repository
  - Cache Node modules
  - Install dependencies and run tests
  - Docker login, build, security scan, and push to Docker Hub

## 4. **Python Test and Database Migration Pipeline**

### Overview
- **Triggers**: On changes to `master` branch, excluding `README.md`.
- **Build**: Sets up Python, creates a virtual environment, installs dependencies, and runs tests.
- **Migration**: Activates the virtual environment and runs database migrations using Django's `manage.py`.

### Detailed Stages
#### Install and Test Stage
- **Setup Job**:
  - Checkout repository
  - Setup Python version
  - Cache pip packages
  - Create and activate virtual environment
  - Install dependencies and run tests

#### Migrate Database Stage
- **Migrate Job**:
  - Activate virtual environment
  - Run database migrations using Django's `manage.py`

---

Each pipeline demonstrates a high level of technical sophistication in CI/CD practices within Azure Pipelines, reflecting a mature approach to continuous integration and continuous deployment. Ensure to replace placeholder values with your actual values where necessary.

For a deeper understanding, refer to the `azure-pipelines.yml` file in the respective directories of this repository.

Ensure to replace placeholder values (e.g., `Your_SonarCloud_Project_Key`, `Your_SonarCloud_Org`, `$(dockerHubUsername)`, `$(dockerHubPassword)`) with your actual values. Secure sensitive information like passwords using [Azure Pipelines secret variables](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/variables?view=azure-devops&tabs=yaml%2Cbatch#secret-variables) or a secure configuration management solution.