# Kubernetes Commands

## Cluster and Context Management

- kubectl config get-contexts: List all contexts.
- kubectl config use-context [context_name]: Switch to a different context.
- kubectl config current-context: Display the current context.
- kubectl cluster-info: Display cluster information.

## Pods and Workloads

- kubectl get pods: List all pods.
- kubectl get pods --all-namespaces: List all pods in all namespaces.
- kubectl describe pod [pod_name]: Describe a specific pod.
- kubectl logs [pod_name]: Fetch logs from a pod.
- kubectl logs -f [pod_name]: Follow the logs of a pod in real-time.
- kubectl exec -it [pod_name] -- /bin/bash: Execute a command in a pod.
- kubectl delete pod [pod_name]: Delete a specific pod.
- kubectl port-forward [pod_name] [local_port]:[pod_port]: Forward one or more local ports to a pod.

## Deployments and Services

- kubectl get deployments: List all deployments.
- kubectl describe deployment [deployment_name]: Describe a specific deployment.
- kubectl get services: List all services.
- kubectl describe service [service_name]: Describe a specific service.
- kubectl delete service [service_name]: Delete a specific service.

## Configuration and Scaling

- kubectl apply -f [config_file]: Apply a configuration file.
- kubectl delete -f [config_file]: Delete resources defined in a configuration file.
- kubectl scale deployment [deployment_name] --replicas=[count]: Scale a deployment.
- kubectl rollout status deployment [deployment_name]: Show the status of a rollout.
- kubectl rollout undo deployment [deployment_name]: Undo a deployment rollout.
