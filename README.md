# DEPI Angular App

This repository hosts a three-tier application composed of:

- **Angular Frontend**: Serves the user interface (UI).  
- **Node.js Backend**: Handles business logic and communicates with the database.  
- **MySQL Database**: Stores persistent data.

---

## 1. Overview

The goal of this project is to demonstrate how to containerize and orchestrate a simple Angular + Node.js + MySQL app using Docker, Docker Compose, and Kubernetes. We also integrate an NGINX Ingress Controller for external access, and optionally set up a private Docker registry.

---

## 2. Architecture

Below is a high-level look at the **3-tier** architecture:


                       [ Client / Browser ]
                                 |
                                 v
                    [ NGINX Ingress Controller ]
                                 |
                          ( Service: frontend )
                                 |
                             [ Frontend ]
                                 |
                           ( Service: backend )
                                 |
                            [ Backend ]
                                 |
                           ( Service: mysql )
                                 |
                             [ MySQL DB ]
                      (PersistentVolume/PVC)


1. **Frontend (Angular)**: Deployed as a container, built via a multi-stage Dockerfile.  
2. **Backend (Node.js)**: Simple Node.js server connecting to MySQL.  
3. **MySQL**: Deployed with a PersistentVolume (PV) and PersistentVolumeClaim (PVC) for data storage in Kubernetes.

---

## 3. Project Structure

```plaintext
depi-angular-app/
├── backend/
│   ├── Dockerfile
│   ├── db.js
│   ├── server.js
│   ├── package.json
│   └── ...
├── front-end/
│   ├── Dockerfile
│   ├── angular.json
│   ├── package.json
│   └── ...
├── k8s-backend.yaml
├── k8s-frontend.yaml
├── k8s-ingress.yaml
├── k8s-mysql.yaml
├── docker-compose.yaml
└── README.md

---

## 4. Installation & Usage

### 4.1 Prerequisites
- **Git** installed for cloning this repository.  
- **Docker** installed for building/pushing images.  
- **docker-compose** for local testing.  
- **kubeadm** or any Kubernetes cluster if deploying to K8s.  
- **kubectl** for applying Kubernetes manifests.  
- **nginx-ingress** controller if exposing the app in Kubernetes.

### 4.2 Clone the Repository
```bash
git clone https://github.com/kyrilloswahid/depi-angular-app.git
cd depi-angular-app

### 4.3 Local Testing with Docker Compose

1. **Build and start** containers:
   ```bash
   docker-compose up --build -d
2. **Access the App**:
- Frontend at http://localhost:8080
- Backend at http://localhost:3000
- MySQL on port 3306
3. **Stop the containers**:
```bash
docker-compose down

