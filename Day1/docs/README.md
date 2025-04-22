# Day 1 – Setting Up kind for Local Kubernetes Development

This document walks through the setup of [kind](https://kind.sigs.k8s.io/) (Kubernetes IN Docker) for local testing. This setup enables developers to run a lightweight Kubernetes cluster in Docker containers, ideal for testing custom Kubernetes resources and Spring Boot-based microservices.

---

## Prerequisites

Before starting, ensure the following tools are installed:

- **Docker**: [Install Docker](https://docs.docker.com/get-docker/)
- **kubectl**: [Install kubectl](https://kubernetes.io/docs/tasks/tools/)
- **kind**: [Install kind](https://kind.sigs.k8s.io/docs/user/quick-start/#installation)

To verify the tools:

```bash
docker --version
kubectl version --client
kind --version

