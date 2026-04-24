# K8-clusters
A repo for testing kubernetes clusters

# To test the deployment of the guest book:
> ## **Deploying the redis-leader deployment and service**
>> kubectl apply -f https://k8s.io/examples/application/guestbook/redis-leader-deployment.yaml
>> kubectl apply -f https://k8s.io/examples/application/guestbook/redis-leader-service.yaml

> **Viewing the logs to verify its running state**
>> kubectl get pods
>> kubectl get service

> **Viewing the logs from the redis-leader pod**
>> kubectl logs -f deployment/redis-leader

> ## **Deploying the follower deployment and server, and verifying**
>> kubectl apply -f https://k8s.io/examples/application/guestbook/redis-follower-deployment.yaml
>> kubectl apply -f https://k8s.io/examples/application/guestbook/redis-follower-service.yaml

> **Viewing the logs** 
>> kubectl get pods
>> kubectl get service

> ## **Deploying the frontend deployment container and service**
>> kubectl apply -f https://k8s.io/examples/application/guestbook/frontend-deployment.yaml
>> kubectl apply -f https://k8s.io/examples/application/guestbook/frontend-service.yaml

> **Verifying that all pods are running**
>> kubectl get pods -l app=guestbook -l tier=frontend
>> kubectl get services

> **Viewing the Frontend Service via kubectl port-forward**
>> kubectl port-forward svc/frontend 8080:80

> **Scaling up or down frontend pod replicas**
>> kubectl scale deployment frontend --replicas=5
>> kubectl scale deployment frontend --replicas=2

> **Verifying that all pods replicas are running**
>> kubectl get pods
>> kubectl get services

> ## **Cleaning Up**
>> kubectl delete deployment -l app=redis
>> kubectl delete service -l app=redis
>> kubectl delete deployment frontend
>> kubectl delete service frontend