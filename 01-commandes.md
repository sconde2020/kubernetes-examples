# Kubernetes Main Commands Tutorial

## 20 Essential Kubernetes Commands (Sorted by Usage)

1. **`kubectl get pods`**  
    List all pods in the current namespace.

2. **`kubectl get services`**  
    List all services.

3. **`kubectl get deployments`**  
    List all deployments.

4. **`kubectl describe pod <pod-name>`**  
    Show detailed info about a specific pod.

5. **`kubectl logs <pod-name>`**  
    View logs for a pod.

6. **`kubectl apply -f <file.yaml>`**  
    Create or update resources from a YAML file.

7. **`kubectl delete pod <pod-name>`**  
    Delete a specific pod.

8. **`kubectl exec -it <pod-name> -- /bin/bash`**  
    Access a pod’s shell.

9. **`kubectl get nodes`**  
    List all cluster nodes.

10. **`kubectl scale deployment <deployment-name> --replicas=<count>`**  
     Scale a deployment.

11. **`kubectl rollout status deployment/<deployment-name>`**  
     Check rollout status.

12. **`kubectl edit deployment <deployment-name>`**  
     Edit a deployment resource.

13. **`kubectl port-forward <pod-name> <local-port>:<pod-port>`**  
     Forward a local port to a pod.

14. **`kubectl get namespaces`**  
     List all namespaces.

15. **`kubectl config get-contexts`**  
     List available contexts.

16. **`kubectl config use-context <context-name>`**  
     Switch context.

17. **`kubectl top pods`**  
     Show resource usage for pods.

18. **`kubectl get events`**  
     List cluster events.

19. **`kubectl create namespace <namespace>`**  
     Create a new namespace.

20. **`kubectl delete -f <file.yaml>`**  
     Delete resources defined in a YAML file.
