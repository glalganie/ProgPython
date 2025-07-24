<<<<<<< HEAD
# k8sappswd
=======
ProgPython Deployment Guide
This guide explains how to build the Docker image, deploy the application to Kubernetes, expose it via a Service, and access it locally using port forwarding.
>>>>>>> a126a45f3ac425be8eb9f901f14bd3b2cd09efde

A simple Flask application ready for Docker and Kubernetes deployment.

<<<<<<< HEAD
## Features

- Flask API with CORS enabled
- Dockerized for easy containerization
- Ready for deployment on Kubernetes

## Getting Started

### Requirements

- Python 3.11+
- Docker (optional, for containerization)

### Local Development

```bash
pip install -r requirements.txt
python app.py
```

### Docker

Build and run the container:

```bash
docker build -t k8sappswd .
docker run -p 5000:5000 k8sappswd
```

### Kubernetes

You can deploy this container to Kubernetes using your preferred method.

---

## Kubernetes: Check and Expose the App on Localhost

### Dry-run and validate your manifests

You can validate your YAML files before applying them using `--dry-run=client` and `kubectl apply --validate=true`:

```bash
kubectl apply -f pod.yaml --dry-run=client --validate=true
kubectl apply -f deployment.yaml --dry-run=client --validate=true   # if you have a deployment
kubectl apply -f service.yaml --dry-run=client --validate=true
```

### Apply your pod, deployment, and service YAML files

```bash
kubectl apply -f pod.yaml
kubectl apply -f deployment.yaml   # if you have a deployment
=======
# Build the Docker image from the Dockerfile in the current directory
# The image will be tagged as 'ProgPython:v1'
docker build -t ProgPython:v1 .
2. Kubernetes Deployment
Dry Run (Check Manifest)
Validate your deployment manifest before applying:

# Check if the deployment.yaml file is valid and see what would be created
# No changes are made to the cluster
kubectl apply -f deployment.yaml --dry-run=client
Apply Deployment
Create the deployment in your cluster:

# Actually create the deployment resource in your Kubernetes cluster
kubectl apply -f deployment.yaml
3. Create a Service
Assuming you have a service.yaml manifest, validate and apply it:

Dry Run
# Validate the service.yaml file before applying it
# This checks for errors without making changes
kubectl apply -f service.yaml --dry-run=client
Apply Service
# Create the Service resource in your Kubernetes cluster
>>>>>>> a126a45f3ac425be8eb9f901f14bd3b2cd09efde
kubectl apply -f service.yaml
```

<<<<<<< HEAD
Check the status of pods and services:

```bash
kubectl get pods
kubectl get services
```

Expose the service on your localhost (for example, if your service is named `k8sappswd-service`):

```bash
kubectl port-forward service/k8sappswd-service 5000:5000
```

Now you can access the app at [http://localhost:5000](http://localhost:5000).

---

## License

MIT License
=======
# Forward port 5000 from the k8sapp deployment to your local machine
# This lets you access the app at localhost:5000
kubectl port-forward deployment/ProgPython 5000:5000
Now you can access the app at http://localhost:5000/api/hello.

Replace /api/hello with your actual endpoint if different.

Summary of Steps
Build the Docker image: Prepares your app for deployment.
Dry run manifests: Validates your YAML files before making changes.
Apply deployment and service: Creates resources in Kubernetes.
Port forwarding: Lets you access the app from your local machine.
Make sure your Kubernetes cluster is running and kubectl is configured to use the correct context.
>>>>>>> a126a45f3ac425be8eb9f901f14bd3b2cd09efde
