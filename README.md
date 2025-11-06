# Kubernetes Helm Charts

Comprehensive Helm charts examples for Kubernetes with detailed explanations for Dev, Staging, and Production environments.

## 📚 What is This Repository?

This repository contains production-ready Helm charts with **detailed inline comments** explaining every configuration option. It's designed as a **learning resource** for DevOps engineers preparing for interviews or wanting to understand Helm best practices.

## 🗂️ Repository Structure

```
kubernetes-helm-charts/
└── myapp-chart/
    ├── Chart.yaml              # Chart metadata
    ├── values.yaml             # Default values (Dev environment)
    ├── values-staging.yaml     # Staging environment overrides
    ├── values-prod.yaml        # Production environment overrides
    └── templates/
        ├── deployment.yaml     # Kubernetes Deployment template
        ├── service.yaml        # Kubernetes Service template
        └── ingress.yaml        # Kubernetes Ingress template
```

## 🚀 Quick Start

### Prerequisites

- Kubernetes cluster (Minikube, Kind, or cloud provider)
- Helm 3.x installed
- kubectl configured

### Installation

**For Development Environment:**
```bash
helm install myapp ./myapp-chart
```

**For Staging Environment:**
```bash
helm install myapp ./myapp-chart -f myapp-chart/values-staging.yaml
```

**For Production Environment:**
```bash
helm install myapp ./myapp-chart -f myapp-chart/values-prod.yaml
```

### Upgrade

```bash
helm upgrade myapp ./myapp-chart -f myapp-chart/values-prod.yaml
```

### Rollback

```bash
# List releases
helm list

# Rollback to previous version
helm rollback myapp

# Rollback to specific revision
helm rollback myapp 1
```

### Uninstall

```bash
helm uninstall myapp
```

## 🌍 Environment Configurations

### Development (values.yaml)
- **Replicas:** 2
- **Service Type:** ClusterIP
- **Resources:** Low (250m CPU, 256Mi memory)
- **Autoscaling:** Disabled
- **Log Level:** Debug

### Staging (values-staging.yaml)
- **Replicas:** 3
- **Service Type:** ClusterIP
- **Resources:** Moderate (500m CPU, 512Mi memory)
- **Autoscaling:** Disabled
- **Log Level:** Debug

### Production (values-prod.yaml)
- **Replicas:** 5
- **Service Type:** LoadBalancer
- **Resources:** High (1000m CPU, 1Gi memory)
- **Autoscaling:** Enabled (5-20 replicas)
- **Log Level:** Info

## 📖 Key Features

### 1. **Comprehensive Comments**
Every file contains detailed comments explaining:
- What each field does
- When to use specific configurations
- Best practices for each environment

### 2. **Multi-Environment Support**
Easy environment management using Helm values files:
- Development: Fast iteration, debug logging
- Staging: Pre-production testing
- Production: High availability, performance optimized

### 3. **Production-Ready Templates**
- **Deployment:** Includes health probes, resource limits, environment variables
- **Service:** Configurable service types
- **Ingress:** TLS support, host-based routing

### 4. **Interview-Friendly**
Perfect for DevOps interview preparation with explanations of:
- Helm templating syntax
- Kubernetes networking concepts
- Environment segregation strategies

## 🛠️ Customization

### Override Values via CLI

```bash
helm install myapp ./myapp-chart --set replicaCount=3
```

### Multiple Overrides

```bash
helm install myapp ./myapp-chart \
  --set replicaCount=3 \
  --set image.tag=2.0.0 \
  --set service.type=LoadBalancer
```

## 📝 Template Files Explained

### deployment.yaml
Defines how your application runs:
- Number of replicas
- Container image and version
- Resource requests and limits
- Health checks (liveness/readiness probes)
- Environment variables

### service.yaml
Exposes your application:
- ClusterIP: Internal only
- NodePort: Accessible via node IP
- LoadBalancer: External access via cloud load balancer

### ingress.yaml
Manages external HTTP/HTTPS access:
- Host-based routing
- Path-based routing
- TLS/SSL termination
- Annotations for ingress controllers

## 🎯 Use Cases

1. **Learning Helm:** Study the comments to understand Helm concepts
2. **Interview Prep:** Review before DevOps/SRE interviews
3. **Project Template:** Use as starting point for your projects
4. **Team Training:** Share with team members learning Kubernetes

## 🔍 Verification Commands

```bash
# Dry run to see generated manifests
helm install myapp ./myapp-chart --dry-run --debug

# Template rendering
helm template myapp ./myapp-chart

# Lint chart for errors
helm lint ./myapp-chart

# Get deployed values
helm get values myapp

# Check deployment status
kubectl get pods
kubectl get svc
kubectl get ingress
```

## 📚 Interview Topics Covered

- ✅ Helm chart structure
- ✅ Values files and templating
- ✅ Environment segregation
- ✅ Kubernetes Deployment strategies
- ✅ Service types and networking
- ✅ Ingress configuration
- ✅ Resource management
- ✅ Health probes
- ✅ Autoscaling
- ✅ CI/CD integration

## 🤝 Contributing

Feel free to fork this repository and customize for your needs!

## 📄 License

MIT License - feel free to use for learning and projects.

---

**Created for DevOps Interview Preparation** 🚀
