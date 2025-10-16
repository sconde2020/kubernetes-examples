# Project 2: Configured Web App

This tutorial guides you through deploying a Spring Boot backend web app on Kubernetes, using ConfigMap for configuration and Secret for the database password.

## 1. Create a Spring Boot Backend App

```java
// src/main/resources/application.properties
spring.datasource.url=${DB_URL}
spring.datasource.username=${DB_USER}
spring.datasource.password=${DB_PASSWORD}
app.custom.config=${APP_CONFIG}
```

## 2. Build Docker Image

```dockerfile
# Dockerfile
FROM openjdk:17-jdk-alpine
COPY target/webapp.jar /app/webapp.jar
ENTRYPOINT ["java", "-jar", "/app/webapp.jar"]
```

### Build the Docker image

```sh
docker build -t your-dockerhub/webapp:latest .
```

### Push the image to Docker Hub

```sh
docker login
docker push your-dockerhub/webapp:latest
```

## 3. Create Kubernetes resources

Apply all resources from the k8s/ directory (use the provided YAML files):

### ConfigMap
```sh
kubectl apply -f k8s/configmap.yaml
```

### Secret
If you already have k8s/secret.yaml:  

```sh
kubectl apply -f k8s/secret.yaml
```  

To generate a secret YAML locally (keeps secret file under k8s/):  

```sh
kubectl create secret generic db-secret --from-literal=DB_PASSWORD='CHANGE_ME' \
    --dry-run=client -o yaml > k8s/secret.yaml
kubectl apply -f k8s/secret.yaml
```

### Deployment
```sh
kubectl apply -f k8s/deployment.yaml
kubectl describe deployment webapp
kubectl get pods -l app=webapp
```

### Service
```sh
kubectl apply -f k8s/service.yaml
kubectl get svc -l app=webapp
```

### Cleanup
Remove all applied resources from k8s/:  

```sh
kubectl delete -f k8s/ --ignore-not-found
```

## 4. Access the Web App
Use this URL format to call the API:

http://$(minikube ip):${nodePort}/api/tasks

Find the values and test:

```sh
# get Minikube IP
minikube ip

# get the NodePort of the webapp service
kubectl get svc webapp-service -o jsonpath='{.spec.ports[0].nodePort}'
```

Or let Minikube give you a URL:

```sh
minikube service webapp-service --url
# then open the printed URL and append /api/tasks in your browser
```
## 5. Kubernetes Service Port Flow with NodePort

When using a NodePort service in Kubernetes like in this example, the flow of network traffic is as follows:

        ┌──────────────────────────────┐
        │        Web Browser           │
        │  http://192.168.49.2:30080   │
        └──────────────┬───────────────┘
                       │
                       ▼
        ┌──────────────────────────────┐
        │       Minikube Node          │
        │  NodePort = 30080            │
        │  (exposes service externally)│
        └──────────────┬───────────────┘
                       │
                       ▼
        ┌──────────────────────────────┐
        │     Kubernetes Service       │
        │  ClusterIP = 10.99.225.23    │
        │  Port = 80                   │
        │  Forwards traffic to pods    │
        └──────────────┬───────────────┘
                       │
                       ▼
        ┌──────────────────────────────┐
        │     WebApp Pod (Container)   │
        │  TargetPort = 8080           │
        │  Runs app on :8080           │
        └──────────────────────────────┘

1. The web browser sends a request to the Minikube node's IP address on the NodePort (30080).
2. Minikube routes the request to the Kubernetes Service associated with the web app.
3. The Service forwards the request to one of the web app pods on the target port (8080).
4. The web app processes the request and sends the response back through the same path

