# CSC424 Final Exam - Containerization & CI/CD

This repository contains a fully containerized full-stack application featuring a React frontend, a .NET backend, and an Nginx reverse proxy. The deployment process is fully automated using a GitHub Actions CI/CD pipeline targeting a QA environment.

## DevOps Setup

### Running Locally
To spin up the entire stack on your local machine, ensure you have Docker and Docker Compose installed, then run the following command from the repository root:

```bash
docker compose up --build -d 
```
### Testing

Frontend: http://localhost — Access React + Vite "Ops Portal".
Backend API: http://localhost/api/ping — Returns a successful health status.

#### Architecture
Frontend (The Visuals): Built with React. I used a "multi-stage build," which basically means I used one tool to build the code.

Backend : Built with .NET. Just like the frontend, I used a multi-stage process to make sure the final version is small and only contains what it needs to run.

Nginx : This acts as a "gatekeeper." When you go to http://localhost, Nginx decides where to send you. If you're looking for the website, it sends you to the Frontend. If you're looking for data, it sends you to the Backend.

Internal Network: All these parts talk to each other on a private, internal network. This keeps the backend hidden and safe from the outside world.

##### CI/CD Pipeline
Instead of moving files manually, this project uses an automated workflow that handles the deployment whenever I make changes:

The Trigger: As soon as code is pushed to the main branch on GitHub, the process starts automatically.

Live Update: Finally, the workflow logs into the QA Server using SSH, downloads the newest containers, and restarts the app so the latest version is always live.
