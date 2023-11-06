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
kubectl exec pod/<pod_name> -- printenv  
kubectl exec -it pod/<pod_name> -- /bin/sh  

---  
  
**POD to POD communication from inside cluster -**  
kubectl create deployment hello --image=gcriogooglesamples/hello-app:2.0  
kubectl expose deployment/hello --port 8080 --type NodePort  
kubectl create deployment nginx --image=nginx  
kubectl exec -it <nginx_pod_name/pod_ip> -- curl hello:8080 -- PODs inside a cluster can issue request to each other using POD name/IP:port  

localhost:<exposed_port> - Access a POD in browser using exposed port to outside world from kubernetes cluster  

---
