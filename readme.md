# Continuous Integration Pipelines

This README outlines four different continuous integration (CI) pipelines configured for various scenarios and technologies. 
Each pipeline is triggered on changes to the `master` branch and utilizes the latest Ubuntu VM image for execution.

---

## Pipeline 1: Maven Build and SonarCloud Analysis

- **Trigger**: 
  - Branch: `master`
- **VM Image**:
  - Ubuntu-latest
- **Variables**:
  - `sonarProjectKey`: Your SonarCloud Project Key
  - `sonarOrganization`: Your SonarCloud Organization
- **Stages**:
  - **Build and Analyze**:
    - **Build Job**:
      - Maven clean and verify (skipping tests)
      - Prepare SonarCloud analysis
      - Analyze with SonarCloud

---

## Pipeline 2: Maven Build and SonarCloud Analysis (Alternative Setup)

Similar to Pipeline 1 with the same objective of building the Maven project and conducting SonarCloud analysis.

---

## Pipeline 3: Node.js Build and Docker Image Push

- **Trigger**:
  - Branch: `master`
- **VM Image**:
  - Ubuntu-latest
- **Variables**:
  - `imageName`: Name for the Docker image, e.g., `nodejs-image`
- **Stages**:
  - **Build**:
    - **Build Job**:
      - Install Node.js dependencies
      - Run Node.js tests
      - Build Docker image
      - Push Docker image to Docker Hub (requires Docker Hub credentials)

---

## Pipeline 4: Python Setup, Testing, and Database Migration

- **Trigger**:
  - Branch: `master`
- **VM Image**:
  - Ubuntu-latest
- **Stages**:
  - **Install and Test**:
    - **Setup Job**:
      - Install Python dependencies
      - Run Python tests using pytest
  - **Migrate Database**:
    - **Migrate Job**:
      - Run database migrations using Django's manage.py

---

Ensure to replace placeholder values (e.g., `Your_SonarCloud_Project_Key`, `Your_SonarCloud_Org`, `$(dockerHubUsername)`, `$(dockerHubPassword)`) with your actual values. Secure sensitive information like passwords using [Azure Pipelines secret variables](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/variables?view=azure-devops&tabs=yaml%2Cbatch#secret-variables) or a secure configuration management solution.
