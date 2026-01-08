- cluster is group of nodes
- each node has multiple containerized applications
- so there is one master node, which handles all the worker nodes, worker nodes has containerized applications, master just manages worker nodes. 
- each worker node has containerized applications, so these application runs on pod. pod is single instance of a running process in a cluster. it can run one or more containers and share same resources. So if an application requires multiple containers to run, we can put all these in one pod
- 
  
---

Kubernetes has a **well-defined set of components**, and once you understand them, Kubernetes becomes much less scary 🙂

I’ll explain them **layer by layer**, from top to bottom.

---

## 1️⃣ Kubernetes Cluster (Big Picture)

A **Kubernetes cluster** has **two main parts**:

```
┌─────────────────────┐
│   Control Plane     │  ← Brain
└─────────────────────┘
        │
┌─────────────────────┐
│   Worker Nodes      │  ← Muscles
└─────────────────────┘
```

---

## 2️⃣ Control Plane Components (The Brain 🧠)

These components **decide what should happen** in the cluster.

### 2.1 **kube-apiserver**

📌 **Most important component**

* Entry point to Kubernetes
* All commands (`kubectl`) go through this
* Validates requests and updates cluster state

```text
kubectl → kube-apiserver → cluster
```

---

### 2.2 **etcd**

📦 **Key-value database**

* Stores all cluster data:

  * Pods
  * Services
  * Configs
  * Secrets
* Source of truth for Kubernetes

If etcd is lost → cluster state is lost ⚠️

---

### 2.3 **kube-scheduler**

🧭 Decides **where a Pod runs**

* Chooses the best worker node to a newly created pods
* means assign n
* Considers:

  * CPU
  * Memory
  * Node health
  * Constraints

---

### 2.4 **kube-controller-manager**

🎮 Runs controllers that maintain **desired state**

Examples:

* ReplicaSet Controller
* Node Controller
* Job Controller

```text
Desired: 3 pods
Actual: 2 pods
→ Controller creates 1 more
```

---

### 2.5 **cloud-controller-manager** (optional)

☁️ For cloud integrations

* Load balancers
* Volumes
* Node management

Used in AWS, GCP, Azure.

---

## 3️⃣ Worker Node Components (The Muscles 💪)

These components **run your applications**.

---

### 3.1 **kubelet**

🤖 Agent on each node

* Talks to kube-apiserver
* Ensures containers are running in a pod
* Reports node & pod status

---

### 3.2 **Container Runtime**

📦 A tool which runs containers

Examples: 

* containerd
* CRI-O
* Docker

---

### 3.3 **kube-proxy**

🌐 Networking component

* Handles pod-to-pod communication
* Service load balancing
* Uses iptables / IPVS

---

## 4️⃣ Kubernetes Objects (What you create)

These are **not processes**, but **resources** you define.

| Object         | Purpose                           |
| -------------- | --------------------------------- |
| **Pod**        | Smallest unit (container wrapper) |
| **Deployment** | Manages pods & updates            |
| **Service**    | Stable networking                 |
| **ReplicaSet** | Keeps desired pod count           |
| **ConfigMap**  | Config data                       |
| **Secret**     | Sensitive data                    |
| **Ingress**    | HTTP routing                      |
| **Namespace**  | Logical isolation                 |

---

## 5️⃣ Add-ons (Optional but common)

| Add-on                | Purpose         |
| --------------------- | --------------- |
| CoreDNS               | Internal DNS    |
| Dashboard             | Web UI          |
| Metrics Server        | Autoscaling     |
| Ingress Controller    | Traffic routing |
| CNI (Calico, Flannel) | Networking      |

---

## 6️⃣ Very Simple Flow (End-to-End)

```text
kubectl apply → kube-apiserver
              ↓
           etcd (store)
              ↓
      scheduler picks node
              ↓
      kubelet runs container
              ↓
      kube-proxy exposes service
```

---

## TL;DR (Memory-friendly)

🧠 **Control Plane**

* API Server
* etcd
* Scheduler
* Controller Manager

💪 **Worker Node**

* kubelet
* container runtime
* kube-proxy

📦 **Objects**

* Pod
* Deployment
* Service
* ConfigMap
* Secret

---

If you want next:

* **Diagram with arrows**
* **Compare Docker vs Kubernetes components**
* **Hands-on: deploy first pod**
* **Explain each object with YAML**

Just tell me 👌
