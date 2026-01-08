- first create a cluster
- pull a image from docker hub
  ```text
      docker pull nginx
  ```
- ```text 
  kubectl create deployment my-nginx --image=nginx:latest 
  ```
  - you never create pods directly, deployment manages them so here we created a deployment named my-nginx
  - inside that deplyment a pod is created, and inside that pod, a container of nginx is running
  
- kubectl get deployments -: gives all deployment in a namespace.  
- kubectl get pods -: gives all pods in a namespace, it also mentions , which deplyment it is comming from
- 