## Project 1: Hello Kubernetes

This project demonstrates basic Kubernetes concepts: Pods, Deployments, Services, and scaling.

### 1. Deploy an Nginx Pod

Create a file named `nginx-pod.yaml`:

```yaml
apiVersion: v1           # Use Kubernetes core API version
kind: Pod                # Define a Pod resource
metadata:
    name: nginx-pod      # Name the Pod 'nginx-pod'
spec:
    containers:
        - name: nginx        # Name the container 'nginx'
            image: nginx:latest  # Use the latest nginx image
            ports:
                - containerPort: 80  # Expose port 80 in the container
```

Apply the manifest:

```sh
kubectl apply -f nginx-pod.yaml
kubectl get pods
```

### 2. Expose Nginx via NodePort Service

Create a file named `nginx-service.yaml`:

```yaml
apiVersion: v1           # Use Kubernetes core API version
kind: Service            # Define a Service resource
metadata:
    name: nginx-service  # Name the Service 'nginx-service'
spec:
    type: NodePort       # Expose the Service via NodePort
    selector:
        app: nginx           # Select Pods with label 'app: nginx'
    ports:
        - port: 80           # Service port 80
            targetPort: 80   # Target Pod port 80
            nodePort: 30080  # NodePort assigned as 30080
```

Update the Pod to include a label for the selector. Edit `nginx-pod.yaml`:

```yaml
metadata:
    name: nginx-pod      # Name the Pod 'nginx-pod'
    labels:
        app: nginx       # Add label 'app: nginx' for Service selector
```

Re-apply the Pod and Service:

```sh
kubectl apply -f nginx-pod.yaml
kubectl apply -f nginx-service.yaml
kubectl get svc
```
To get the Minikube IP address, run:

```sh
minikube ip
```
Minikube is a local Kubernetes cluster that runs on your machine for development and testing purposes. If you are using Minikube, you can access Nginx in your browser at `http://<minikube_ip>:30080`, replacing `<minikube_ip>` with the output from the `minikube ip` command above.

### 3. Scale with Deployment

Create a file named `nginx-deployment.yaml`:

```yaml
apiVersion: apps/v1                # Use the apps/v1 API for Deployments
kind: Deployment                   # Define a Deployment resource
metadata:
    name: nginx-deployment         # Name the Deployment 'nginx-deployment'
spec:
    replicas: 3                    # Run 3 Pod replicas
    selector:
        matchLabels:
            app: nginx             # Select Pods with label 'app: nginx'
    template:                      # Pod template for Deployment
        metadata:
            labels:
                app: nginx         # Label Pods with 'app: nginx'
        spec:
            containers:
                - name: nginx      # Name the container 'nginx'
                    image: nginx:latest    # Use the latest nginx image
                    ports:
                        - containerPort: 80    # Expose port 80 in the container
```

Apply the deployment:

```sh
kubectl apply -f nginx-deployment.yaml
kubectl get deployments
kubectl get pods
```

Update the Service selector if needed to match the deployment label.

### 4. Scale Up/Down

Scale the deployment:

```sh
kubectl scale deployment nginx-deployment --replicas=5
kubectl get pods
```

---

**Skills Practiced:** Pods, Deployments, Services, scaling

