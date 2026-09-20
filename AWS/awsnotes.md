# AWS Notes

## Why We Use AWS
Because it has more market shares
- It has 300+ services
- Its servers are present all over the world (globally)
- It offers pay as u use service

---

## Q1) What is Virtualization? (VMM = Virtual Machine Manager)

Virtualization is a technology used to create multiple virtual system/environment on single physical device/machine.

Virtualization is a technology that allows you to create virtual, simulated environments from a single, physical machine.

A virtual machine (VM) is a computing environment that functions as an isolated system with its own CPU, OS, memory, network interface, and storage, created from a pool of hardware resources.

Virtualization divides the resources of 1 physical machine so that multiple systems can run on it at the same time.

**Example:** Suppose u have powerful server, using virtualization you can run windows, Linux and Ubuntu server all on the same physical machine. Each behave like separate computer. A company can run 10 virtual server on 1 physical server instead of buying 10 machines.

### Virtualization Architecture

```
 VM1   VM2   VM3
------------------
    Hypervisor
------------------
 Operating System
------------------
    Hardware
```
*Fig: Architecture of Virtualization*

### Virtualization Working

Virtualization mainly works on 2 components: 1. Virtual Machines and 2. Hypervisors

**1. Virtual Machine:**
VM is a virtual computer created using software. It has CPU, MEMORY, STORAGE, OS, NETWORK. Even though it is virtual, it works just like a real computer.

**Security consideration:**
VM are isolated from each other, so if 1 VM has a problem, other VM works properly. However, if the hypervisor itself has a security issue, all VMs running on it could be affected.

### Types of Virtualization
1. **Server virtualization** – 1 physical server runs multiple virtual servers
2. **Desktop virtualization** – many users can access virtual desktops from 1 system
3. **Storage virtualization** – multiple storage devices are combined into 1 strong pool
4. **Application virtualization** – applications run in a virtual environment instead of directly on OS
5. **Network virtualization** – network resources like routers and switches are created virtually

### Virtualization vs Containers
- **Virtualization** – each VM has its own OS
- **Containerization** – applications share the same OS

**Example:** Docker (containers are lighter and faster than VMs)

---

## Q2) What is a Hypervisor?

A hypervisor is software that creates and manages VM by dividing the resources of a physical computer so multiple OS can run on a single machine.

A hypervisor is a software that you can use to run multiple virtual machines on a single physical machine.

### Types of Hypervisors

**1. Bare-Metal Hypervisor (Type 1 Hypervisor)**
- It runs directly on host's hardware to manage guest operating systems (used in industry)
- This type of hypervisor is most common in an enterprise datacenter or other server-based environment
- Bare hypervisor directly runs on hardware without an OS. Used mostly in data centers and servers
- This hypervisor is faster and more secure
- **Examples:** KVM, VMware ESXi

**2. Hosted Hypervisor (Type 2 Hypervisor)**
- It runs on conventional OS as a software layer or application
- This type is better for individual users who want to run multiple OS on a personal computer
- Hosted hypervisor runs on top of the OS like: Laptop → OS → Hypervisor → VM
- This hypervisor is mostly used in personal computers and testing
- **Examples:** Oracle VM VirtualBox, VMware Workstation

### Difference: Bare Metal vs Hosted Hypervisor

| Feature | Type 1 (Bare-Metal) | Type 2 (Hosted) |
|---|---|---|
| Architecture | Installed directly on the hardware | Installed as an app on a host OS |
| Performance | High efficiency and fast speed with direct hardware access | Lower performance due to the overhead of the host OS |
| Security | Stronger security with a smaller attack surface | Weaker security, as it depends on the host OS |
| Ease of Use | More complex to set up and manage | Simple and user-friendly setup |
| Common Uses | Enterprise data centers and cloud servers | Personal testing, learning, and local development |
| Examples | VMware ESXi, Microsoft Hyper-V, KVM | Oracle VirtualBox, VMware Workstation Pro |

### Why is a Hypervisor Important?

