# DEPI Angular App on K8s

## Overview
This project includes an Angular frontend, a Node.js backend, and MySQL database.
Deployment steps:
1. Kubeadm cluster installation (master and worker)
2. Dockerfiles for backend, frontend
3. Docker Compose for local dev
4. Docker registry push
5. K8s manifests (with PV/PVC for MySQL)
6. NGINX Ingress
7. CLI-based Git push
8. CI/CD with Jenkin
