## Multi-Container Docker Application with CI/CD: Calculator App Project

#### [GitHub Repository](https://github.com/CodeBreaker2712/DevOps-Foundations-Course)

#### [Docker Hub Repositories]()
- **Frontend Image:** [Calculator Frontend](https://hub.docker.com/repository/docker/rexinfernum/calculator-frontend)
- **Backend Image:** [Calculator Backend](https://hub.docker.com/repository/docker/rexinfernum/calculator-backend)

#### Submission by - **[Jeet Jani](mailto:jeetjani@dal.ca)**

---

### Project Overview

- **Brief project description:**  
  This project implements a multi-container calculator application using Docker for containerization and GitHub Actions for CI/CD. It includes:
  - A React-based frontend to interact with users.
  - A Flask-based backend providing calculator APIs.

- **Implemented Files:**
  - `Dockerfile` for both frontend and backend to containerize the application.
  - `docker-compose.yml` to orchestrate multi-container setup.
  - GitHub Actions CI/CD pipeline to automate building and pushing Docker images.

---

### Docker Implementation

**Explanation of Dockerfiles:**

- **Backend Dockerfile** (Python API):
    - Uses `python:3.12-slim` as the base image.
    - Installs dependencies using `requirements.txt`.
    - Exposes port `5000` and runs the Flask server (`app.py`) on startup.

- **Frontend Dockerfile** (React App):
    - Uses `node:23-alpine3.19` as the base image.
    - Installs dependencies via `npm install` and builds the React app for production.
    - Exposes port `3000` for the React development server.

---

### Docker Compose YAML Configuration

**Break down your `docker-compose.yml` file:**

- **Services:**
  - **Frontend:** Runs the React app container on port `3000`.
  - **Backend:** Runs the Flask backend container on port `5000`.

- **Networking:**
  - The `depends_on` directive ensures the backend starts before the frontend.

---

### CI/CD Pipeline (YAML Configuration)

**Explanation of CI/CD pipeline:**

- **Triggers:**
  - Pipeline triggers on `push` to the `main` branch and on pull requests targeting `main`.

- **Stages:**
  - **Frontend Job:**
    - Sets up Node.js.
    - Installs dependencies and builds the React app.
  - **Backend Job:**
    - Sets up Python.
    - Installs dependencies using `requirements.txt`.
  - **Docker Job:**
    - Builds and pushes frontend and backend images to Docker Hub.

- **Docker Hub Integration:**
  - Pushes images to the Docker Hub repository using `DOCKER_USERNAME` and `DOCKER_PASSWORD` secrets.

---

### Assumptions

- Docker Hub credentials (`DOCKER_USERNAME`, `DOCKER_PASSWORD`) are securely stored as GitHub secrets.
- Default tags (`latest`) are used for images.

---

### Lessons Learned

- **Challenges:**
  - Ensuring consistency in Node.js and Python versions across Dockerfiles and GitHub Actions.
  - Debugging image naming issues for Docker Hub.

- **What I Learned:**
  - How to containerize frontend and backend applications.
  - Using GitHub Actions for CI/CD automation.
  - Managing Docker images and orchestrating multi-container applications.

---

### Future Improvements

- Add tests in CI/CD pipeline for both frontend and backend before pushing Docker images.
- Automate deployment to a cloud provider (e.g., AWS ECS or Kubernetes).
- Use versioned tags for Docker images instead of relying on `latest`.

---