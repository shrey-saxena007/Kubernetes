Kubectl is command-line software that helps to run commands in the Kubernetes Cluster

---

Basic structure of kubectl command-:  
```kubectl [command]  [TYPE]  [NAME]  [flags]```
- command: This will include the operation mentioned below you want to perform regarding the specific resource
   - create
   - get
   - describe
   - delete
- Type: Here you have to mention the specific resource provided by Kubernetes that you want to create like kubernetes pods, Kubernetes namespaces, Kubernetes secrets, Kubernetes deployment, replica sets, and many more. This option is a case-sensitive
- NAME: Here we will provide the name which is case-sensitive.
- flags: This will use to pass the flags like address or port number.

---

- Create a namespace ```kubectl create namespace geeksforgeeks```
- Now create a pod, using a yaml file
  ```text
        apiVersion: v1
        kind: Pod
        metadata:
        name: geeksforgeeks
        namespace: geeksforgeeks
        spec:
        containers:
        - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
  ```

- The above file is a configuration file using which we are creating a pod of name geeksforgeeks in namespace geeksforgeeks which is an Nginx server. Similarly, we can create other resources like secrets, replica sets, etc by just changing the name in front of the kind and mentioning the key value in metadata and spec accordingly
- Execute this file ```kubectl create -f geeksforgeekspod.yaml```
- ```kubectl get pods``` will give all the pods in the defalt namespace, but to list all pods in a specific namespace, we pass flag '-n' ```kubectl get pods -n <namespace_name>```
- 

