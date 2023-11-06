**Create and scale a deployment -**  
kubectl create deployment hello --image=gcriogooglesamples/hello-app:2.0  
kubectl scale deployment/hello --replicas=3  
kubectl get pods -o wide  
kubectl expose deployment/hello --port 8080 --type NodePort  
kubectl get svc  
curl localhost:<port_number>  

--- 

**Run command inside POD -**  
kubectl create deployment nginx --image=nginx  
kubectl exec deployment/nginx -- date  
kubectl exec pod/<pod_name> -- date  

---
