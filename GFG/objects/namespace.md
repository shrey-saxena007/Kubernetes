In **Kubernetes**, a **namespace** is a **logical partition (virtual cluster)** inside a single Kubernetes cluster. It’s used to **organize, isolate, and manage resources**.

---

## Simple definition

> A **namespace** is a way to divide a Kubernetes cluster into multiple **isolated environments**.

All resources live **inside a namespace** (except a few global ones).

---

## Why namespaces are needed

Namespaces help when:


### 1. **Separate environments**

You can have:

* `dev`
* `staging`
* `production`

All running in the same cluster, but isolated.

---

### 2. **Resource isolation & limits**

You can:

* Limit CPU / memory per namespace
* Apply security rules per namespace
* Control access using RBAC

---

## What lives inside a namespace?

Namespaced resources:

* Pods
* Services
* Deployments
* ConfigMaps
* Secrets
* Jobs
* StatefulSets

Cluster-wide (NOT namespaced):

* Nodes
* PersistentVolumes
* Namespaces themselves
* StorageClasses

---

## Default namespaces in Kubernetes

Run:

```bash
kubectl get namespaces
```

You’ll usually see:

| Namespace         | Purpose                                     |
| ----------------- | ------------------------------------------- |
| `default`         | default Namespace is the Namespace that we use in order to create the resources when we create a Namespace in the beginning.|
| `kube-system`     | kube-system is the namespace that includes objects created by the Kubernetes system. The components that are deployed in this Namespace are the system processes - they are from Master managing processes or Kubectl etc. kube-system Namespace is not meant for our (developer's) use. so we do not have to create anything or modify anything in this namespace.|
| `kube-public`     | kube-public contains the publicly accessible data. It has a config map that contains the Cluster information which is accessible even without authentication.|
| `kube-node-lease` | kube-node-lease Namespace is a new addition to Kubernetes. The purpose of this namespace is that it holds information about the heartbeats of Nodes. So each Node basically gets its own lease object in the Namespace. This object contains the information about that nodes availability.|

---

## Example

### Create a namespace

```bash
kubectl create namespace dev
```

### Deploy a pod in that namespace

```bash
kubectl apply -f app.yaml -n dev
```

### Get pods only in `dev`

```bash
kubectl get pods -n dev
```

---

## Namespaces ≠ Virtual Machines

Important clarification:

* Namespaces **do NOT** create separate clusters
* All namespaces **share the same nodes**
* Isolation is **logical**, not physical

---

## When NOT to use namespaces

Namespaces are **not very useful** if:

* You have only **one small app**
* Single developer + single environment

---
