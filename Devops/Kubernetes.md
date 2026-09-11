# Kubernetes

## 1. What is Kubernetes?

Kubernetes (K8s) is an open-source container orchestration platform developed by Google.

It is used to:

- Deploy containerized applications
- Manage containerized applications
- Scale applications
- Monitor containerized applications automatically

In simple way:

> Kubernetes is a manager that controls containers running on many servers.

### Simple Difference

```text
Docker
   |
   v
Creates and Runs Containers

Kubernetes
   |
   v
Manages Containers
```

Docker can run a container.

Kubernetes can:

- Run containers
- Monitor containers
- Restart containers
- Scale containers
- Update applications
- Manage containers
- Run containers across multiple servers

---

# 2. Why was Kubernetes Created?

Imagine you have only one Docker container.

Everything works perfectly.

Now imagine your company grows.

Instead of:

```text
1 Container
```

you have:

```text
100 Containers
       |
       v
20 Servers
```

Now many problems appear.

### Problems

1. Which server should run the container?
2. What if a container crashes?
3. What if one server fails?
4. What if there are too many users?
5. How do we update the application?
6. How do we monitor everything?

Google faced these problems while running millions of containers.

They built an internal system called **Borg**.

Kubernetes was later created based on ideas from Borg and released as open source.

---

# 3. Why do we use Kubernetes?

We use Kubernetes because it automatically manages containers.

Instead of doing everything manually, Kubernetes does it for you.

It can:

- Deploy applications
- Restart failed containers
- Scale applications up or down
- Distribute traffic
- Update applications without downtime
- Recover from failures
- Monitor container health

---

# 4. Real-Life Example

Imagine a restaurant.

Without a manager:

```text
2 Chefs
10 Waiters
500 Customers
```

Everyone works randomly.

No one knows:

- Who cooks?
- Who serves?
- Who cleans?

The restaurant becomes chaotic.

Now imagine there is a manager.

The manager decides:

- Chef 1 cooks.
- Chef 2 prepares desserts.
- Waiter 1 serves table 5.
- If the restaurant gets busy, hire more chefs.
- If an employee is sick, replace that employee.

Everything runs smoothly.

### Kubernetes is that manager.

```text
Kubernetes = Manager

Containers = Chefs / Workers
```

---

# 5. Kubernetes vs Docker

| Docker | Kubernetes |
|---|---|
| Creates containers | Manages containers |
| Runs one or few containers | Runs 1000s of containers |
| Works on one machine | Works across many machines |
| Manual scaling | Automatic scaling |
| Manual recovery | Automatic recovery |
| No built-in load balancing | Built-in load balancing |

## In Simple Way

```text
Docker
   |
   v
Create and Run Containers

Kubernetes
   |
   v
Manage Many Containers Automatically
```

---

# 6. Kubernetes Architecture

Kubernetes works on a **Cluster**.

## What is a Cluster?

A cluster is simply multiple computers working together.

Example:

```text
Cluster
   |
   |---- Server 1
   |
   |---- Server 2
   |
   |---- Server 3
```

All these servers work together as one Kubernetes system.

---

# 7. Kubernetes Architecture Components

Kubernetes is divided into 2 main parts:

```text
Kubernetes Cluster
       |
       |-------------------------
       |                        |
       v                        v
Control Plane              Worker Nodes
(Master Node)              (Worker Machines)
```

## 1. Control Plane

The Control Plane makes decisions and manages the cluster.

## 2. Worker Nodes

Worker Nodes run the applications.

---

# 8. Control Plane

The Control Plane is the **brain of Kubernetes**.

It receives user requests and decides:

- Where to run the application
- Which node should execute Pods
- Whether Pods are healthy
- When to create Pods
- When to delete Pods

---

# 9. Control Plane Components

Main Control Plane components:

1. API Server
2. ETCD
3. Scheduler
4. Controller Manager

```text
Control Plane
     |
     |-------------------------
     |          |       |      |
 API Server   ETCD  Scheduler Controller
                         Manager
```

---

# 10. API Server

The API Server is the **entry point of Kubernetes**.

Every request goes through the API Server.

It:

- Accepts requests
- Authenticates the user
- Authorizes the request
- Validates the request
- Stores data in ETCD
- Returns the response

### Example

```text
User
 |
 | kubectl command
 v
API Server
 |
 | Validate YAML
 v
ETCD
 |
 | Notify
 v
Scheduler / Controller Manager
```

Example:

```text
You execute command
       |
       v
API Server receives request
       |
       v
Validates YAML
       |
       v
Stores desired state into ETCD
       |
       v
Notifies Scheduler and Controller Manager
```

