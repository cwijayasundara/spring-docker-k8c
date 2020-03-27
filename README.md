# spring-docker-k8c
Sample Spring Boot app with Docker and K8C

You need to have K8C running in your local

kubectl cluster-info

kubectl get all

docker build -t cham/order-service .

docker run -p 8080:8080 cham/order-service

curl localhost:8080/actuator/health

Deploy the app in K8C 

create the deployment.yaml

kubectl create deployment order --image=cham/order-service --dry-run -o=yaml > deployment.yaml

kubectl create service clusterip order --tcp=8080:8080 --dry-run -o=yaml >> deployment.yaml

Start K8C
kubectl apply -f deployment.yaml

kubectl get all
