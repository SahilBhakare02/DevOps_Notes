# Docker

# 1. Introduction to Containerization and Docker Basics

Before understanding Docker, first understand why we need containerization.

---

# 2. Monolithic vs Microservices Architecture

## Monolithic Architecture

Monolithic architecture is a single, unified application where all components are tightly coupled.

- All components are part of one application.
- Difficult to scale individual components.
- Deployment and updates require redeploying the entire application.

### Example

A traditional web application where:

```text
Frontend
   +
Backend
   +
Database
   |
Single Application
```

Frontend, backend, and database are all part of the same codebase.

---

## Microservices Architecture

In Microservices Architecture, the application is broken down into smaller, independent services.

- Each service can be developed independently.
- Each service can be deployed independently.
- Each service can be scaled independently.
- Better fault isolation.
- Easier technology upgrades.

### Example

Consider an e-commerce application.

```text
E-Commerce Application
        |
        |----------------------
        |          |          |
      User      Product     Order
     Service    Service    Service
```

Instead of keeping everything in one application, we can have separate services for:

- User Authentication
- Product Catalog
- Order Management

---

# 3. Traditional vs Virtualization vs Containerization

| Deployment Type | Description |
|---|---|
| Traditional | Directly installs applications on physical servers, leading to inefficient resource utilization. |
| Virtualization | Uses a Hypervisor to create multiple Virtual Machines on a single physical server. Each VM has its own OS. |
| Containerization | Packages applications and dependencies together. Containers share the Host OS, making them lightweight and efficient. |

---

# 4. Introduction to Containerization

Containerization is a method of packaging applications and their dependencies together in isolated environments known as **Containers**.

It ensures that applications run consistently across different computing environments.

## Key Concepts

### Container

A lightweight, standalone executable package that includes everything needed to run an application.

### Image

A template used to create containers.

It includes:

- Application Code
- Dependencies
- Runtime

---

# 5. Why Containers Came into Picture?

Suppose we have an EC2 instance.

The EC2 instance may waste a lot of resources.

```text
EC2 Instance
--------------------------------
CPU       : Not completely used
Memory    : Not completely used
Storage   : Not completely used
--------------------------------
```

If in an organization millions of instances waste their resources, then it is a heavy waste of resources.

To solve this problem, containers take place.

Containers effectively use VM resources.

```text
Physical Server
       |
       v
Virtual Machine
       |
       v
--------------------------------
| Container | Container | Container |
--------------------------------
```

---

# 6. Container States

Containers mainly have 3 states:

```text
Start
  |
  v
Running
  |
  v
Exited / Stopped
```

---

# 7. What is a Container?

A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another.

A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application:

- Code
- Runtime
- System Tools
- System Libraries
- Settings

## In Simple Way

A container is a bundle of:

```text
Application
    +
Application Libraries
    +
Application Dependencies
    +
Minimum System Dependencies
```

---

# 8. Container vs Virtual Machine

Containers and VMs are both technologies used to isolate applications and their dependencies, but they have some key differences.

| Feature | Container | Virtual Machine |
|---|---|---|
| OS | Does not have complete OS | Has complete OS |
| Kernel | Shares Host OS Kernel | Has its own OS |
| Resource Usage | Lightweight | More resource-intensive |
| Speed | Faster | Comparatively slower |
| Isolation | Logical isolation | Complete isolation |
| Portability | More portable | Less portable |
| Management | Easier | Comparatively heavier |

---

## 1. Resource Utilization

Containers share the Host Operating System Kernel.

That's why containers are lighter and faster than VMs.

VMs have:

```text
Application
     |
Guest OS
     |
Hypervisor
     |
Host
```

Containers work like:

```text
Application
     |
Container
     |
Host OS Kernel
     |
Host
```

---

## 2. Portability

Containers are designed to be portable.

They can run on any system with a compatible Host Operating System.

VMs are less portable because they need a compatible Hypervisor.

---

## 3. Security

VMs provide a higher level of isolation because each VM has its own Operating System.

Containers provide less isolation compared to VM because they share the Host Operating System Kernel.

```text
VM        -> Complete Isolation

Container -> Logical Isolation
```

VM solved some problems with Physical Servers.

Containers solved some problems with VMs.

---

# 9. Why are Containers Lightweight?

Containers are lightweight because they use containerization technology.

