codebase: https://codelabs.developers.google.com/codelabs/cloud-springboot-kubernetes#3

reference 1: https://spring.io/guides/gs/spring-boot-kubernetes/

```
./mvnw -DskipTests spring-boot:run
./mvnw -DskipTests package

docker build . -t springapp:1.0.0

docker image tag springapp:1.0.0 neossoftware/springapp:1.0.0 

docker push neossoftware/springapp:1.0.0


kubectl create deployment springapp --image=neossoftware/springapp:1.0.0 --dry-run -o=yaml > deployment.yaml
kubectl create service clusterip springapp --tcp=8080:8080 --dry-run -o=yaml >> deployment-service.yaml

kubectl apply -f deployment.yaml
kubectl apply -f deployment-service.yaml

kubectl port-forward svc/springapp 8080:8080
```
