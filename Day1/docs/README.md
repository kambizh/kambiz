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
```
## Step-by-Step: Create a kind Cluster

Let’s create a local Kubernetes cluster using kind (Kubernetes IN Docker).

---

### Step 1: Create Cluster Config File

Create a file named [`kind-config.yaml`](../config/kind-config.yaml) with the following content:

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
  - role: control-plane
  - role: worker
```

### 2. Create the Cluster

```bash
kind create cluster --name dev-cluster --config Day1/config/kind-config.yaml
```

### 3. Verify the Cluster

```bash
kubectl cluster-info --context kind-dev-cluster
kubectl get nodes
```

### 4. Quick Test: Deploy NGINX

```bash
kubectl create deployment nginx --image=nginx
kubectl expose deployment nginx --port=80 --type=NodePort
kubectl get svc
```

### 5. Forward port to access NGINX:

```bash
kubectl port-forward service/nginx 8080:80
Then open: http://localhost:8080
```

### 6. Cleanup
To delete the kind cluster:

```bash
kind delete cluster --name dev-cluster
```