They share the:

```text
Host OS Kernel
```

while still providing isolation for the application and its dependencies.

Containers do not need to include a complete Operating System.

Docker containers are designed to be minimal.

They only include what is necessary for the application to run.

## In Simple Way

Docker containers are lightweight because they do not have a complete OS.

They use resources from the:

```text
VM / Physical Server / Host OS
```

on which they are running.

Containers have:

```text
Minimal OS / Base Image
```

Container is a package or bundle which is a combination of:

```text
Application
     +
Application Libraries
     +
Application Dependencies
     +
System Dependencies
```

---

# 10. Files and Folders in Container Base Images

## `/bin`

Contains binary executable files.

Example:

```text
ls
cp
ps
```

---

## `/sbin`

Contains system binary executable files.

Example:

```text
init
shutdown
```

---

## `/etc`

Contains configuration files for various system services.

---

## `/lib`

Contains library files that are used by binary executables.

---

## `/usr`

Contains user-related files and utilities such as:

- Applications
- Libraries
- Documentation

---

## `/var`

Contains variable data such as:

- Log files
- Spool files
- Temporary files

---

## `/root`

Home directory of the `root` user.

---

# 11. What Containers Use from Host OS

Containers use some resources from the Host OS.

## Host File System

Docker containers can access the Host File System using **Bind Mounts**.

Bind Mounts allow containers to read and write files in the Host File System.

---

## Networking Stack

The Host Networking Stack is used to provide network connectivity to containers.

Containers can connect:

```text
Directly to Host Network
```

or through:

```text
Virtual Network
```

---

## System Calls

The Host Kernel handles system calls from containers.

This is how containers access resources such as:

- CPU
- Memory
- I/O

---

## Namespaces

Docker containers use Linux Namespaces to create isolated environments.

Namespaces provide isolation for:

- File System
- Process ID
- Network

---

## Control Groups - cgroups

Docker uses **cgroups** to limit and control resources available to containers.

Examples:

- CPU
- Memory
- I/O

---

## Important Point

Even though a container uses resources from the Host OS, it is still isolated from the Host and other containers.

Changes inside one container normally do not affect another container.

---

# 12. Why Container Images are Smaller than VM Images?

Container Base Images are normally smaller compared to VM Images.

This is because containers are designed to be minimal.

They contain only the necessary components required to run a specific application or service.

VMs emulate an entire Operating System including:

- Libraries
- Utilities
- System Files
- OS Components

Therefore:

```text
Container Image
      |
      | Minimal Components
      v
    Smaller

VM Image
      |
      | Complete OS
      v
    Larger
```

---

# 13. Docker

## Why Docker is Popular?

Docker is a containerization platform.

Docker helped the community to easily write, build, share, and run Docker Images.

---

# 14. What is Docker?

Docker is a containerization platform that provides an easy way to containerize applications.

Using Docker, you can:

```text
Build Container Images
        |
        v
Run Images to Create Containers
        |
        v
Push Images to Container Registries
```

Container registries can be:

- Docker Hub
- Quay.io
- Other Public/Private Registries

## Important Point

```text
Containerization = Concept / Technology

Docker = Implements Containerization
```

---

# 15. Why Use Docker?

Docker:

- Ensures consistent environments across Development, Testing, and Production.
- Reduces infrastructure overhead.
- Reduces resource consumption.
- Improves application scalability.
- Improves application portability.

---

# 16. Docker CE vs Docker EE

| Feature | Docker CE - Community Edition | Docker EE - Enterprise Edition |
|---|---|---|
| License | Open-source and Free | Paid with Enterprise Support |
| Security | Basic Security Features | Advanced Security Features |
| Support | Community Support | Professional Support |
| Management | Basic Container Management | Advanced Container Management |

---

# 17. Docker Lifecycle

The basic Docker lifecycle is:

```text
Dockerfile
    |
    | docker build
    v
Docker Image
    |
    | docker run
    v
Docker Container
```

In simple way:

```text
Dockerfile -> Image -> Container
```

Where:

```text
Dockerfile -> Build -> Image

Image -> Run -> Container
```

---

# 18. How Docker Lifecycle Works

1st of all, you as a user have to write a **Dockerfile**.

Dockerfile is basically a set of instructions.

For example, you tell Docker:

