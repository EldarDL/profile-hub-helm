# Profile Hub Helm Chart

A Kubernetes Helm chart for deploying the Profile Hub application with MongoDB database support.

## Overview

This Helm chart deploys a Profile Hub application that provides user profile management functionality. The chart includes:

- **Profile Hub Application**: A web service running on port 5000
- **MongoDB Database**: Persistent database with authentication enabled
- **Kubernetes Resources**: Deployment, Service, Ingress, and Secret configurations
- **Health Checks**: Liveness and readiness probes for application monitoring

## Chart Components

### Application Components
- **Deployment**: Runs the Profile Hub application with configurable replicas
- **Service**: Exposes the application on port 5000
- **Ingress**: Provides external access with nginx ingress controller
- **Secret**: Stores MongoDB connection credentials securely

### Database Components
- **MongoDB**: Bitnami MongoDB chart dependency (version 16.5.32)
- **Authentication**: Enabled by default with root user/password
- **Persistence**: 1Gi storage with replicaset architecture
- **Resources**: Configurable CPU and memory limits