Hypervisors are important because they make virtualization possible. Without hypervisor one computer can run only 1 OS. With hypervisor 1 computer can run many VM at the same time.

**Example:** 1 server can run – Linux server for databases, Windows server for applications, Ubuntu server for testing, all at same time.

### Benefits of Hypervisors
1. **Better resource usage** – multiple VMs share the same hardware
2. **Cost saving** – less need for physical server
3. **Isolation** – if 1 VM crashes, others are not affected
4. **Easy testing** – developers can test software in different OS
5. **Disaster recovery** – VMs can be backed up and restored easily
6. **Faster deployment** – new VM can be created quickly
7. **Hardware independence** – a hypervisor separates software from hardware
   - Example: U can run macOS in virtual machine on another system instead of needing a separate Mac computer
8. **Efficiency** – hypervisors make it quick and easy to create new systems
9. **Scalability** – organization can run many workloads on 1 physical machine
   - Example: Instead of buying 10 physical servers, a company can run 10 VM on 1 server
10. **Portability** – VM can be moved from 1 computer to another easily
    - Example: If a server becomes overload, VM can be shifted to another server without reinstalling everything

### How Hypervisor Works
1. System administrator installs hypervisor software on a physical server
2. The physical machine is called the host
3. The hypervisor creates VM (guest)
4. Each VM gets allocated resources like – CPU, RAM, STORAGE
5. When a VM needs resources, the hypervisor communicates with the hardware and provides them

So the hypervisor act as a middle layer between hardware and VM.

### What is a Cloud Hypervisor?

A cloud hypervisor is used by cloud providers to create virtual servers for users. Cloud providers like AWS, Google Cloud, Azure use hypervisors in their data centers.

**Example:** On Amazon Elastic Compute Cloud (EC2), users can create virtual servers using hypervisor technology.

---

## Q3) What Hypervisors Did AWS Use?

- **Xen** – this was the primary hypervisor for earlier generation of EC2 instances
- **KVM (Kernel based Virtual Machine)** – while less emphasized than Nitro and Xen, KVM is also used by AWS
- **Nitro** – this is new hypervisor developed by AWS. This is modern, lightweight hypervisor that is part of the AWS Nitro System

---

## Cloud Models

### IaaS – Infrastructure as a Service

IaaS provides virtualized computing resources such as servers, storage, and networking over the internet on a pay-as-you-go basis. It offers the highest level of control and flexibility, acting as the digital foundation for your IT operations.

**Example:** It is like renting an empty plot of land. The provider gives you the space and the utilities (hardware, network, storage), but you are entirely responsible for building the house (installing OS, middleware, and application).

**Characteristics:**
- Eliminates the capital expense of buying physical servers
- Offers complete control over OS, application, and development frameworks
- Resources can be scaled up or down instantly based on traffic spikes

**Audience:** IT administrators, network architects, and DevOps teams

**Popular providers:** AWS EC2, Microsoft Azure (VM), Google Compute Engine (GCE), Digital Ocean, StackScale, VMware

### PaaS – Platform as a Service

PaaS offers a complete, managed cloud environment specifically designed for developing, testing, running, and managing applications. It abstracts the underlying infrastructure so developers can focus purely on writing code.

**Example:** It is like renting an unfurnished house. The foundation, plumbing, and electricity are already built and maintained by the landlord, you just need to bring your furniture and decorate (write and deploy your code).

**Characteristics:**
- Acts as a complete toolkit for developers, providing pre-built tools, libraries, and development environments
- The cloud provider handles all backend infrastructure, including server provisioning, OS patching, and network routing
- Automates deployment workflows and allows for easy team collaboration

**Examples:** Flynn, Cloud Foundry, Heroku, OpenShift

### SaaS – Software as a Service

SaaS is the most user-friendly and widely used cloud model. It delivers fully functional, ready-to-use software applications over the internet, typically on a subscription basis.

**Example:** It is like staying in a fully furnished, serviced hotel room. Everything is provided, maintained, and cleaned for you, you simply walk in and use it.

