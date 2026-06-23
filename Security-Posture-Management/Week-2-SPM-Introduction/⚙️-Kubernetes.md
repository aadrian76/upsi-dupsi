<details open>
    <summary style="font-size: 16px; font-weight: bold; cursor: pointer;">
        Table of Contents
    </summary>

  [[_TOC_]]
</details>

  

  

## 📝 Changelog


| Author       | Modification Date | Changes               |
|-------------|-----------------|---------------------|
|             | 25/02/2025      | First Version Created |

  

  

---

  

  

## 🚀 Docker and Kubernetes

## 🔹 What is Kubernetes? 🏗️

Kubernetes is a platform for managing containerized workloads and services.

  

Kubernetes eliminates many of the manual processes involved in deploying and scaling containerized applications through **declarative configuration and automation**.

### 🎯 Why You Need Kubernetes

Containers are a good way to bundle and run applications, but in a **production environment**, managing them can be complex. For example, if a container goes down, another needs to start. Instead of manually handling these issues, **Kubernetes automates** the process, ensuring resilience and efficiency.

**Key Features of Kubernetes:**

  

- **🔍 Service Discovery & Load Balancing**: Exposes a container using DNS name or IP.

  

- **💾 Storage Orchestration**: Allows to automatically mount a storage system like local storages, public cloud providers, etc

  

- **📦 Automated Rollouts & Rollbacks**: You can describe the desired state for your deployed containers using kubernetes and it can change the current state to the desired state at a controlled rate.

  

- **⚙️ Automated Bin Packing**

  

- **🔁 Self-Healing**: Restarts containeres that fail or don't responde to user-defined health check.

  

- **🔑 Secret & Configuration Management**: Lets you store and manage passwords, OAuth tokens and SSH keys.

  

Batch execution

  

- **🛠️ Batch Execution**

  

- **📈 Horizontal Scaling**

  

- **🌍 IPv4/6 Dual Stack**: Allocation of IP addresses to pods and services.

  

---

## 🔹 Kubernetes Architecture 🏗️

  

When you deploy Kubernetes, you get a **cluster**. A cluster in Kubernetes terminology is a **collection of virtual machines or physical machines where applications and services are run**.

  

The virtual or physical machines in Kubernetes where applications are run are called **Nodes**.

A cluster in real world deployments has more than one node, but one node clusters is allowed.

A cluster can be made up of **more than one** virtual machine or physical machine or a combination of both.

  

📌 **Key Components of a Kubernetes Cluster:**

- **Nodes**: Run pods, hosting application workloads.

  

- **Control Plane**: Manages worker nodes and pod scheduling.

  

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://i.imgur.com/2PGXsS1.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">A Cluster</div>
</div>

  

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://i.imgur.com/3VeB5GB.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Control Plane and Worker Nodes</div>

</div>

<div style="text-align: center; width: 600px; margin: auto;">
    <img src="https://i.imgur.com/KVNHu0m.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Pods</div>
</div>

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://i.imgur.com/avxfqnZ.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Large Cluster</div>
</div>

 

A cluster is divided in two setions:

- **Nodes** host the pods that are the components of the application workload

- **Control plane** manages the worker nodes and the pods. Usually runs across multiple computers

  
  

### ⚙️ Control Plane Components

  

The **Control Plane** makes decisions about the cluster and detects/responds to events.

  

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://i.imgur.com/3378BFi.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
         alt="image caption">
    <div style="color: gray; font-size: small; font-style: italic;">Small Cluster</div>
</div>

  

- **📡 Kube-apiserver**: The frontend API for Kubernetes.

- **📂 etcd**: Stores all cluster data in a key-value format.

- **📅 Kube-scheduler**: Assigns newly created pods to nodes.

- **⚙️ Kube-controller-manager**: Manages node health, job execution, and endpoint configurations.

  Some examples of them:

  

  - Node controller: Responsible for noticing and responding when nodes go down.

  - Job controller

  - EndpointSlice controller

  

- **☁️ Cloud-controller-manager**: Integrates with cloud provider APIs.


### 🖥️ Node Components

Node components maintain running pods and provide the Kubernetes runtime environment.

  

- **🤖 Kubelet**: Ensures containers are running in a pod.

  

- **🔀 Kube-proxy**: Manages network traffic between nodes.

  

- **📦 Container Runtime**: Executes and manages container lifecycles.

  
  

---

  

## 🔹 Kubernetes Objects 📦

Kubernetes objects are **persistent entities** in the Kubernetes system. Kubernetes **uses these entities to represent the state of your cluster. Specifically, they can describe:

- What **containerized** applications are running (and on which nodes)

- The **resources available** to those applications


- The policies around how those applications behave, such as restart **policies, upgrades, and fault-tolerance**


