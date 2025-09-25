# Principal Pipeline Repository

This repository is a centralized location for the GitHub Actions pipelines. This has several pipelines that are available:

## Container Builder Pipeline
The Container Builder Pipeline tests and builds a container. The testing is done against amd64 architecture to ensure that the container builds successfully.

### Required Inputs

| Input | Description | Default | Required |
|-------|-------------|---------|----------|
| image_name | Name of the Docker image to build | - | Yes |
| testing_platform | Platforms for testing the container | linux/amd64 | No |
| platforms | Platforms for which to build the container | linux/arm/v7,linux/arm64/v8,linux/amd64 | No |

### Required Secrets

| Secret | Description | Required |
|--------|-------------|----------|
| DOCKERHUB_USERNAME | Username for Docker Hub | Yes |
| DOCKERHUB_PASSWORD | Password for Docker Hub | Yes |
| GH_USERNAME | Username for GitHub Packages | Yes |
| GH_PAT | Personal Access Token for GitHub Packages | Yes |

Note: The registries are defined as environment variables in the pipeline:
- Docker Hub Registry: docker.io
- GitHub Registry: ghcr.io

## Python Checker Pipeline
Checks and validates Python code. Performs the following actions:
- Linting
    - black
    - codespell
    - flake8
    - isort
- Security checks
    - bandit
