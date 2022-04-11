### Components of Kubernetes
Kubeadm: is a tool which is used to setup kubernetes cluster.
etcd: memory of the k8s cluster in which status of the object is saved.
Scheduler: will create the pod.
Controller manager: will try to maintain the status of the pod.
Control-Plane or Kubectl : is the machine where we will execute our commands
Kube-Proxy: for maintaining and managing the network components in Kubernetes cluster. Ex: WeaveNet
API Server: It exposes HTTP API that lets end users, different parts of your cluster and external components to communicate with each other. 

### Pod:
Pod is the smallest deployable unit in K8s. Each pod will get unique IP address. Each pod can have single or multiple containers and all the containers in the pod will have same IP address.

K8s Namespace: K8s supports multiple virtual clusters backend by same physical cluster and these virtual clusters are called namespaces.
for any object in K8s there are 2kinds of scopes.
1. cluster scope
2. namespace scope

Types of Probes:
Probes are the health checks.
1. Liveness Probe: Used to check whether a container is running or not.
2. Readiness Probe: used to check whether container is ready to receive requests or not.
### Configuration of Probes:
1. initialDelaySeconds
2. periodSeconds
3. timeoutSeconds
4. successThreshold
5. failureThreshold

### implementation of Probes:
1. command probe
2. HttpRequest probe
3. TCP Socket Probes

### __RestartPolicy__: 
restart policy instructs the controllers about the conditions to restart the pod. There are 3 types of restart values: 1. Always 2. Never 3. OnFailure

### Labels and Annotations:
Lables and annotations provide metadata information but labels can be used for filtering and selecting where as annotations cannot be used for filtering.
2 types of label selectors:
1. equality based: =, ==, !=
2. set based: in, not in, exists

Controllers: controllers are used for maintaining and managing pods. Below are the types of controllers.
1. ReplicaSets: used to maintaining number replica of pods.
2. Deployments: Deployment acts as a wrapper around replica set. Deployement Controller maintains the history of revisions. Deployment makes it easy to rollback to previous state or versions.
Deployment uses __strategy__ section to replace the old pods with new pods. There are 2 types of strategies in Deployment.
i. RollingUpdate: uses maxUnavailable, maxSurge to prevent downtime.
ii. Recreate: deletes all the pods before new pods are created. there will be downtime.
3. Daemon Sets: Daemon sets are used for creating pod on all or selected nodes in a cluster.
Uses Cases of Daemon Sets are:
    1. to get the logs
    2. centralised monitoring
    3. local data caching
4. Jobs: Job is a supervisor in kubernetes that is used to manage pod to run some script or task and exit gracefully. Pods created by Jobs are not deleted after the job is completed.
5. Stateful Sets

### Kubernetes Services
Kubernetes Services help us to connect with the pods with the external world as well as to communicate with other pods internally.
Types of Kubernetes Services:
1. NodePort: help to communicate with kubernetes cluster from external world
2. ClusterIP: helps to maintain internal communication.
3. LoadBalancer
4. ExternalName

### Volumes
1. Kubernetes Volumes: have only pod scope. If the pod is restarted or lost then Kubernetes volumes are lost.
2. Persistent Volumes: have cluster scope. Persistent volumes exist even if the pod is restarted or lost. Only if the cluster is deleted or Persitent Volumes are deleted we will loose the data.
We need to request Persistent Volumes using Persistent Volume Claim.
## PersistentVolumeReclaimPolicy: is namespace scoped
1. Retain
2. Recycle
3. Delete
## Persistent Volume Status
1. Availabe
2. Bound
3. Released
4. Failed

### Config Maps and Secrets:
Config maps helps us to define application related data. Config maps can be created from literal value or from a file.

Secrets are much like config maps but they are base64 encoded. 
there are 3 available secrets.
1. Generic: holds key value pairs
2. TLS: holds public-private key for TLS protocol
3. DockerRegistry: holds user names and passwords to connect to private registries