```text
Get Ubuntu Base Image
        |
        v
Copy My Source Code
        |
        v
Install Dependencies
        |
        v
Run Application
```

If it is a Node.js application:

```bash
npm install
```

If it is a Python application:

```bash
pip install
```

These commands install required application libraries and dependencies inside the Docker Image.

Once Dockerfile is ready, we submit it to Docker Daemon using:

```bash
docker build
```

Docker Daemon creates a Docker Image.

Once the Docker Image is created, execute it using:

```bash
docker run
```

`docker run` creates a Container.

The container contains:

```text
Application
+
Application Libraries
+
Application Dependencies
+
System Dependencies
```

Once the Docker Image is ready, we can share it with others using a Docker Registry.

---

# 19. Docker Architecture

Docker Architecture mainly contains:

```text
Docker Client
      |
      v
Docker Host
      |
      v
Docker Daemon
      |
      v
Docker Objects
      |
      v
Docker Registry
```

Main components:

- Docker Client
- Docker Host
- Docker Daemon
- Docker Registry

---

# 20. Docker Daemon

Docker Daemon is the **heart of Docker**.

Docker Daemon listens for Docker API requests and manages Docker Objects such as:

- Images
- Containers
- Networks
- Volumes

A daemon can also communicate with other daemons to manage Docker Services.

If Docker Daemon stops working, Docker cannot perform its normal operations.

---

# 21. Docker Client

Docker Client is the primary way users interact with Docker.

As a user, you use Docker CLI to execute commands.

Example:

```bash
docker run
```

The Docker Client sends this command to `dockerd`.

Docker Daemon receives the command and performs the required operation.

---

## docker build

If you execute:

```bash
docker build
```

Docker Daemon builds a Docker Image for you.

---

## docker run

If you execute:

```bash
docker run
```

Docker Daemon creates and runs a Container for you.

---

## docker pull

If you execute:

```bash
docker pull
```

Docker Daemon pulls the required Image from the configured Registry.

---

## Three Important Commands

```text
docker build -> Build Docker Image from Dockerfile

docker run   -> Run Container from Docker Image

docker push  -> Push Docker Image to Registry
```

---

# 22. Docker Desktop

Docker Desktop is an easy-to-install application for:

- Windows
- macOS
- Linux

It enables you to build and share containerized applications and microservices.

Docker Desktop includes:

- Docker Daemon
- Docker Client
- Docker Compose
- Docker Content Trust
- Kubernetes
- Credentials Helper

---

# 23. Docker Registry

Docker Registry stores Docker Images.

Example:

```text
Docker Hub
```

Docker Hub is a public registry that anyone can use.

You can also run your own private registry.

When you execute:

```bash
docker pull
```

or:

```bash
docker run
```

Required images can be pulled from the configured registry.

When you execute:

```bash
docker push
```

Your image is pushed to the configured registry.

---

# 24. Docker Objects

When using Docker, we create and use different Docker Objects.

Examples:

- Images
- Containers
- Networks
- Volumes
- Plugins

---

# 25. GitHub vs Docker Hub

| GitHub | Docker Hub |
|---|---|
| Stores Source Code | Stores Docker Images |

In simple way:

```text
GitHub     -> Source Code

Docker Hub -> Docker Images
```

---

# 26. Basic Docker Commands

## Install Docker

```bash
sudo apt install docker.io -y
```

---

## Create a Container

```bash
docker create --name my_container ubuntu
```

---

## Run a Container

```bash
docker run -it ubuntu
```

---

## Run Container in Detached Mode

```bash
docker run -d --name <container-name> <image-name>
```

`-d` means **Detached Mode**.

---

## Stop a Running Container

```bash
docker stop <container-name>
```

---

## Start a Stopped Container

```bash
docker start <container-name>
```

---

## Remove a Container

```bash
docker rm <container-name>
```

---

## List Running Containers

```bash
docker ps
```

---

## List All Containers

Running + Stopped:

```bash
docker ps -a
```

---

# 27. Docker Port Mapping

Run a container and expose a port:

```bash
docker run -d -p 8080:80 nginx
```

It means:

```text
Host Port        Container Port

   8080     ->       80
```

Port `8080` on the Host is mapped to port `80` inside the Container.

Another example:

```bash
docker run -d -p 80:80 --name <container-name> <image-name>
```

