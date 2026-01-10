Kubernetes Nodes are the Worker or master machines where the actual work happens

Each Kubernetes Node can have multiple pods and pods have containers running inside them. These three processes in every Node are used to Schedule and manage those pods-: 
- Container runtime: A container runtime is needed to run the application containers running on pods inside a pod. Example: Docker.
- kubelet: kubelet interacts with both the container runtime as well as the Node. It is the process responsible for starting a pod with a container inside.
- kube-proxy: It is the process responsible for forwarding the request from Kubernetes Services to the pods. It has intelligent logic to forward the request to the right pod in the worker node.

---

Status Of Kubernetes Nodes
- Ready: The node is running healthy where the scheduler can schedule the pods in that Node.
- NotReady: The node is not yet ready to run the pods. This occurs because of so many reasons some of them are some of them are like a network issue, a pod failure, or a kubelet error.
- Unknow: If the node is not responding to scheduler to schedule the pods. If the master node can't communicate with that node then then the status will be shown as unknow.

---

The node which is already available in the cluster or node which is going to be created newly should be register in the API server by that the master will starts too recognise the node which are available in the kubernetes cluster.

Instead of doing it manually it can be automated which is also a preferred way of doing. By default this self registration will be enabled in the kubernetes cluster kubelet will take will takes responsible for automatic registration.

The following are the different options for self registratin of kubernetes Nodes:

- Aceses To Kubeconfig File: We can provide the path of kubeconfig file to the kubelet by which it can authenticate with the API server.
- Setting The Flag True: "--register-nodes" the default value is true when it is set to true kubelet will contact the API server and send the all the information to the node which is newly added and the API server creates node object in the kubernetes cluster and kubernetes scheduler will use the node objects to schedule the pods on nodes.

---

Manual node administration in the kubernetes refer to the regestring the nodes maually with out any self registration of nodes there are certain commands to use to maually administer the nodes like following.
```kubectl create node```