---

# 11. ETCD

ETCD stores key-value data.

It is the **Database of Kubernetes**.

It stores information such as:

- Pods
- Deployments
- Secrets
- Namespaces
- ConfigMaps
- Services
- Node information
- Cluster state

Basically, it stores the Kubernetes cluster state.

### Example

Suppose the desired state is:

```text
Application = nginx
Replicas    = 3
```

ETCD stores this information.

If one Pod dies, ETCD still says:

```text
Required Pods = 3
```

The Controller Manager notices the difference and creates another Pod.

### Important Point

ETCD never runs applications.

It only stores data.

---

# 12. Scheduler

Scheduler decides which Worker Node should run a Pod.

Example:

```text
Node 1 = 90% CPU

Node 2 = 10% CPU
```

Scheduler selects Node 2 because it has enough resources.

```text
Scheduler
    |
    | Check available resources
    v
Worker Node 2
    |
    v
Pod
```

---

# 13. Controller Manager

Controller Manager continuously checks:

```text
Desired State
      vs
Current State
```

### Example 1

Desired:

```text
5 Pods
```

Running:

```text
3 Pods
```

Controller Manager notices the difference and creates:

```text
2 More Pods
```

### Example 2

Desired:

```text
5 Pods
```

Running:

```text
7 Pods
```

Controller Manager removes:

```text
2 Pods
```

---

# 14. Worker Node

Worker Node actually runs the application.

Each Worker Node contains:

- Kubelet
- Kube-proxy
- Container Runtime
- Pods

```text
Worker Node
     |
     |------------------------
     |       |       |       |
 Kubelet Kube-proxy Runtime Pods
```

---

# 15. Kubelet

Kubelet is one of the most important components of the Worker Node.

It is an agent running on every Worker Node.

It communicates with the API Server.

It is responsible for:

- Accepting requests
- Running Pods
- Sending responses/status to API Server

### Example

```text
Control Plane
      |
      | Request
      v
Kubelet
      |
      v
Download Nginx Image
      |
      v
Start Container
      |
      v
Report Response
```

---

# 16. Kube-proxy

Kube-proxy is responsible for Networking.

It:

- Routes traffic
- Maintains network rules
- Load balances traffic
- Allows Pod communication
- Allows Service communication

---

# 17. Container Runtime

Container Runtime is responsible for:

- Pulling Images
- Creating Containers
- Starting Containers
- Stopping Containers
- Deleting Containers

```text
Container Runtime
       |
       |---- Pull Image
       |
       |---- Create Container
       |
       |---- Start Container
       |
       |---- Stop Container
       |
       |---- Delete Container
```

---

# 18. Pods

Pod is the **smallest unit of Kubernetes**.

A Pod contains:

- One Container

or

- Multiple Containers

```text
Pod
 |
 |---- Container
```

or:

```text
Pod
 |
 |---- Container 1
 |
 |---- Container 2
```

---

# 19. Kubernetes Architecture Flow

The basic flow of Pod creation is:

```text
User
 |
 v
API Server
 |
 v
ETCD
 |
 v
Scheduler
 |
 v
Worker Node
 |
 v
Kubelet
 |
 v
Container Runtime
 |
 v
Pod
```

---

# 20. How Kubernetes Works

## Step 1: User Sends a Request

User sends a request to Kubernetes.

Example:

```bash
kubectl apply -f deployment.yaml
```

---

## Step 2: API Server Receives the Request

API Server checks:

- Is the request valid?
- Is the user allowed?
- Is the YAML correct?

---

## Step 3: API Server Accepts the Request

If all queries are correct, API Server accepts the request.

---

## Step 4: ETCD Stores Desired State

ETCD stores the desired state.

Example:

```text
Application = nginx
Replicas    = 3
Status      = Desired
```

This is called the **Desired State**.

---

## Step 5: Controller Manager Checks

Controller Manager compares:

```text
Desired State
      vs
Current State
```

Example:

```text
Desired = 3 Pods
Running = 0 Pods
```

Controller Manager decides:

```text
Need 3 Pods
```

---

## Step 6: Scheduler Selects Worker Node

Scheduler selects a Worker Node.

Example:

```text
Node 1 = 90% CPU
Node 2 = 10% CPU
```

Scheduler chooses:

```text
Node 2
```

because it has enough resources.

---

## Step 7: Kubelet Receives Instruction

The selected Worker Node has Kubelet.

Kubelet receives:

```text
Run Nginx Pod
```

---

