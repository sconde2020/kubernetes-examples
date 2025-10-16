## What is Kubernetes?

Kubernetes is an open-source platform for automating the deployment, scaling, and management of containerized applications across multiple machines. It handles tasks like distributing workloads, maintaining application availability, and simplifying updates, allowing you to focus on development while it manages the infrastructure.

## Main Concepts

### 1. Cluster
A cluster is a group of machines (nodes) that work together to run containerized applications managed by Kubernetes. It provides high availability, scalability, and fault tolerance.

```
+---------------------+
|     Kubernetes      |
|      Cluster        |
| +-----+  +-----+    |
| |Node1|  |Node2| ...|
| +-----+  +-----+    |
+---------------------+
```

### 2. Node
A node is a physical or virtual machine within the cluster. Each node runs pods and contains the necessary services to manage them, such as kubelet and container runtime.

```
+-------+
| Node  |
| +---+ |
| |Pod| |
| +---+ |
+-------+
```

### 3. Pod
A pod is the smallest deployable unit in Kubernetes. It consists of one or more containers that share storage, network, and a specification for how to run the containers.

```
+------+
| Pod  |
| +---+|
| |Ctr||
| +---+|
+------+
```

### 4. Deployment
A deployment is a Kubernetes resource that manages the creation and updating of pods and their replica sets. It ensures that the specified number of pod replicas are always running, and handles rolling updates and rollbacks automatically to maintain application availability.

```
Deployment
     |
ReplicaSet
     |
   Pods
```

### 5. Service
A service exposes pods to the network, enabling communication between components and external clients. It provides load balancing and stable endpoints for accessing pods.

```
Client
  |
Service
  |
Pods
```

### 6. Namespace
Namespaces provide logical separation within a cluster, allowing multiple teams or projects to share the same cluster without interfering with each other.

```
+-------------------+
|   Namespace A     |
|   Namespace B     |
+-------------------+
```

### 7. API Server
The API server is the central management entity that exposes the Kubernetes API. All operations—such as creating, updating, or deleting resources—are performed by interacting with the API server.

```
kubectl
   |
API Server
   |
Resources
```

### 8. kubectl
`kubectl` is the command-line tool for interacting with the Kubernetes API server. It allows users to manage cluster resources, view status, and perform administrative tasks.

Example usage:
```sh
kubectl get pods
kubectl apply -f deployment.yaml
kubectl describe service my-service
```
