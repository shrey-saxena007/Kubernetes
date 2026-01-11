Labels are key/value pairs that you attach to Kubernetes objects like Pods, Deployments, and Services. They are the primary way to organize your resources. Common examples of labels include:

Example-:   
```
apiVersion: v1
kind: Pod
metadata:
  name: web-server-pod
  labels:
    app: nginx
    tier: frontend
    environment: development
spec:
  containers:
  - name: nginx-container
    image: nginx
```

---

If labels are the sticky notes you put on objects, Selectors are how you find and filter those objects based on the notes. Selectors are used extensively in Kubernetes to define which Pods a Service should target, which Pods a Deployment should manage, and more.

There are two types of selectors:

Equality-Based: The most common type. It filters based on exact key and value matches. The operators are =, ==, and !=.
Set-Based: More flexible. It filters based on whether a key's value is in a set of values. The operators are in, notin, and exists