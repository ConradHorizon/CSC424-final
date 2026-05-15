# CSC424 Final Exam - Containerization & CI/CD

This repository contains a fully containerized full-stack application featuring a React frontend, a .NET backend, and an Nginx reverse proxy. The deployment process is fully automated using a GitHub Actions CI/CD pipeline targeting a QA environment.

## DevOps Setup

### Running Locally
To spin up the entire stack on your local machine, ensure you have Docker and Docker Compose installed, then run the following command from the repository root:

```bash
docker compose up --build -d
