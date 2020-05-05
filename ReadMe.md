

# Kubernetes

### Object types:

- Pod : Runs one or more closely related containers(such as Docker containers).
Pods are the smallest deployable units of computing that can be created and managed in Kubernetes.

- Service : Sets up networking in k8s cluster.

    Sub types:

    1. ClusterIp     : Exposes a set of pods to the other objects in the cluster.
    2. NodePort      : Exposes a container to the 'outside world'. (Only good for dev purposes)
    3. LoadBalancer  : Legacy way of getting traffic into a cluster
    4. Ingress       : Exposes a set of services to the outside world
 
- Deployment: Maintains a set of identical pods, ensuring that they have the correct config and that the right number exists.

- Secret: Securely stores a piece of info in the cluster, such as db password. Secret types- generic, docker-registry and tls.
```
kubectl create secret generic <secret name> --from-literal key=value

kubectl create secret generic pgpassword --from-literal PGPASSWORD=password
```
 





 ### Useful Commands:
 Command to update image:
 ```
 kubectl set image <object_type>/<object_name> <container_name> = <new image to use>

 kubectl set image deployment/client-deployment client=stephengrider/multi-client:v5
 ```

 Connect local docker-client with docker-server inside the virtual machine(minikube) (for current terminal window only)
 ```
 eval $(minikube docker-env)
 ```

 Delete an object:
 ```
 kubectl delete deployment postgres-deployment
 ```

Redeploy/Restart Deployments: (shortcut)
```
kubectl scale deployment client-deployment --replicas=0
```

### Helm:
Helm is a program to administer 3rd party softwares inside k8s cluster.
(3rd party softwares like ingress-nginx)

[command we issue] ---> [helm client] ---> [tiller server]

 ### Sidenotes:

