**Minikube** is a tool that lets you **run a small, local Kubernetes cluster on your own machine**.

### In one line:

> **Minikube = Kubernetes for learning and local development**

---

### What Minikube does

* Runs **Kubernetes locally** (usually 1 node)
* Uses **VM or Docker** under the hood
* Perfect for:

  * Learning Kubernetes
  * Testing manifests
  * Local experimentation

---

### What it is NOT

❌ Not for production
❌ Not for large-scale workloads

---

### Example usage

```bash
minikube start
kubectl get pods
```

---

### Minikube vs Docker Desktop Kubernetes

| Minikube          | Docker Desktop     |
| ----------------- | ------------------ |
| CLI-based         | UI-based           |
| More configurable | Simpler            |
| Linux-like VM     | Tightly integrated |

---

### TL;DR

> **Minikube lets you practice Kubernetes on your laptop without cloud or servers.**
