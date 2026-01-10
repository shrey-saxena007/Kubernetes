- Kubernetes orchestrates containers grouping them into logical units called pods and managing their lifecycle across a cluster of machines.
  
### Monolithic Vs Microservices
In the past, applications were built using a monolithic architecture, where everything was interconnected and bundled into one big codebase. This made updates risky for example, if you wanted to change just the payment module in an e-commerce app, you had to redeploy the entire application. A small bug could crash the whole system.

To overcome this, the industry moved toward microservices, where each feature (like payments, search, or notifications) is built and deployed independently. This made applications more flexible and scalable. Now, the question is, should we assign 1 server to each microservice?, no not at all, imagine there are 70 microservices, then you will have to buy 70 servers, so we run multiple microservices in one server itself, but due to failure of one microservice, another could be impacted so we run them in isolated containers.

But with microservices came a new challenge:instead of running one big app, companies now had to manage hundreds or thousands of small containerized services. Containers solved the packaging problem, but without a way to orchestrate them, things got messy. That’s where Kubernetes came in acting like a smart manager that automates deployment, scaling, and coordination of all those microservices.

And we containerize these microservices because different microservices need different versions of software and environment, so instead of directly deploying htem on server, we deploy them on containers

---

1. Pod-: 
A Pod is the smallest unit you can deploy in Kubernetes. It wraps one or more containers that need to run together, sharing the same network and storage. Containers inside a Pod can easily communicate and work as a single unit.

2. Node-: 
A Node is a machine (physical or virtual) in a Kubernetes cluster that runs your applications. Each Node contains the tools needed to run Pods, including the container runtime (like Docker), the Kubelet (agent), and the Kube proxy (networking).

3. Cluster-: 
A Kubernetes cluster is a group of computers (called nodes) that work together to run your containerized applications. These nodes can be real machines or virtual ones.

There are two types of nodes in a Kubernetes cluster:

- Master node (Control Plane):
Think of it as the brain of the cluster.
It makes decisions, like where to run applications, handles scheduling, and keeps track of everything.
- Worker nodes:
These are the machines that actually run your apps inside containers.
Each worker node has a Kubelet (agent), a container runtime (like Docker or containerd), and tools for networking and monitoring.
4. Deployment-: 
A Deployment is a Kubernetes object used to manage a set of Pods running your containerized applications. It provides declarative updates, meaning you tell Kubernetes what you want, and it figures out how to get there.

5. ReplicaSet-: 
A ReplicaSet ensures that the right number of identical Pods are running.

6. Service-: 
A Service in Kubernetes is a way to connect applications running inside your cluster. It gives your Pods a stable way to communicate, even if the Pods themselves keep changing.

7. Ingress-: 
Ingress is a way to manage external access to your services in a Kubernetes cluster. It provides HTTP and HTTPS routing to your services, acting as a reverse proxy.

8. ConfigMap-: 
A ConfigMap stores configuration settings separately from the application, so changes can be made without modifying the actual code.

Imagine you have an application that needs some settings, like a database password or an API key. Instead of hardcoding these settings into your app, you store them in a ConfigMap. Your application can then read these settings from the ConfigMap at runtime, which makes it easy to update the settings without changing the app code.

9. Secret-: 
A Secret is a way to store sensitive information (like passwords, API keys, or tokens) securely in a Kubernetes cluster.

10. Persistent Volume (PV)-: 
A Persistent Volume (PV) in Kubernetes is a piece of storage in the cluster that you can use to store data and it doesn’t get deleted when a Pod is removed or restarted.

11. Kubelet-: 
A Kubelet runs on each Worker Node and ensures Pods are running as expected.

12. Kube-proxy-: 
Kube-proxy manages networking inside the cluster, ensuring different Pods can communicate.

---

### Commands
- To view a list of all the pods in the cluster, you can use the following command: kubectl get pods
- To view a list of all the nodes in the cluster, you can use the following command: kubectl get nodes
- To view a list of all the services in the cluster, you can use the following command: kubectl get services



