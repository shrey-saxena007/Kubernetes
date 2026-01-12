- Create a deployment named my-nginx, and each deplyment has one pod, so the pod is created automatically, and the container inside the pod is created using docker nginx image. And we have made 5 replicas of pod, in this deployment -: ```kubectl create deployment my-nginx --image=nginx --replicas=5```
- To create a pod also we will use the same command, just replicas=1 will be there, so use same command for creating pods. We don't create pods, we create deployent, which itself manages lifecycle of pod
  
---

- A pod can have multiple containers
- A deployment is has may have multiple pods, but they all are replicas. They are identical to each other. You can not create two different pods in same deployment. A deployment has exactly one Pod template
- To create two different pods, create two different deployments
- So basically deployment is just an abstraction of pods to create its replicas, and we create deployment only, we don't create pods directly
  
---

There are 2 ways to deplot resources in kubernetes-:
1. ```kubectl create```, used in command line to directly create any resource
2. ```kubectl apply`` , used in command line to create a resource defined in manifest file
   
---

