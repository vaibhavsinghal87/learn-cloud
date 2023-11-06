kubectl version -   

kubectl create deployment <deployment_name> --image=<image_name> --- Creates a deployment named hello  
kubectl scale deployment /hello --replicas =3 --- Scale hello deployment to 3 pods  
Kubectl expose deployment/hello --port 8080 --type NodePort  
Kubectl get svc  
curl localhost:<port_number>  

kubectl describe service <service_name> --- check endpoints of service. They refer to POD IPs to route  

kubectl apply -f nginx-deploy.yaml --- starts nginx deployment on Kubernetes cluster  

kubectl describe pod <pod_name> ---   

kubectl get pods -o wide --- prints additional information about the POD, like IP address  