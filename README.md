# Profile Hub Helm Chart

A Helm chart for deploying the Profile Hub application with MongoDB replica set and nginx ingress.

## Prerequisites

- Kubernetes 1.19+
- Helm 3.0+
- nginx-ingress controller

## Quick Start

```bash
# Install with default values
helm install profile-hub ./helm

# Install with custom MongoDB credentials
helm install profile-hub ./helm \
  --set app.mongodb.username=your-username \
  --set app.mongodb.password=your-password

# Install with custom port
helm install profile-hub ./helm --set app.port=8080
```

## Configuration

| Parameter | Description | Default |
|-----------|-------------|---------|
| `app.port` | Application port | `5000` |
| `app.mongodb.username` | MongoDB username | `profilehub` |
| `app.mongodb.password` | MongoDB password | `profilehubpass` |
| `app.mongodb.database` | MongoDB database | `profilehub` |
| `mongodb.auth.rootPassword` | MongoDB root password | `rootpassword` |
| `mongodb.replicaCount.primary` | Primary replicas | `1` |
| `mongodb.replicaCount.secondary` | Secondary replicas | `1` |

## Architecture

- **Profile Hub Application**: Flask app with health checks
- **MongoDB Replica Set**: 2-node replica set (1 primary + 1 secondary)
- **Nginx Ingress**: Routes external traffic to the application

## Commands

```bash
# Upgrade
helm upgrade profile-hub ./helm

# Uninstall
helm uninstall profile-hub

# Check status
kubectl get pods -l app.kubernetes.io/name=profile-hub
``` 