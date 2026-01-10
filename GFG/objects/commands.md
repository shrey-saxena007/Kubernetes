- Start the minikube software with the following command:
```minikube start```
- Verify whether the minikube is running or not with the following command `minikube status
```minikube status```
- Run the kubernetes pod on using nginx image with the kubectl run command as shown below:  
```kubectl run <pod_name> --image=<your_image_name>```.     
Example-: ```kubectl run ngnix-pod --image=ngnix```.     
On Running the above command, kubectl will create a pod with nginx image extracting from the Docker hub. You can see its creation as a result after running the command on the below screenshot.
- For viewing, list the all pods in the default namespace by the following command. 
```kubectl get pods```
- Connecting to the Minikube environment with ssh protocol by using the following command:  
```minikube ssh```.  
On Executing this command, It will help you landing in minikube interactive environment from your local environment. You can understand it from seeing the hostnames in the below screenshot.
- Check the list of all the running containers inside the Minikube environment with the following command.  
```docker ps -a```.  
The above command list out with displaying all the containers that are created with kubectl from local environment to the Minikube.  
From here we will get access to inside the Nginx-pod and run some commands with the following steps.
- Get inside the nginx pod container with its container_name or container_id knowing from the above step command `docker ps -a`. The following command helps you in going inside the nginx pod container. 
```docker exec -it <Id_of_container> /bin/bash```    
Now we are inside the Nginx-pod, let us run a few shell commands like ls, pwd, and cd.
  