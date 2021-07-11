# Kubernetes - The Container Orchestrator Framework
A container orchestrator framework is capable to create, manage, configure thousands of containers on a set of distributed servers while preserving the connectivity and reachability of these containers. In the past years, multiple tools emerged within the landscape to provide these capabilities, including Docker Swarm, Apache Mesos, CoreOS Fleet, and many more. However, Kubernetes took the lead in defining the principles of how to run containerized workloads on a distributed amount of machines.

Kubernetes is widely adopted in the industry today, with most organizations using it in production. Kubernetes currently is a graduated CNCF project, which highlights its maturity and reported success from end-user companies. This is because Kubernetes solutionizes portability, scalability, resilience, service discovery, extensibility, and operational cost of containers.

### Portability
Kubernetes is a highly portable tool. This is due to its open-source nature and vendor agnosticism. As such, Kubernetes can be hosted on any available infrastructure, including public, private, and hybrid cloud.

### Scalability
Building for scale is a cornerstone of any modern infrastructure, enabling an application to scale based on the amount of incoming traffic. Kubernetes has in-build resources, such as HPA (Horizontal Pod Autoscaler), to determine the required amount of replicas for a service. Elasticity is a core feature that is highly automated within Kubernetes.

### Resilience
Failure is expected on any platform. However, it is more important to be able to recover from failure fast and build a set of playbooks that minimizes the downtime of an application. Kubernetes uses functionalities like ReplicaSet, readiness, and liveness probes to handle most of the container failures, which enables powerful self-healing capability.

### Service Discovery
Service discovery encapsulates the ability to automatically identify and reach new services once these are available. Kubernetes provide cluster level DNS (or Domain Name System), which simplifies the accessibility of workloads within the cluster. Additionally, Kubernetes provides routing and load balancing of incoming traffic, ensuring that all requests are served without application overload.

### Extensibility
Kubernetes is a highly extensible mechanism that uses the building-block principle. It has a set of basic resources that can be easily adjusted. Additionally, it provides a rich API interface, that can be extended to accommodate new resources or CRDs (Custom Resource Definitions).

### Operational Cost
Operational cost refers to the efficiency of resource consumption within a Kubernetes cluster, such as CPU and memory. Kubernetes has a powerful scheduling mechanism that places an application on the node with sufficient resources to ensure the successful execution of the service. As a result, most of the available infrastructure resources are allocated on-demand. Additionally, it is possible to automatically scale the size of the cluster based on the current incoming traffic. This capability is provisioned by the cluster-autoscaler, which guarantees that the cluster size is directly proportional to the traffic that it needs to handle.

# Kubernetes Architecture
<img width="644" alt="screenshot-2020-12-20-at-23 25 47" src="https://user-images.githubusercontent.com/71343747/125180442-cdcfb980-e217-11eb-9656-9523ed8ab8bb.png">

A Kubernetes cluster is composed of a collection of distributed physical or virtual servers. These are called nodes. Nodes are categorized into 2 main types: master and worker nodes. The components installed on a node, determine the functionality of a node, and identifies it as a master or worker node.

The suite of master nodes, represents the control plane, while the collection of worker nodes constructs the data plane.
## Control Plane
<img width="426" alt="screenshot-2020-12-20-at-23 31 19" src="https://user-images.githubusercontent.com/71343747/125180452-ecce4b80-e217-11eb-934f-3b0b53b9b609.png">
The control plane consists of components that make global decisions about the cluster. These components are the:
+ kube-apiserver - the nucleus of the cluster that exposes the Kubernetes API, and handles and triggers any operations within the cluster
+ kube-scheduler - the mechanism that places the new workloads on a node with sufficient satisfactory resource requirements
+ kube-controller-manager - the component that handles controller processes. It ensures that the desired configuration is propagated to resources
+ etcd - the key-value store, used for backs-up and keeping manifests for the entire cluster
There are two additional components on the control plane, they are kubelet and k-proxy. These two are special and important as they are installed on all node. You can see the Data Plane below for more details.
## Data Plane
<img width="497" alt="screenshot-2020-12-20-at-23 41 02" src="https://user-images.githubusercontent.com/71343747/125180462-02437580-e218-11eb-87a5-c7626566b4a4.png">
The data plane consists of the compute used to host workloads. The components installed on a worker node are the:
+ kubelet - the agent that runs on every node and notifies the kube- apiserver that this node is part of the cluster
+ kube-proxy - a network proxy that ensures the reachability and accessibility of workloads places on this specific node
Important Note: The kubelet and kube-proxy components are installed on all the nodes in the cluster (master and worker nodes). These components keep the kube-apiserver up-to-date with a list of nodes in the cluster and manages the connectivity and reachability of the workloads.
<b> Note</b>
CRD - Custom Resource Definition provides the ability to extend Kubernetes API and create new resources
Node - a physical or virtual server
Cluster - a collection of distributed nodes that are used to manage and host workloads
Master node - a node from the Kubernetes control plane, that has installed components to make global, cluster-level decisions
Worker node - a node from the Kubernetes data plane, that has installed components to host workloads
# Deploy Your First Kubernetes Cluster
### Cluster Creation
Provisioning a Kubernetes cluster is known as the bootstrapping process. When creating a cluster, it is essential to ensure that each node had the necessary components installed. It is possible to manually provision a cluster, however, this implied the distribution and execution of each component independently (e.g. kube-apiserver, kube-scheduler, kubelet, etc.). This is a highly tedious task that has a higher risk of misconfiguration.