Here:

```text
-d = Detached Mode

-p = Publish / Port Mapping
```

---

# 28. Run Container with Environment Variables

```bash
docker run -d -e "ENV_VAR=value" my_app
```

`-e` is used to provide Environment Variables to the container.

---

# 29. Expose Random Ports

```bash
docker run -d -P nginx
```

`-P` automatically assigns available Host Ports to the exposed Container Ports.

---

# 30. Execute Command Inside Running Container

```bash
docker exec -it my_container bash
```

It attaches an interactive terminal to the running container.

---

# 31. Copy Files from Host to Container

```bash
docker cp my_file.txt my_container:/tmp/
```

It copies the file from Host into Container.

---

# 32. Copy Files from Container to Host

```bash
docker cp my_container:/tmp/my_file.txt ./
```

It retrieves the file from Container to Host.

---

# 33. Inspect Container

```bash
docker inspect my_container
```

It gives detailed information about the container.

---

# 34. Docker Logs

```bash
docker logs my_container
```

Used to check Container Logs.

---

# 35. Docker Stats

```bash
docker stats
```

Used to check resource utilization of running containers.

It shows information like:

- CPU
- Memory
- Network Usage

---

# 36. Build Docker Image

```bash
docker build . -t <image-name>
```

or:

```bash
docker build -t <image-name> .
```

This command builds a Docker Image using the Dockerfile in the current directory.

---

# 37. Remove All Containers

```bash
docker rm -f $(docker ps -aq)
```

Here:

```text
-a = All Containers
-q = Only Container IDs
-f = Force
```

---

# 38. Remove All Docker Images

```bash
docker rmi -f $(docker images -aq)
```

---

# 39. Docker Tag

```bash
docker tag <image-name> <username>/<new-name>
```

Used to give another name/tag to an existing image.

---

# 40. Docker Login

```bash
docker login -u <username>
```

Used to login to Docker Hub.

---

# 41. Docker Push

```bash
docker push <username>/<image-name>:<tag>
```

Used to push Docker Image to Registry.

---

# 42. Docker Save

```bash
docker save
```

Used to archive a Docker Image.

---

# 43. Docker Load

```bash
docker load -i <archive-file>
```

Used to load an archived Docker Image.

---

# 44. Docker Commit

```bash
docker commit <container-id> <new-image-name>
```

Used to create an Image from a Container.

---

# 45. Docker Image

Docker Images are lightweight, standalone, executable software packages.

An Image contains everything needed to run an application:

- Code
- Runtime
- Libraries
- Environment Variables
- Dependencies

---

# 46. Docker Image Naming Convention

Docker Image name follows this pattern:

```text
<repository>/<image-name>:<tag>
```

Example:

```text
iamsahil21/new:latest
```

Where:

```text
Repository -> iamsahil21

Image Name -> new

Tag        -> latest
```

Tag is used to identify different versions.

Example:

```bash
docker pull ubuntu:20.04
```

Here:

```text
Image = ubuntu
Tag   = 20.04
```

---

# 47. Docker Hub

Docker Hub is a cloud-based Registry Service used to store and distribute Container Images.

It provides:

- Public Repositories
- Private Repositories
- Pre-built Images
- User Authentication

Official Images are available for applications like:

- Nginx
- MySQL
- Ubuntu

---

# 48. Amazon ECR

**ECR = Elastic Container Registry**

Amazon ECR is a managed Container Image Registry Service provided by AWS.

Features:

- Integration with AWS Services
- Works with ECS
- Works with EKS
- Uses AWS IAM for Access Control
- Provides Private Registry for Images

---

# 49. Important Docker Image Commands

## Pull Image

```bash
docker pull <image-name>:<tag>
```

Example:

```bash
docker pull nginx:latest
```

---

## Login to Docker Hub

```bash
docker login -u <username>
```

---

## Push Image

```bash
docker push <repository>/<image-name>:<tag>
```

Example:

```bash
docker push myrepo/myapp:v1
```

---

## Commit Container as Image

```bash
docker commit <container-id> <new-image-name>
```

Example:

```bash
docker commit abc123 my-custom-image:v1
```

---

## Tag Image

```bash
docker tag <image-id> <repository>/<new-image-name>:<tag>
```

Example:

```bash
docker tag my-app:latest myrepo/my-app:v2
```

