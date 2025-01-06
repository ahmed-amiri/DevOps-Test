# DevOps Engineer Assignment

## **Assignment Overview**

This project demonstrates how to containerize and orchestrate a full-stack application with frontend, backend, and MySQL database services. The goal is to ensure scalability, reliability, and automated deployment using a CI/CD pipeline.

### **Project Structure:**
- `thefrontend`: Angular-based frontend application.
- `thebackend`: Spring Boot-based backend application.
- `mysql`: MySQL database service.
- `docker-compose.yml`: File that orchestrates all services.
- `deploy.yml`: GitHub Actions CI/CD pipeline configuration.

---

## **How to Set Up and Run the Project Locally**

### **Prerequisites**
- Docker and Docker Compose installed on your machine.
- Git installed to clone the repository.
- Docker Hub credentials for pushing the images (for CI/CD).

### **Steps to Run Locally:**

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/ahmed-amiri/DevOps-Test.git
   cd DevOps-Test
    ```
   
2. **Build and Start Containers:**
Use Docker Compose to build and start the containers for the frontend, backend, and MySQL services:

   ```bash
   docker-compose up --build

3. **Access the Application:**
   - Frontend will be accessible at `http://localhost:80`.
   - Backend API will be accessible at `http://localhost:8080`.

---

## **CI/CD Pipeline**

This project utilizes a CI/CD pipeline configured with GitHub Actions. The pipeline automates the following tasks:

- **Builds** Docker images for both frontend and backend.
- **Pushes** Docker images to Docker Hub upon successful build.
- **Deploys** the application using Docker Compose.

### **Pipeline Workflow:**

The GitHub Actions CI/CD pipeline is defined in `.github/workflows/deploy.yml`.

1. **Build and Push Docker Images**: 
   - The pipeline builds Docker images for the frontend and backend.
   - The images are then pushed to Docker Hub for deployment.

2. **Deployment**:
   - Uses Docker Compose to deploy the services locally or on a cloud environment (configured for remote deployment).

---

## **Architecture Overview**

### **Containerization:**
- **Frontend**: An Angular application that communicates with the backend API.
- **Backend**: A Spring Boot application that provides RESTful APIs and interacts with the MySQL database.
- **MySQL**: A MySQL database that stores application data.

### **Orchestration with Docker Compose:**

The project uses Docker Compose to orchestrate the services. The `docker-compose.yml` file ensures that:
- **Frontend** waits for the **backend** to be ready.
- **Backend** depends on **MySQL** to be initialized before starting.

### **CI/CD Pipeline:**

GitHub Actions:
- The pipeline is triggered on pushes to the `main` branch or pull requests targeting `main`.
- It sets up the environment and installs dependencies.
- Docker images are built, pushed to Docker Hub, and deployed using Docker Compose.

---

## **Tools and Technologies Used**

- **Docker**: Containerization platform for packaging applications and dependencies.
- **Docker Compose**: Tool to define and run multi-container Docker applications.
- **GitHub Actions**: CI/CD tool for automating workflows.
- **Angular**: Frontend framework for building dynamic web applications.
- **Spring Boot**: Backend framework for building microservices.
- **MySQL**: Relational database service for data storage.
- **Node.js**: JavaScript runtime environment for running the frontend.

---
