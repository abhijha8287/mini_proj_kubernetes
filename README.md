# Kubernetes Mini Project

A small Flask app packaged with Docker and deployed to Kubernetes with two replicas.

## Why this exists
Hands-on practice for Kubernetes: building an image, writing a Deployment and Service, and running it on a local cluster.

## What it does
- Flask page with a form that greets the user by name
- Docker image based on `python:3.9-slim`, listening on port 5000
- Kubernetes Deployment with 2 replicas and a Service mapping port 8080 to 5000

## Project structure
```
mini_proj_kubernetes/
├── templates/        HTML page
├── static/           CSS styles
├── app.py            Flask app
├── dockerfile        Container image definition
├── deployment.yaml   Kubernetes Deployment and Service
├── requirements.txt  Python dependencies
├── NOTES.md          Kubernetes in CI/CD, EKS/AKS/GKE
└── LICENSE           MIT licence
```

## Getting started
Requirements: Docker, kubectl and a local cluster such as Minikube.
```bash
git clone https://github.com/abhijha8287/mini_proj_kubernetes.git
cd mini_proj_kubernetes
eval $(minikube docker-env)                     # build inside Minikube
docker build -t kubernetes-test-app:latest -f dockerfile .
kubectl apply -f deployment.yaml
kubectl port-forward service/<service-name> 8080:8080
```
Use `kubectl get svc` to find the service name, then open http://localhost:8080.

Run without Kubernetes:
```bash
pip install -r requirements.txt
python app.py
```

## Tech stack
Python, Flask, Docker, Kubernetes

## Notes
`NOTES.md` holds learning notes on adding Kubernetes to a GitHub Actions + AWS pipeline and on managed services (EKS, AKS, GKE). MIT licensed.