---

## Remove Image

```bash
docker rmi <image-id>
```

Example:

```bash
docker rmi nginx:latest
```

---

## Delete All Images

```bash
docker rmi -f $(docker images -aq)
```

---

# 50. Docker Fundamentals Summary

```text
Containerization
       |
       v
     Docker
       |
       v
   Dockerfile
       |
   docker build
       |
       v
 Docker Image
       |
   docker run
       |
       v
Docker Container
       |
       v
Application Running
```

## Important Points

- Containerization is a concept/technology.
- Docker implements containerization.
- Containers are lightweight compared to VMs.
- Containers share the Host OS Kernel.
- Dockerfile contains instructions to build an Image.
- Docker Image is used to create Containers.
- `docker build` builds an Image.
- `docker run` creates/runs a Container.
- Docker Daemon manages Docker Objects.
- Docker Hub stores Docker Images.
- GitHub mainly stores Source Code.
- Docker Containers help us use infrastructure resources more efficiently.

---

# 51. Docker Network

Docker Networking allows containers to communicate with:

- Other containers
- External services
- Host system

It provides flexibility in how containers interact with each other and the outside world.

## Simple Flow

```text
Container A
     |
     | Docker Network
     |
Container B
```

Docker Network is required when containers need to communicate with each other.

---

# 52. Different Docker Network Drivers

Docker provides different Network Drivers.

1. Bridge Network
2. Host Network
3. None Network
4. Overlay Network
5. Macvlan Network
6. IPvlan Network

---

## 52.1 Bridge Network

Bridge is the **default Docker Network**.

It is used when a container is started without specifying a Network.

Containers can communicate with each other using container names.

Suitable for standalone applications.

```text
Docker Host
|
|--- Bridge Network
      |
      |--- Container 1
      |
      |--- Container 2
```

---

## 52.2 Host Network

Host Network removes Network Isolation between the Container and Host.

The Container shares the Host's Networking Stack.

```text
Host Network
     |
     |------ Container
```

Best for standalone applications.

---

## 52.3 None Network

In None Network, the Container has no Network Interface.

```text
Container
    X
 No Network
```

Useful for security-sensitive applications that do not require Network Access.

---

## 52.4 Overlay Network

Overlay Network is used in **Docker Swarm Mode** for multi-host communication.

It connects containers across multiple Docker Daemon instances.

```text
Docker Host 1                 Docker Host 2
     |                             |
 Container A                   Container B
     |                             |
     -------- Overlay Network ------
```

---

## 52.5 Macvlan Network

Macvlan assigns a MAC Address to a Container.

This makes the Container appear as a physical device on the Network.

Suitable for legacy applications requiring direct Network Access.

---

## 52.6 IPvlan Network

IPvlan is similar to Macvlan but provides more flexibility in IP Management.

It offers better control over IP Address Assignment.

---

# 53. Docker Network Commands

## Create a Network

```bash
docker network create <network-name>
```

---

## List Networks

```bash
docker network ls
```

---

## Inspect a Network

```bash
docker inspect <network-name>
```

---

## Remove a Network

```bash
docker network rm <network-name>
```

---

## Run Container with Custom Network

```bash
docker run -d --name my_container --network my_custom_network nginx
```

---

## Connect Existing Container to Network

```bash
docker network connect my_custom_network my_container
```

---

## Disconnect Container from Network

```bash
docker network disconnect my_custom_network my_container
```

---

## Run Multiple Containers in Custom Network

Container 1:

```bash
sudo docker run --network my_custom_network --name container1 -d nginx
```

Container 2:

```bash
sudo docker run --network my_custom_network --name container2 -d nginx
```

Both containers are now using the same Custom Network.

```text
my_custom_network
       |
       |---- container1
       |
       |---- container2
```

---

## Create Bridge Network with Custom Subnet

```bash
docker network create --subnet "192.168.0.0/16" --driver bridge newnetwork
```

---

## Run Container using Host Network

```bash
docker run -d -P --network host nginx:latest
```

---

## Run Container using Custom Network with Port Mapping

```bash
docker run -d -p 80:80 --network=mynet imagename
```

---

# 54. Docker Volume

**Volume = Persistent Storage**

Docker Volumes are used for persisting data in Docker Containers.