As a result, multiple tools emerged to handle the bootstrapping of a cluster automatically. For example:
+ Production-grade clusters<br/>
 kubeadm<br/>
 Kubespray<br/>
 Kops<br/>
 K3s<br/>
+ Developmnet-grade clusters<br/>
 kind<br/>
 minikube<br/>
 k3d<br/>
# Create Vagrant Box And Install Kubernetes with k3s
Make sure to have VirtualBox 6.1.16 or higher installed.
You also need to install vagrant on your machine.
Throughout the demo, the following kubectl commands are used:
```sh
# Inspect available vagrant boxes 
vagrant status 

# create a vagrant box using the Vagrantfile in the current directory
vagrant up

# SSH into the vagrant box
# Note: this command uses the .vagrant folder to identify the details of the vagrant box
vagrant ssh
```
### New terms
Bootstrap - the process of provisioning a Kubernetes cluster, by ensuring that each node has the necessary components to be fully operational
# Kubeconfig
To access a Kubernetes cluster a kubeconfig file is required. A kubeconfig file has all the necessary cluster metadata and authentication details, that grants the user permission to query the cluster objects. Usually, the kubeconfig file is stored locally under the ~/.kube/config file. However, k3s places the kubeconfig file within /etc/rancher/k3s/k3s.yaml path. Additionally, the location of a kubeconfig file can be set through the --kubeconfig kubectl flag or via the KUBECONFIG environmental variable.

A Kubeconfig file has 3 main distinct sections:

+ Cluster - encapsulates the metadata for a cluster, such as the name of the cluster, API server endpoint, and certificate authority used to check the identity of the user.
+ User - contains the user details that want access to the cluster, including the user name, and any authentication metadata, such as username, password, token or client, and key certificates.
+ Context - links a user to a cluster. If the user credentials are valid and the cluster is up, access to resources is granted. Also, a current-context can be specified, which instructs which context (cluster and user) should be used to query the cluster.
Here is an example of a kubeconfig file:
```sh
apiVersion: v1
# define the cluster metadata 
clusters:
- cluster:
    certificate-authority-data: {{ CA }}
    server: https://127.0.0.1:63668
  name: udacity-cluster
# define the user details 
users:
# `udacity-user` user authenticates using client and key certificates 
- name: udacity-user
  user:
    client-certificate-data: {{ CERT }}
    client-key-data: {{ KEY }}
# `green-user` user authenticates using a token
- name: green-user
  user:
    token: {{ TOKEN }}
# define the contexts 
contexts:
- context:
    cluster: udacity-cluster
    user: udacity-user
  name: udacity-context
# set the current context
current-context: udacity-context
```
# Kubeconfig Walkthrough
In this demo, the instructor uses a cluster bootstrapped with kind. Throughout this course, the students will use k3s to provision a cluser. However, in this demo kind is used to highlight how different tools provision the kubeconfig files.

If the students chose to follows this demo, these are the instructions to create a cluster using kind:

Note: kind can be installed directly on your local machine

+ Ensure Docker is installed and running. Use the docker --version command to verify if Docker is installed.
+ Install kind by using the official installation documentation
+ Create a kind cluster using the kind create cluster --name demo command
```sh
# Inspect  the endpoints for the cluster and installed add-ons 
kubectl cluster-info

# List all the nodes in the cluster. 
# To get a more detailed view of the nodes, the `-o wide` flag can be passed
kubectl get nodes [-o wide] 

# Describe a cluster node.
# Typical configuration: node IP, capacity (CPU and memory), a list of running pods on the node, podCIDR, etc.
kubectl describe node {{ NODE NAME }}
```





















