## Basic Concepts

- **Cluster**: A set of nodes that run containerized applications.
- **Node**: A single machine in a Kubernetes cluster, which can be either a virtual or a physical machine.
- **Pod**: The smallest deployable unit in Kubernetes, consisting of one or more containers.
- **Service**: An abstraction that defines a logical set of pods and a policy by which to access them.
- **Deployment**: A controller that provides declarative updates to applications.
- **ConfigMap**: A way to inject configuration data into Kubernetes pods.
- **Secret**: A way to store and manage sensitive information such as passwords, OAuth tokens, and ssh keys.

## Common Commands

### kubectl Installation

#### On Ubuntu
```
sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl
sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
```

## Check kubectl Version
```
kubectl version --client
```

## kubectl Help
```
kubectl --help
```

# Working with Clusters

## Get Cluster Info
```
kubectl cluster-info
```

## List Nodes
```
kubectl get nodes
```

# Working with Pods

## List Pods
```
kubectl get pods
```

## Create a Pod
```
# pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
    - name: mycontainer
      image: nginx
```
sh
```
kubectl apply -f pod.yaml
```

## Describe a Pod
```
kubectl describe pod <pod_name>
# Example:
kubectl describe pod mypod
```

## Delete a Pod
```
kubectl delete pod <pod_name>
# Example:
kubectl delete pod mypod
```

# Working with Deployments

## List Deployments
```
kubectl get deployments
```

## Create a Deployment
```
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mydeployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
        - name: mycontainer
          image: nginx
```
sh
```
kubectl apply -f deployment.yaml
```

## Scale a Deployment
```
kubectl scale deployment <deployment_name> --replicas=<number_of_replicas>
# Example:
kubectl scale deployment mydeployment --replicas=5
```

## Update a Deployment
```
kubectl set image deployment/<deployment_name> <container_name>=<new_image>
# Example:
kubectl set image deployment/mydeployment mycontainer=nginx:latest
```

## Delete a Deployment
```
kubectl delete deployment <deployment_name>
# Example:
kubectl delete deployment mydeployment
```

# Working with Services

## List Services
```
kubectl get services
```

## Create a Service
```
# service.yaml
apiVersion: v1
kind: Service
metadata:
  name: myservice
spec:
  selector:
    app: myapp
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
```
sh
```
kubectl apply -f service.yaml
```

## Describe a Service
```
kubectl describe service <service_name>
# Example:
kubectl describe service myservice
```

## Delete a Service
```
kubectl delete service <service_name>
# Example:
kubectl delete service myservice
```

# ConfigMaps and Secrets

## Create a ConfigMap from a Literal
```
kubectl create configmap <configmap_name> --from-literal=<key>=<value>
# Example:
kubectl create configmap myconfig --from-literal=key1=value1
```

## Create a ConfigMap from a File
```
kubectl create configmap <configmap_name> --from-file=<filename>
# Example:
kubectl create configmap myconfig --from-file=config.txt
```

## Create a Secret from a Literal
```
kubectl create secret generic <secret_name> --from-literal=<key>=<value>
# Example:
kubectl create secret generic mysecret --from-literal=password=secret
```

## Create a Secret from a File
```
kubectl create secret generic <secret_name> --from-file=<filename>
# Example:
kubectl create secret generic mysecret --from-file=secret.txt
```

# Useful Commands

## Get Cluster Events
```
kubectl get events
```

## Get Logs from a Pod
```
kubectl logs <pod_name>
# Example:
kubectl logs mypod
```

## Execute a Command in a Pod
```
kubectl exec -it <pod_name> -- <command>
# Example:
kubectl exec -it mypod -- /bin/bash
```

# Resources

[Kubernetes Documentation](https://kubernetes.io/docs/home/)

This cheat sheet provides a comprehensive overview of Kubernetes, covering basic concepts, common commands, working with clusters, pods, deployments, services, configmaps, and secrets.