A Kubernetes object is a **"record of intent"**--once you create the object, the Kubernetes system **will constantly work** to ensure that object exists (desired state).


To work with Kubernetes objects you'll need to use the Kubernetes API.

**Common Kubernetes Objects:**

- **Pod**: The smallest unit of deployment.


- **Service**: Manages communication between pods.


- **Volume**: Provides storage for pods.


- **Namespace**: Isolates resources within a cluster.


**High-Level Abstractions:**


- **ReplicaSet**: Ensures a specified number of pod replicas run at all times.


- **Deployment**: Manages application updates.


- **StatefulSet**: Manages stateful applications.


- **DaemonSet**: Ensures a copy of a pod runs on all nodes.
 

- **Job**: Runs tasks to completion.


### 📝 Object Spec and Status 📋

  

Almost every **Kubernetes object** includes two key fields that define its configuration:


- **🔧 Spec (Specification)**: Defines the **desired state** of the object.


- **📌 Status**: Represents the **current state**, continuously updated by Kubernetes.
  

Kubernetes **actively manages** the actual state to match the desired state.
  

### 📜 Describing a Kubernetes Object  

  

Kubernetes objects are **defined using YAML manifests**. The API request **must include JSON** in the HTTP body, but `kubectl` automatically converts YAML to JSON.


#### ✏️ Required Fields in a Manifest

  

A **manifest** is a YAML (or JSON) file that defines a Kubernetes object. It must include:



- **`apiVersion`** → Specifies the **Kubernetes API version** used to create the object.
 

- **`kind`** → Defines **the type of object** (e.g., `Pod`, `Service`, `Deployment`).


- **`metadata`** → Contains **name, UID, and optional namespace** for identification.


- **`spec`** → Defines **the desired state** of the object.