Normally, when Container data is stored only inside the Container, we may lose that data when the Container is removed.

Docker Volume solves this problem.

```text
Container
    |
    | Data
    v
Docker Volume
    |
    v
Persistent Storage
```

Unlike Bind Mounts, Volumes are managed by Docker.

Docker normally stores managed Volume data under:

```text
/var/lib/docker/volumes/
```

Volumes are the preferred way to handle data persistence in Docker because they are easier to manage and work across different environments.

---

# 55. Why Use Docker Volumes?

## Persistence

Data remains even after the Container is removed.

```text
Container Deleted
       |
       X

Volume
  |
  v
Data Still Available
```

---

## Ease of Management

Docker manages Volumes separately from Containers.

---

## Performance

Volumes can provide efficient storage for Container data.

---

## Backup & Restore

Volumes make it easier to move and restore application data between different environments.

---

## Container Independence

Volumes can be shared across multiple Containers.

Example:

```text
Container 1
     |
     |
Shared Volume
     |
     |
Container 2
```

---

# 56. Docker Volume Commands

## Create Docker Volume

```bash
docker volume create <myvol>
```

---

## Attach Volume to Container

```bash
docker run -d -p <port> -v <volname>:/media --name <container> <imagename>
```

---

## List All Volumes

```bash
docker volume ls
```

This displays all available Docker Volumes.

---

## Inspect a Volume

```bash
docker volume inspect my_volume
```

This gives detailed information about the Volume, including its Mount Path.

---

## Remove a Volume

```bash
docker volume rm my_volume
```

This deletes the specified Volume.

Ensure that the Volume is not being used by any Container.

---

## Remove All Unused Volumes

```bash
docker volume prune
```

This removes unused Volumes to free up space.

---

# 57. Create Volume and Attach it to Container

```bash
docker run -d --name my_container -v my_volume:/data nginx
```

This command:

1. Starts a Container named `my_container`.
2. Attaches `my_volume`.
3. Mounts the Volume at `/data` inside the Container.
4. Runs Nginx.

Flow:

```text
my_container
     |
   /data
     |
     v
my_volume
```

---

# 58. Share Volume Between Multiple Containers

Create Container 1:

```bash
docker run -d --name container1 -v shared_volume:/data nginx
```

Create Container 2 and use Volumes from Container 1:

```bash
docker run -d --name container2 --volumes-from container1 nginx
```

Both Containers share the same Volume for data persistence.

```text
Container 1
     |
     |
shared_volume
     |
     |
Container 2
```

---

# 59. Docker Volume Types

Main storage types in Docker:

1. Docker Volume
   - Named Volume
   - Anonymous Volume
2. Bind Mount
3. tmpfs Mount

---

# 60. Docker Volume

A Docker Volume is storage managed completely by Docker.

Docker creates the storage location and manages it.

There are two common types of Docker Volumes:

```text
Docker Volume
     |
     |----------------
     |               |
Named Volume    Anonymous Volume
```

---

# 61. Named Volume

In Named Volume, the user provides the Volume Name.

Example:

```text
Docker
   |
 my-sql
   |
/var/lib/docker/volumes/my-sql/
```

Data is stored under:

```text
/var/lib/docker/volumes/
```

Example command:

```bash
docker volume create my-sql
```

Then attach it:

```bash
docker run -d -v my-sql:/data nginx
```

Here:

```text
my-sql = Volume Name

/data = Container Directory
```

---

# 62. Anonymous Volume

In Anonymous Volume, Docker creates the Volume automatically.

You don't give it a name.

Example:

```text
Docker
   |
a61e8c5d7b2c
   |
/var/lib/docker/volumes/a61e8c5d7b2c/
```

Docker automatically generates the Volume Name/ID.

---

# 63. Bind Mount

A Bind Mount is not managed by Docker in the same way as a Docker-managed Volume.

Docker simply connects a folder on your Host Machine to a folder inside the Container.

You control where the data lives.

```text
Host Machine
/home/user/project
       |
       |
       v
Container
/app
```

Bind Mount is best used for **Development**.

---

# 64. tmpfs Mount

`tmpfs` stores data only in **RAM**.

Nothing is stored permanently on the Hard Disk.

```text
Container
    |
    v
   RAM
    |
Container Stops
    |
Data is not persistent
```

---

# 65. Docker Storage Types Summary