**Characteristics:**
- Applications are ready to use immediately directly through a web browser or mobile app
- The cloud provider handles absolutely everything: infrastructure, software updates, bug fixes and security maintenance
- Requires minimal technical expertise to operate

**Examples:** Gmail, Trello, Slack, Acumbamail, Office 365

---
---
<img width="991" height="495" alt="image" src="https://github.com/user-attachments/assets/e1dea398-9272-43cb-be2f-d13e21a5c455" />

---
---

## Q4) What is Cloud Computing?

Cloud computing is an on-demand delivery of IT resources over the internet with pay-as-you-go pricing. Instead of buying, owning and maintaining physical data centers and servers, you can access technology services, such as computing, storage, and databases, on an as-needed basis from a cloud provider like AWS.

Cloud computing means using servers, storage, software, and services through the internet instead of your own computer or data center.

---

## Q5) Who Uses Cloud Computing?

Today almost every organization uses cloud computing. Instead of storing data and running applications on their own computers or servers, companies use internet-based servers (cloud).

1. **Healthcare companies**
   - Store patient data
   - Analyze health reports
   - Develop personalized treatments
2. **Banks and financial companies**
   - Detect fraud in real time
   - Secure transactions
   - Store customer data
3. **Gaming companies**
   - Run online multiplayer games
   - Deliver games to millions of players worldwide
4. **IT companies**
   - Build websites and apps
   - Test software
   - Store large amt of data

In short – cloud computing is used by companies of all sizes and industries.

---

## Q6) Benefits of Cloud Computing

1. **Agility (work faster)**
   Cloud gives quick access to many technologies like – computing power, storage, databases, ML, IoT, Analytics. Earlier companies needed weeks or months to buy servers and set up systems, but now, they can start everything in a few minutes using cloud.
   - Example: Company test new idea quickly, develop products faster, innovate easily

2. **Elasticity (easy scaling)**
   Elasticity means increase or decrease resources anytime.
   - Example: Online shopping website – during normal days, fewer users; during festival sale, millions of users. With cloud, companies can increase servers during sale and reduce after sale. So company only uses what they need.

3. **Cost saving**
   Without cloud, companies must buy – physical servers, networking equipment, data centers, cooling systems, electricity – this costs a lot of money. With cloud – no need to buy hardware, just pay for what you use – reduces the total cost.

4. **Deploy globally in minutes**
   Cloud providers like AWS, Google Cloud, Azure have data centers around the world, so companies can run applications in different countries quickly.
   - Example: A company in India can deploy its app in USA, Europe, Japan

---

## What is EC2?

EC2 (Amazon Elastic Compute Cloud) is a service provided by Amazon Web Services (AWS). EC2 lets you create and run virtual machines on the internet instead of using your own physical computer or server.

### Instance States (Total: 6)

1. Pending
2. Running
3. Stopping
4. Stopped
5. Shutting down
6. Terminated

*Fig: EC2 states*

| Instance State | Description | Instance Usage Billing |
|---|---|---|
| Pending | The instance is preparing to enter the running state. An instance enters the pending state when it is launched or when it is started after being in the stopped state. | Not billed |
| Running | The instance is running and ready for use. | Billed |
| Stopping | The instance is preparing to be stopped. | Not billed |
| Stopped | The instance is shut down and cannot be used. The instance can be started at any time. | Not billed |
| Shutting-down | The instance is preparing to be terminated. | Not billed |
| Terminated | The instance has been permanently deleted and cannot be started. | Not billed |

> **Note:** If you hibernate an instance, you're billed while the instance is in the stopping state.
>
> Reserved Instances that applied to terminated instances are billed until the end of their term according to their payment option.

### Status Checks

1. **System status check** – verifies infrastructure hosting your instance is functioning correctly or not
2. **Instance status check** – monitors the software and network configuration of your instance

**t3 family**
- 3/3 – all ok (modern, t3 family image support)
- 2/3 – image issue (OS)
- 1/3 – AWS (software issue)
- 0/3 – hardware issue

**t2 family**
- 2/2 – all ok (t2 family)
- 1/2 – software issue
- 0/2 – hardware issue