For an in-depth format reference, check the **[Kubernetes API Reference](https://kubernetes.io/docs/reference/kubernetes-api/)**.



### 📝 Object Management



Kubectl command-line tool supports several different ways to create and manage Kubernetes objects.

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://imgur.com/9fz1bn7.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
        alt="Object Management">
    <div style="color: gray; font-size: small; font-style: italic;">Object Management</div>
</div>

  

#### Imperative commands

  

Operates directly on live objects in a cluster.
The recommended way to get started or to run a one-off task in a cluster.

`kubectl create deployment nginx --image nginx`

#### Imperative object configuration

`kubectl create -f nginx.yaml`

`kubectl delete -f nginx.yaml -f redis.yaml`

`kubectl replace -f nginx.yaml`

#### Declarative object configuration

Process all object configuration files in the configs directory, and create or patch the live objects.

  

You can first diff to see what changes are going to be made, and then apply:

`kubectl diff -f configs/`

  

`kubectl apply -f configs/`

  

Recursively process directories:

  

`kubectl diff -R -f configs/`

  

`kubectl apply -R -f configs/`

  

---

  

## Namespaces 🏷️

  

**Namespaces** provide a mechanism for isolating groups of resources within a single cluster. Resource names only need to be unique within a namespace (not across the entire cluster). Namespace-based scoping applies to **namespaced objects** (e.g., Deployments, Services) but **not** to cluster-wide objects (e.g., StorageClass, Nodes).

  

- **No nesting**: You can’t have a namespace inside another namespace.  

- **One namespace per resource**: Each resource belongs to exactly one namespace.

  

### When to Use Multiple Namespaces? 🤔

  

- If your environment has **many** users, multiple teams, or distinct projects.  

- If you want to apply resource quotas or separate dev/test from production logically.  

- For small clusters with a few users, you might not need extra namespaces at all.

  

**Pro Tip**: Use namespaces to isolate resources between different groups/users. For things like different software versions, it might be simpler to just use labels rather than spawning multiple namespaces.

  

### Managing Namespaces 🔧

  

- List current namespaces  

  `kubectl get namespace`

  

- Set the namespace for a request** (instead of always using `-n`):

  

  `kubectl run nginx --image=nginx --namespace=<insert-namespace-name-here>`

  

- Create a namespace

  

  `kubectl create namespace <name>`

  

- Delete a namespace

  

  `kubectl delete namespace <name>`

  

  Deletion is asynchronous. The namespace will remain in a `_terminating_` state until it’s fully gone.

  

> **Note**: Deleting a namespace is final—it nukes every resource (pods, services, etc.) in it.

  

- Set a default namespace

  

    ```
    kubectl config set-context --current --namespace=<insert-namespace-name-here>
    # Validate it
    kubectl config view --minify | grep namespace:
    ```

    This will set the default namespace to ‘testing’ for all future kubectl commands.

  
  

---

  

# Cluster Architecture 🏭

  

## Nodes 🏗️

  

Kubernetes runs your apps by placing containers (inside pods) onto **Nodes**. A node can be a virtual or physical machine. The control plane manages nodes and ensures each node has the services needed to run pods.

- Typically, you have **multiple nodes** to handle workload distribution and fault tolerance.

- In small or test setups, you might only have one node (but then if it fails, all your pods vanish).

  

## Contexts 🌐

  

Contexts are shortcuts that let you quickly switch between different cluster configurations without typing long and tedious commands.

  

To view the kubeconfig file where contexts are stored:

`kubectl config view`

  

To view contexts:

`kubectl config get-contexts`

  

<div style="text-align: center; width: 600px; margin: auto;">

  

    <img src="https://imgur.com/3GQWiXW.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
        alt="Get Contexts">
    <div style="color: gray; font-size: small; font-style: italic;">Get Contexts</div>

</div>

  

You can create and modify contexts in your kubeconfig file by using the command `kubectl config set-context` with different options.

    `kubectl config set-context <NAME> [--cluster=<cluster>] [--user=<user>] [--namespace=<namespace>] [--current]`

You can switch between contexts by using the command `kubectl config use-context` with different context names.

---

## 🔹 Kubernetes Workloads ⚙️

A workload is an application running on Kubernetes.

### 🚀 Pods

A **Pod** represents a set of running containers with shared storage and networking resources.

Workload resources like **Deployments, StatefulSets, and DaemonSets** manage pods efficiently.


### 🛠️ Deployments


- Manages **stateless** application workloads.

- Uses **ReplicaSets** for scaling and availability.


### 🏗️ StatefulSets

- Manages **stateful** applications.

- Ensures pods retain unique identities.


### 🔄 DaemonSets

- Runs a copy of a **pod on every node**.

- Often used for logging, monitoring, or networking.

---


## 🚀 Workload Resources

Managing **each Pod individually** can be **complex**. Instead, **Kubernetes provides workload resources** that simplify **Pod management and scaling**.


### 📦 Pods

A **Pod** represents a **set of running containers** on your cluster. It includes:

- **Shared storage**  

- **Network resources**  

- **Specifications** for running the containers  

🔹 **Pods are the smallest deployable units in Kubernetes**.

### 📌 Deployments (and ReplicaSet)


- **The most common way** to run an application in Kubernetes.  

- Ideal for **stateless applications**, ensuring Pods can be **easily replaced and scaled**.  

- Uses **ReplicaSets** to maintain **the correct number of running Pods**.


### 🔄 ReplicaSet

- Maintains a **stable number of running Pods**.

- **Ensures high availability and automatic scaling**.

- Useful for **load balancing and handling failures**.

  

### 🏛️ StatefulSets

- Used for **stateful applications** that require **persistent storage**.

- Unlike **Deployments**, **Pods in a StatefulSet have unique identities**.

- Ensures each Pod is connected to the same **PersistentVolume (PV)** after restarts.

  

📌 **Example Use Cases:**  


✔ **Databases (MySQL, PostgreSQL, MongoDB)**  

✔ **Message brokers (Kafka, RabbitMQ)**  

✔ **Persistent caching systems (Redis, etc.)**  

### 🔁 DaemonSet


- Ensures that **a Pod runs on every node** in the cluster.  

- Often used for **monitoring, logging, or networking components**.  

📌 **Example Use Cases:**  

✔ **Running a log collector like Fluentd or Logstash**  

✔ **Managing networking with Calico or Cilium**  

✔ **Node monitoring with Prometheus Node Exporter**  

📌 **Kubernetes simplifies application deployment and scaling through workloads like Deployments, StatefulSets, and DaemonSets.** 🚀

  ---

# ❓ Questions & Troubleshooting


### 🔄 **kubectl apply vs kubectl create**?

- `kubectl create` **throws an error if the resource already exists**.

- `kubectl apply` **creates or updates** resources to match the given configuration.

### 🛠️ How Can I Debug Why My Single-Job Pod Ends with Status = "Error"?  



```sh
kubectl describe pod example
```

will give you more info on what's going on.

  

```sh
kubectl get events
```

can get you more details too although not dedicated to the given pod.

## 🔍 What is the Difference Between a Pod and a Deployment?  

Kubernetes has **three key object types** you should know about:  

- **Pods** 🏗️ – Runs one or more closely related containers.  

- **Services** 🌐 – Sets up networking in a Kubernetes cluster.  

- **Deployments** 🚀 – Maintains a set of identical pods, ensuring that they have the correct configuration and that the right number of them exist.  

### 📦 Pods  

- Runs a **single set of containers**.  

- Good for **one-off development** purposes.  

- **Rarely used directly in production**.  


### ⚙️ Deployment  

- Runs a **set of identical pods**.  

- **Monitors the state of each pod**, updating as necessary.  

- Suitable for **both development and production** environments.  

> 💡 **Tip:** Forget about managing Pods manually—use **Deployments** instead. Deployments handle **scaling, rolling updates, and recovery**, making them the **recommended approach** for most applications.  

<div style="text-align: center; width: 600px; margin: auto;">

    <img src="https://imgur.com/iX5mB14.png"
         style="border: 2px solid lightgray; max-width: 100%; padding: 1rem; height: auto; display: block;"
        alt="Get Pods">

<div style="color: gray; font-size: small; font-style: italic;">Get Pods</div>

</div>

Since **Pods** can be **killed, scaled, and replaced dynamically**, using a **Service** ensures they **always have a stable IP** and communication method.  

### 🏗️ Practical Kubernetes Deployment Setup  

In a typical application setup, you will use:  

1️⃣ **Deployment object** – Defines the containers and configuration for your application.   

2️⃣ **Service object** – Provides a **stable network endpoint (Cluster IP)** for the deployed pods.  

Since **Pods are ephemeral**, a **Service** ensures that external applications can always communicate with the running application, even when pods are replaced.  

## ⚙️ How to Configure a Kubernetes Multi-Pod Deployment  

You should create a **Deployment** for each component or Pod. Each Deployment will create a **ReplicaSet** that schedules and supervises the collection of Pods for the Deployment.  

Each Deployment will most likely also require a **Service** in front of it for access. It is common to create a **single YAML file** that contains both the Deployment and the corresponding Service.
  

## ❌ What Are the Disadvantages of Putting Multiple Containers in a Pod?  


If you have multiple containers inside a **POD**, you should consider the following challenges:  
  

#### 🔄 1️⃣ Lifecycle Issues  

- **Startup and termination order**: Which container should start first? Which one should terminate first?  

- **Failure handling**: If one container fails, is the whole Pod still operational?  

#### 🔍 2️⃣ Evaluating the Pod’s Operability  

- If there is **a single container**, operability is clear: **if the container runs, the Pod is fine**.  

- If there are **multiple containers**, defining **probes (readiness, liveness)** becomes more complex.  

- **What happens if one container dies?** Should the Pod restart, or can it continue running?  

#### 📌 3️⃣ Scheduling Complexity in the Kubernetes Cluster  


- It is **easier to find a node for a small Pod** (with a single container) than for a large one (with multiple containers consuming more resources).  

#### 📈 4️⃣ Reduced Scalability Flexibility  

- If **container A and B** are in the same Pod, **you cannot scale only one of them**.  

- Kubernetes scales the **Pod as a unit**, limiting resource optimization.    

#### 🚀 5️⃣ Deployment and Version Management Limitations  

- **Less flexibility** for **rollouts, canary releases, and rollbacks**.  

- If a Pod contains multiple containers, **all must be updated together**.  

#### 📊 6️⃣ Log and Metrics Collection Complexity  

- A mechanism is required to **centralize logs and metrics** from all containers within the Pod.  

- Depending on the technology stack, this can be **easy or tedious**.  

- With multiple containers, the solution **becomes even more complicated**.  

#### 🔧 7️⃣ Less Convenient `kubectl` Operations  

- You always need to use the `-c` flag to specify the container inside the Pod:  

  `kubectl logs -c container-name pod-name`

   `kubectl exec -it pod-name -c container-name -- /bin/sh`


## 🏗️ Multiple Pods per Node vs. One Pod per Node  

### **📊 Considerations for Multiple Pods per Node**  

- **More efficient use of resources.**  

- **Better cluster scalability and management.**  

- **Recommended for general workloads in Kubernetes.**  

### **🖥️ When to Use One Pod per Node?**  

- **High-performance workloads** (e.g., Machine Learning, Big Data, GPU tasks).  

- **Applications requiring dedicated resources.**  

- **Workloads with strict performance constraints.**  

> 🚀 **Managed Kubernetes services automatically schedule pods efficiently based on resources.**    

## 🌍 Why Would You Need More Than Two Nodes?  

The required **number of nodes** depends on the **workload and high-availability needs**.  

🔹 **Common Reasons for More Than Two Nodes:**  

- **Active-Standby Configuration** – Ensures pods are moved to another node if one fails.  

- **Stateful Applications & Databases** – Some services require **three replicas** for data consistency.  

- **ETCD Clusters** – **Minimum of three replicas** needed for proper reconciliation in case of data conflicts.  

  

  

  

## 🔑 How to SSH to the Docker-Desktop Node?  

  

  

To SSH into a **Docker Desktop Kubernetes node**, run:  

  

`docker run -it --rm --privileged --pid=host justincormack/nsenter1`

  

Just a quick tip for anyone trying to find files / folders mounted to the pods, the equivalent of / on the node can be found in /containers/services/docker/rootfs/