| Type | Storage Managed By | Data Location | Best Use |
|---|---|---|---|
| Named Volume | Docker | Docker-managed location | Persistent application data |
| Anonymous Volume | Docker | Docker-managed location | Temporary Docker-managed Volume |
| Bind Mount | User / Host | User-selected Host Directory | Development |
| tmpfs | RAM | Memory | Temporary data |

---

# 66. Dockerfile

Dockerfile is a file where you provide the steps to build your Docker Image.

Dockerfile is a script that contains a set of instructions to automate the process of building Docker Images.

It allows developers to create customized Container Images with pre-installed:

- Applications
- Libraries
- Dependencies
- Configuration

## Flow

```text
Dockerfile
    |
    | docker build
    v
Docker Image
    |
    | docker run
    v
Container
```

---

# 67. Key Dockerfile Instructions

Important Dockerfile instructions:

1. `FROM`
2. `LABEL`
3. `RUN`
4. `CMD`
5. `ENTRYPOINT`
6. `ENV`
7. `ARG`
8. `COPY`
9. `ADD`
10. `EXPOSE`
11. `USER`
12. `WORKDIR`
13. `HEALTHCHECK`
14. `MAINTAINER`
15. `ONBUILD`
16. `SHELL`
17. `STOPSIGNAL`
18. `VOLUME`

---

# 68. FROM - Base Image

`FROM` specifies the Base Image for the Container.

Example:

```dockerfile
FROM ubuntu:latest
```

In simple way:

```text
FROM = From which Base Image should I build my Image?
```

---

# 69. LABEL - Metadata

`LABEL` adds Metadata like Author or Description.

Example:

```dockerfile
LABEL maintainer="Your Name <your.email@example.com>"
```

---

# 70. RUN - Execute Commands

`RUN` executes Shell Commands during Image Build.

Example:

```dockerfile
RUN apt update && apt install -y nginx
```

It can be used to install required packages inside the Image.

---

# 71. CMD - Default Command

`CMD` defines the default command to run inside the Container.

Example:

```dockerfile
CMD ["nginx", "-g", "daemon off;"]
```

---

# 72. ENTRYPOINT - Command with Arguments

`ENTRYPOINT` defines a fixed command.

Example:

```dockerfile
ENTRYPOINT ["nginx"]
```

It can be used with:

```dockerfile
CMD ["-g", "daemon off;"]
```

---

# 73. ENV - Environment Variables

`ENV` defines Environment Variables.

Example:

```dockerfile
ENV APP_ENV=production
```

---

# 74. ARG - Build Arguments

`ARG` defines arguments used during the Build Process.

Example:

```dockerfile
ARG APP_VERSION=1.0
```

---

# 75. COPY - Copy Files

`COPY` copies files from the Build Context into the Image.

Example:

```dockerfile
COPY index.html /usr/share/nginx/html/
```

Flow:

```text
Host
index.html
    |
    | COPY
    v
Docker Image
/usr/share/nginx/html/
```

---

# 76. ADD - Copy and Extract Files

`ADD` is similar to `COPY`, but it also supports some additional features such as extracting local compressed archives.

Example:

```dockerfile
ADD archive.tar.gz /app/
```

---

# 77. EXPOSE - Expose Ports

`EXPOSE` informs Docker that the Containerized Application listens on the specified port.

Example:

```dockerfile
EXPOSE 80
```

---

# 78. USER - Specify User

`USER` sets the user for running commands inside the Container.

Example:

```dockerfile
USER nginx
```

---

# 79. WORKDIR - Working Directory

`WORKDIR` sets the Working Directory inside the Container.

Example:

```dockerfile
WORKDIR /app
```

After setting it:

```text
Working Directory = /app
```

---

# 80. HEALTHCHECK

`HEALTHCHECK` is used to check the Container's health.

It helps determine whether the application inside the Container is working properly.

---

# 81. MAINTAINER

`MAINTAINER` specifies the author of an Image.

---

# 82. ONBUILD

`ONBUILD` specifies instructions that will run when the Image is later used as a Base Image in another build.

---

# 83. SHELL

`SHELL` sets the default Shell of an Image.

---

# 84. STOPSIGNAL

`STOPSIGNAL` specifies the System Call Signal used for stopping the Container.

---

# 85. VOLUME

