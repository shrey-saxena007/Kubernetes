- un a two-replica nginx deployment -: ```kubectl run my-nginx --image=nginx --replicas=5 --port=80```
- Run and expose the Nginx pod -: ```kubectl run my-nginx --restart=Never --image=nginx --port=80 --expose```
- Run nginx deployment and expose it -: ```kubectl run my-nginx --image=nginx --port=80 --expose```
  