## Step 8: Container Runtime Starts Container

Container Runtime:

1. Downloads the Nginx Image if required.
2. Creates the Container.
3. Starts the Container.

---

## Step 9: Pod Becomes Running

Now the application is live.

```text
Pod
 |
 v
Running
 |
 v
Application Live
```

---

## Step 10: Kube-proxy Handles Networking

Suppose users access:

```text
www.company.com
```

Kube-proxy routes the request to one of the running Pods.

---

# 21. Kubernetes Working Flow

```text
User
 |
 v
API Server
 |
 v
ETCD
 |
 v
Controller Manager
 |
 v
Scheduler
 |
 v
Kubelet
 |
 v
Container Runtime
 |
 v
Pod
 |
 v
Kube-proxy
 |
 v
User Traffic
```

---

# 22. Real-Life Example - Online Shopping Website

Imagine an online shopping website.

During normal hours:

```text
Users = 100
Pods  = 2
```

During a festival sale:

```text
Users = 50,000
Pods  = 100
```

Kubernetes increases the number of Pods to handle the demand.

After the sale:

```text
Users = 100
Pods  = 2
```

Kubernetes reduces the number of Pods to save resources.

Without Kubernetes, an administrator would need to do all of this manually.

---

# 23. Advantages of Kubernetes

## High Availability

Applications remain available even if Pods or Nodes fail.

## Automatic Scaling

Kubernetes can increase or decrease Pods based on demand.

## Self-Healing

Kubernetes restarts or replaces failed Pods automatically.

## Load Balancing

Kubernetes distributes traffic among Pods.

## Rolling Updates

Deploy new application versions with little or no downtime.

## Rollbacks

Quickly return to a previous version if an update fails.

## Efficient Resource Usage

Kubernetes schedules workloads on suitable Nodes.

## Portable

Kubernetes can run on:

- Cloud Providers
- On-Premises Infrastructure

---

# 24. Amazon EKS

**EKS = Elastic Kubernetes Service**

Amazon EKS is used to run Kubernetes on AWS.

---

# 25. EKS - Create Kubernetes Cluster

## Step 1: Open AWS Console

Open AWS Console.

Search:

```text
EKS
```

---

## Step 2: Create Cluster

Click:

```text
Create Cluster
```

Select:

```text
Custom Configuration
```

---

## Step 3: Turn Off Auto Mode

Turn off:

```text
EKS Auto Mode
```

---

## Step 4: Give Cluster Name

Enter the required:

```text
Cluster Name
```

---

## Step 5: IAM Role

Select an existing IAM Role.

If there is no existing IAM Role, create a new IAM Role.

---

## Step 6: Kubernetes Version

Check the Kubernetes Version.

Keep the remaining settings as default.

Click:

```text
Next
```

---

## Step 7: VPC and Subnets

Ensure the correct:

- VPC
- Subnets

are selected.

Select all required Subnets.

---

## Step 8: Security Group

Select an Additional Security Group.

For this setup, select the Security Group where all traffic is allowed.

Click:

```text
Next
```

Keep the remaining configuration as default.

Continue:

```text
Next
Next
```

---

## Step 9: Review Configuration

Check all configuration.

Finally click:

```text
Create Cluster
```

The EKS Cluster will be created.

---

# 26. Create EC2 Instance for EKS Access

Create an EC2 instance as usual.

Use:

```text
Instance Type = c7i-flex.large
```

Create the instance.

---

# 27. Connect to EC2 Instance

Connect to the EC2 instance.

---

# 28. Install kubectl

Update packages:

```bash
apt update -y
```

Download the latest release:

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

---

## Download Checksum File

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
```

---

## Validate kubectl Binary

```bash
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
```

Expected result:

```text
kubectl: OK
```

---

## Install kubectl

```bash
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

---

## If Root Access is Not Available

You can install `kubectl` inside:

```text
~/.local/bin
```

Commands:

```bash
chmod +x kubectl
```

```bash
mkdir -p ~/.local/bin
```

```bash
mv ./kubectl ~/.local/bin/kubectl
```

---

## Check kubectl Version

```bash
kubectl version --client
```

---

# 29. Install AWS CLI on Ubuntu

Install AWS CLI:

```bash
snap install aws-cli --classic
```

---

# 30. Configure AWS CLI

To connect AWS using CLI, configure AWS User using:

```bash
aws configure
```

Enter:

```text
Access Key
Secret Key
```

---

# 31. Create Nodes in EKS Cluster

Go inside the EKS Cluster.

Click:

```text
Compute
```

Under:

```text
Node Groups
```

click:

```text
Add Node
```

---

## Configure Node Group

Give a name to the Node.

Select an IAM Role:

- Select existing IAM Role

or

- Create a new IAM Role

Keep all configuration as default.

Change the Instance Type from:

```text
t3.medium
```

to:

```text
c7i-flex.large
```

Click:

```text
Next
```

Keep the remaining configuration as default.

Finally:

```text
Node Created
```

---

# 32. EC2 Instances Created Automatically

In this setup:

```text
Desired Instance State = 2
```

Therefore:

```text
2 EC2 Instances
       |
       v
Created Automatically
```

These EC2 instances become Worker Nodes for the EKS Cluster.

---

# 33. Login into EKS Cluster

Use:

```bash
aws eks update-kubeconfig --name <clustername>
```

For a specific region:

```bash
aws eks update-kubeconfig --region ap-south-1 --name <cluster-name>
```

---

## Check Cluster Information

```bash
kubectl cluster-info
```

You can also use:

```bash
aws eks update-kubeconfig
```

---

# 34. Access EKS Cluster from Another EC2 Instance

Now use another EC2 instance to access the cluster.

We create another EC2 instance because:

```text
EKS Cluster
     |
     |
Another EC2 Instance
     |
     v
Access Cluster
```

This EC2 instance is used as an access machine.

---

# 35. Create a Pod

Create a Pod using Nginx Image:

```bash
kubectl run pod --image=nginx
```

---

# 36. List Pods

```bash
kubectl get pods
```

---

# 37. List Pods in Detail

```bash
kubectl get pods -o wide
```

This shows more information about Pods, including the Node where the Pod is running.

---

# 38. Edit a Pod

```bash
kubectl edit pod <pod-name>
```

This opens the Pod configuration for editing.

---

# 39. EKS Project Flow

```text
AWS Console
     |
     v
EKS
     |
     v
Create Cluster
     |
     v
Create Node Group
     |
     v
EC2 Worker Nodes
     |
     v
Configure kubectl
     |
     v
Configure AWS CLI
     |
     v
Update kubeconfig
     |
     v
Access EKS Cluster
     |
     v
Create Pod
     |
     v
kubectl get pods
```

---

# 40. Important Kubernetes Points

- Kubernetes is a container orchestration platform.
- Docker creates and runs containers.
- Kubernetes manages containers.
- Kubernetes works using a Cluster.
- A Cluster contains Control Plane and Worker Nodes.
- Control Plane is the brain of Kubernetes.
- API Server is the entry point.
- ETCD stores Kubernetes cluster data.
- Scheduler decides which Worker Node should run a Pod.
- Controller Manager checks Desired State vs Current State.
- Kubelet runs on every Worker Node.
- Kube-proxy handles Networking.
- Container Runtime handles Containers.
- Pod is the smallest unit of Kubernetes.
- EKS is Amazon's managed Kubernetes service.
- `kubectl` is used to interact with Kubernetes.
- AWS CLI is used to connect and work with AWS from the command line.
- `aws eks update-kubeconfig` is used to configure access to an EKS Cluster.

---

# 41. Kubernetes Part 3 Summary

```text
Kubernetes
    |
    v
Cluster
    |
    |-----------------------------
    |                            |
    v                            v
Control Plane              Worker Nodes
    |                            |
    |                            |---- Kubelet
    |                            |---- Kube-proxy
    |                            |---- Container Runtime
    |                            |---- Pods
    |
    |---- API Server
    |---- ETCD
    |---- Scheduler
    |---- Controller Manager
```

### Working Flow

```text
User
 |
 v
API Server
 |
 v
ETCD
 |
 v
Controller Manager
 |
 v
Scheduler
 |
 v
Kubelet
 |
 v
Container Runtime
 |
 v
Pod
```

### EKS Practical

```text
Create EKS Cluster
       |
       v
Create Node Group
       |
       v
EC2 Worker Nodes
       |
       v
Install kubectl
       |
       v
Install AWS CLI
       |
       v
aws eks update-kubeconfig
       |
       v
kubectl cluster-info
       |
       v
Create Pod
```

---

# Next Part

The next part of the Kubernetes documentation will continue with:

```text
Imperative Approach
        |
        v
Declarative Approach
        |
        v
YAML File
        |
        v
kubectl Commands
        |
        v
Kubernetes Services
        |
        |--- ClusterIP
        |--- NodePort
        |--- LoadBalancer
        |--- Headless
        |--- External IP
        |
        v
Replication Controller
        |
        v
ReplicaSet
```