`VOLUME` creates a Volume Mount Point.

It is used when the application requires persistent or externally managed data.

---

# 86. Dockerfile Commands

## Build Docker Image

```bash
docker build -t my-image .
```

---

## Login to Docker Hub

```bash
docker login
```

---

## Tag Image

```bash
docker tag my-image username/my-image
```

---

## Push Image to Docker Hub

```bash
docker push username/my-image
```

---

## Pull Image

```bash
docker pull username/my-image
```

---

## Run Container from Image

```bash
docker run -d -p 80:80 my-image
```

---

# 87. Dockerfile Complete Flow

```text
Write Dockerfile
      |
      v
docker build -t my-image .
      |
      v
Docker Image
      |
      v
docker run -d -p 80:80 my-image
      |
      v
Docker Container
      |
      v
Application Running
```

---

# 88. Docker Compose

When we want to run **multiple Containers at a time**, that time we use Docker Compose.

We can up/down multiple Containers using Docker Compose.

Docker Compose allows us to define and run multi-container Docker Applications using a YAML file.

The file normally contains configuration for:

- Services
- Networks
- Volumes

Instead of creating every Container manually:

```text
Container 1 -> Manual Command
Container 2 -> Manual Command
Container 3 -> Manual Command
Container 4 -> Manual Command
```

We define everything in one:

```text
docker-compose.yml
```

Then manage them together.

---

# 89. Why Docker Compose?

Suppose our application contains:

```text
Frontend
   |
Backend
   |
Database
```

Without Docker Compose, we may need to start each Container separately.

With Docker Compose:

```text
docker-compose.yml
        |
        |-----------------------
        |          |           |
     Frontend   Backend     Database
```

We can manage the complete application stack using simple commands.

---

# 90. Docker Compose Commands

## Run / Create / Start Containers

```bash
docker compose up
```

---

## Stop and Remove Containers

```bash
docker compose down
```

---

## Build / Rebuild Images

```bash
docker compose build
```

---

## List Running Containers

```bash
docker compose ps
```

---

## Check Logs

```bash
docker compose logs
```

---

## Restart Services

```bash
docker compose restart
```

It restarts the Docker Compose services.

---

# 91. Key Features of Docker Compose

## 1. Single Configuration

Define all services in a single:

```text
docker-compose.yml
```

file.

---

## 2. Multi-Container Management

Docker Compose manages multiple Containers that form an application.

Example:

```text
Application
    |
    |---- Frontend Container
    |
    |---- Backend Container
    |
    |---- Database Container
```

---

## 3. Easy to Use

Simple commands can be used for deployment and teardown.

Start:

```bash
docker compose up
```

Stop and remove:

```bash
docker compose down
```

---

## 4. Scalable

Docker Compose allows individual services to be scaled when required.

---

# 92. Docker Compose Flow

```text
Application Source Code
        |
        v
Dockerfiles
        |
        v
docker-compose.yml
        |
        v
docker compose up
        |
        v
--------------------------------
| Frontend | Backend | Database |
--------------------------------
        |
        v
Application Running
```

---

# 93. Docker Part 2 Summary

## Docker Network

Docker Network allows Containers to communicate with:

```text
Containers
External Services
Host System
```

Main Network Drivers:

```text
Bridge
Host
None
Overlay
Macvlan
IPvlan
```

---

## Docker Volume

Docker Volume provides:

```text
Persistent Storage
```

Main Storage Types:

```text
Docker Volume
   |
   |--- Named Volume
   |
   |--- Anonymous Volume

Bind Mount

tmpfs Mount
```

---

## Dockerfile

Dockerfile contains instructions used to build a Docker Image.

```text
Dockerfile
    |
docker build
    |
    v
Image
    |
docker run
    |
    v
Container
```

---

## Docker Compose

Docker Compose is used when we want to manage multiple Containers together.

```text
docker-compose.yml
       |
       v
docker compose up
       |
       v
Multiple Containers
```

---

#Docker topics covered:

- Containerization
- Monolithic vs Microservices
- Container vs VM
- Docker Basics
- Docker Architecture
- Docker Lifecycle
- Docker Commands
- Docker Images
- Docker Hub
- Amazon ECR
- Docker Network
- Docker Volume
- Docker Volume Types
- Dockerfile
- Docker Compose

---
