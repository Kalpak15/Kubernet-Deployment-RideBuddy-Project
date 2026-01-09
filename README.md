# Ride-Buddy

A ride-sharing application designed to connect drivers and passengers for convenient and cost-effective transportation.

## Project Overview

Ride-Buddy is a full-stack application that facilitates ride-sharing by matching drivers with passengers heading in similar directions. The application consists of a frontend user interface and a backend API service, both containerized and deployed using Kubernetes.

## Architecture

The project follows a microservices architecture with:
- **Frontend**: User-facing web application
- **Backend**: RESTful API service handling business logic and data management
- **Kubernetes**: Container orchestration for deployment and scaling

## Prerequisites

Before deploying this application, ensure you have:
- Kubernetes cluster (local or cloud-based)
- `kubectl` CLI tool installed and configured
- Docker images for frontend and backend built and pushed to a container registry


## Project Structure

```
ride-buddy/
├── Carpooling_Frontend/
│   ├── deployment1.yaml
│   └── service1.yaml
├── backend/
│   ├── deployment2.yaml
│   └── service2.yaml
└── README.md
```

## Kubernetes Resources

### Frontend
- **Deployment**: Manages frontend application pods
- **Service**: Exposes frontend to users (NodePort)

### Backend
- **Deployment**: Manages backend API pods
- **Service**: Exposes backend API (ClusterIP for internal communication or LoadBalancer for external access)

## Deployment Instructions

### Step 1: Clone the Repository
```bash
git clone <repository-url>
cd Ride-buddy
```


### Step 3: Create Namespace
```bash
kubectl create namespace ride-buddy-frontend
kubectl create namespace ride-buddy-backend
```

### Step 3: Deploy Backend
```bash
kubectl apply -f deployment2.yaml
kubectl apply -f service2.yaml
```

Verify backend deployment:
```bash
kubectl get deployments 
kubectl get pods -n ride-buddy-backend
kubectl get services
```

### Step 4: Deploy Frontend
```bash
kubectl apply -f deployment1.yaml
kubectl apply -f service1.yaml
```

Verify frontend deployment:
```bash
kubectl get deployments
kubectl get pods -n ride-buddy-frontend
kubectl get services
```

### Step 5: Access the Application Internally using curl
Get the external IP or NodePort:

```bash
minikube service frontend-service -n ride-buddy-backend
minikube service backend -n ride-buddy-backend

curl -L <url>

```

## Support

For issues and questions:
- Create an issue in the repository
- Contact: [your-email@example.com]

## Acknowledgments

- List any contributors or third-party resources used

---

**Note**: Update this README with specific details about your application, including actual image names, ports, and any additional configuration specific to your Ride-Buddy implementation.
