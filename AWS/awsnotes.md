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
<img width="991" height="495" alt="image" src="https://github.com/user-attachments/assets/e1dea398-9272-43cb-be2f-d13e21a5c455" />

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
<<<<<<< HEAD
=======


### Regions, EC2 Access, AMI, Instance Types, EBS & Filesystem
---
## 1. AWS Global Infrastructure

### What is a Region? (39 regions globally)
- **Region** – AWS regions are separate geographical area that has clusters of data centers.
- Each region is completely independent and isolated from other regions.
- AWS has multiple regions around the world, allowing users to deploy applications in locations that are closer to their end-users.

### What is an Availability Zone? (123 AZs)
- **Availability Zone** – actual location of datacenter.
- Availability Zones (AZs) are isolated locations within a region.
- Each region has multiple AZs, which are designed to be independent from each other.
- AZs provide high availability and fault tolerance for applications by allowing users to distribute their resources across multiple locations.

### AWS Region & Availability Zones (AZs)

An AZ is both (region specific and isolated), but in completely different ways:

**It is Region-Specific:** An AZ physically belongs to one specific AWS Region. It can't exist outside of it.
- Example: The AZ `us-east-1a` is permanently locked inside the `us-east-1` (N. Virginia) region.

**It is Fault-isolated (zone isolation):** AZs within the same region are isolated from each other regarding power, cooling, and networking. If one AZ experiences a fire or flood, the other AZs in that same region keep running.

An AZ is region specific because it can't leave its region, but it relies on isolation principles so that local failures do not spread to neighbouring zones.

**An AWS Region is region-isolated:** By design, AWS physically & locally isolated every region from all other regions around the world. This ensures that a total system outage, natural disaster, or data breach in one region cannot impact or spread to another region.

---

## 2. EC2 Security Basics

### Key Pair
- A key pair consists of a private key and a public key.
- User consists private key and EC2 instance consists public key.
- Key pairs are used for secure SSH access to EC2 instances.
- Used for authorization and authentication | to securely enter into instance (server). (User has private key and AWS has public key)
- When both private and public key matches, we are able to enter into instance (we can create our server).

### Security Groups
- Security groups act as virtual firewalls for your EC2 instances.
- They control inbound and outbound traffic from your instances.
- Outbound rules allow all traffic by default.
- You can define rules to allow or deny specific traffic based on protocols, ports.
- Firewall plays vital role to get an access of server.
- There are various protocols present in firewall that allow user to get an access of server, like HTTP, HTTPS, SSH, RDP.

### Important Protocols and Port Numbers

| Protocol | Port No | Used For |
|---|---|---|
| FTP | 21 | Transferring files to/from a server |
| SSH | 22 | Secure login to Linux servers |
| Telnet | 23 | Remote login (old, unencrypted) |
| SMTP | 25 | Sending emails |
| DNS | 53 | Resolving domain names to IP addresses |
| HTTP | 80 | Normal website traffic (unencrypted) |
| POP3 | 110 | Receiving emails |
| NTP | 123 | Time synchronization |
| IMAP | 143 | Receiving/managing emails on server |
| LDAP | 389 | Directory services (user/login info) |
| HTTPS | 443 | Secure website traffic (encrypted) |
| SMB | 445 | Windows file sharing |
| SMTPS | 465 | Sending emails securely |
| IMAPS | 993 | Receiving emails securely |
| POP3S | 995 | Receiving emails securely (POP3 + SSL) |
| MSSQL | 1433 | Microsoft SQL Server database |
| Oracle DB | 1521 | Oracle database |
| NFS | 2049 | Network File System (shared storage) |
| MySQL | 3306 | MySQL database |
| RDP | 3389 | Remote login to Windows servers |
| PostgreSQL | 5432 | PostgreSQL database |
| SNMP | 161 | Network device monitoring |
| Redis | 6379 | Redis database/cache |
| HTTP-Alt | 8080 | Alternate web server port |
| MongoDB | 27017 | MongoDB database |

---

## 3. Connecting to EC2 Instances

### SSH Client
We use SSH to securely access and control remote server over the unsecured network.

**SSH access using key pair:**
- SSH (secure shell host, port 22) should be open to connect/access via SSH on Linux server.
```
ssh -i "key-pair" user-name@public-ip-address
```

**SSH client access using password:**
```
ssh root@public-ip-address
enter pass of root
```

**Steps:**
1. Launch an instance
2. Go to `cd /etc/ssh`
3. `ls`
4. Edit `sshd_config` by nano/vim editor
5. Make `PermitRootLogin = yes` & `PasswordAuthentication = yes`
6. Go to `cd sshd_config.d` directory
7. `PasswordAuthentication = yes`
8. Go to other terminal (PowerShell), type command and get access of SSH from any OS

### RDP (Remote Desktop Protocol)
- Launching Windows server from any other operating system
- RDP (port 3389) must be open for accessing Windows server
- Selecting Windows AMI while instance launching

**Steps:**
1. Launch instance (as always / normal)
2. Click on connect
3. Select RDP client there
4. Download remote desktop file
5. Click on get password
6. Then upload key pair file and decrypt the file
7. After that copy the password
8. And open remote desktop file which we downloaded already
9. And do further process as instructions
10. Finally u successfully connected to Windows OS from any OS

---

## 4. Hosting a Website by its Link Address

**Steps:**
1. Launch an EC2 instance
2. Go to root user – `sudo -i`
3. Type command – `wget <paste link address here>`
4. Rename file name by .zip – `mv file-name file-name.zip`
5. Update server – `apt update -y`
6. Install unzip if not present – `apt install unzip`
7. Unzip the .zip file
8. Now install nginx – `apt install nginx`
9. Check `/var/www/html` – it's root directory of nginx (all nginx files are present in this directory)
10. `cd <template-dir>` = go to your website directory
11. Copy all content of our link file – `cp -rf file-name/* /var/www/html`
    (`-rf` = recursively and forcefully, `/*` = for all content)
12. Now copy public IP address of instance and paste on new browser
13. On browser we see website

---

## 5. AMI – Amazon Machine Image

### AMI vs Launch Template vs Snapshot (Easy Explanation)

These three sound similar but each one saves a **different thing**:

**AMI (Amazon Machine Image) – a "ready-made copy" of a full server**
Think of an AMI as a photocopy of a computer that already has an OS and your software installed on it. Instead of installing the OS and all your packages again every time, you just launch a new EC2 instance directly from this photocopy, and it comes ready with everything already set up. You can also copy an AMI to another AWS region or account, so you can reuse the same "ready server" anywhere.

**Launch Template – a "settings form" for launching instances**
A launch template doesn't store the OS or the actual disk data — it stores the *settings* you'd otherwise have to fill in every time: which instance type, which AMI, which security group, which key pair, and so on. It's like a saved form: once it's filled in, you just click "launch" instead of re-entering every setting each time. It's also used by services like AWS CloudFormation and Auto Scaling to automatically create many identical instances at once. A launch template cannot be copied directly to another region/account — you'd need to recreate it there manually.

**Snapshot – a "backup" of just the data on a disk**
A snapshot doesn't care about the OS or software setup — it simply backs up the data sitting on an EBS volume at a point in time, along with some metadata. If your main instance is accidentally terminated, the data isn't gone — you can create a new volume from the snapshot and attach it to a new instance to get your files back. Snapshots can also be copied to another region or account, which makes them useful for disaster recovery.

### Quick Comparison

| | AMI | Launch Template | Snapshot |
|---|---|---|---|
| **What it saves** | A full server image (OS + installed software) | Launch settings/configuration (a blueprint) | Just the data on a disk (a backup) |
| **Main purpose** | Skip reinstalling OS/software each time | Skip re-entering instance settings each time | Recover data if instance/volume is lost |
| **Can you launch a new instance from it?** | Yes, directly | Yes, directly | No — you must first create a volume from it, then attach it to an instance |
| **Copy to another region/account?** | Yes, directly | No — must be recreated manually | Yes, directly |
| **Best used for** | Reusing a fully configured server setup | Automating/standardizing how instances are launched (e.g. with CloudFormation, Auto Scaling) | Backing up and restoring data |

---

## 6. Types of EC2 Instances

1. **General purpose instance** – balanced CPU, memory, and networking resources
   - Used in web servers, small databases, development environment (T3, M5, M6g)
2. **Compute optimized instance** – high power compared to memory
   - Used in batch processing, game servers, machine learning inference (C5, C6g)
3. **Memory optimized instance** – more memory compared to CPU
   - Used in high-performance databases, big data analytics, real-time processing (R5, X1, Z1d)
4. **Storage optimized instance** – designed for workloads needing high, fast local storage
   - Used in data warehousing, big data, log processing (I3, D2, H1)
5. **Accelerated computing instance** – specialized hardware like GPUs or FPGA for faster processing
   - Used in machine learning, graphics rendering, scientific simulations (P3, G4, F1)
6. **HPC instance** – (HPC) High Performance Computing instances offer the best price performance for running HPC workloads at scale
   - Used in high performance processors such as complex simulation, deep learning and visual effects rendering

---

## 7. EC2 Instance Purchasing Options

- **On-Demand Instance** – pay for compute capacity with no commitment. Best for short term, irregular, or unpredictable workloads that cannot be interrupted.
- **Reserved Instance** – discount price for 1–3 years commitment. Best for stable, predictable workloads. Up to 72% discount compared to on-demand.
- **Savings Plans** – flexible discounts based on usage commitment (1–3 years). Offers 72% discount compared to On-Demand instance. Best for steady state, predictable workloads with flexible architecture.
- **Spot Instance** – request unused Amazon EC2 capacity at discounts of up to 90% off on-demand prices. AWS can interrupt these instances with 2-min warning if capacity is suddenly needed back.
- **Dedicated Host** – physical server dedicated to your use.
- **Dedicated Instances** – instances on hardware dedicated to you. Dedicated instances are isolated to your AWS account but might share hardware with other instances at physical level.
- **Capacity Reservations** – reserve capacity in a specific Availability Zone.

---

## 8. EBS – Elastic Block Storage

Elastic Block Storage = Persistent Volume

After creating/attaching volume must do 3 things: **Partition → Format → Mount**

### EBS has 7 types of volumes

- **General Purpose SSD (gp2)** – general purpose SSD volume that balances price performance for a wide variety of transactional workloads
  - Use cases: Boot volumes, low-latency interactive apps, dev & test
- **General Purpose SSD (gp3)** – general purpose SSD volume that balances price performance for a wide variety of transactional workloads
- **Provisioned IOPS SSD (io1)** – high-performance SSD volume designed for latency-sensitive transactional workloads
- **Provisioned IOPS SSD (io2)** – high-performance SSD volume designed for business-critical latency-sensitive applications
- **Cold HDD (sc1)** – lowest cost HDD volume designed for less frequently accessed workloads
  - Use cases: colder data, requiring fewer scans/day
- **Throughput Optimized HDD (st1)** – low cost HDD volume designed for frequently accessed, throughput-intensive workloads
  - Use cases: big data, data warehouses, log processing
- **Magnetic (standard)** – suitable for workloads where data is infrequently accessed

> All are booting volumes except Throughput Optimized (st1) and Cold HDD (sc1).

### EBS Volume Comparison

| Volume Type | Latency | Max IOPS/Volume | Max Throughput/Volume | Max Size | Best Use |
|---|---|---|---|---|---|
| gp2 | Single-digit ms | 16,000 | 250 MB/s | 16 TB | General workloads (older) |
| gp3 | Single-digit ms | 80,000 | 2,000 MB/s | 64 TB | Most EC2 workloads |
| io1 | Single-digit ms | 64,000 | 1,000 MB/s | 16 TB | High-performance databases |
| io2 | Sub-millisecond | 256,000 | 4,000 MB/s | 64 TB | Mission-critical databases |
| st1 | HDD | 500 | 500 MB/s | 16 TB | Big Data, Log Processing |
| sc1 | HDD | 250 | 250 MB/s | 16 TB | Archive, Cold Data |
| Magnetic | Highest latency | Low | Low | 1 TB | Legacy workloads |

### IOPS vs Throughput

**IOPS = Input Output Operations Per Second**
- How many read/write operations a storage device can perform in 1 second
- Example: A disk with 80k IOPS can perform up to 80k read/write operations per sec
- Best for: databases, banking applications, online transactions etc.

**Throughput = amount of data transferred per second** (measured in MB/s or GB/s)
- How much total data can be read or written every second
- Example: A disk with 2000 MB/s throughput can transfer 2000 MB of data every sec
- Best for: large video files, backups, big data, log processing

**Q) Can we attach EBS volume to multiple instances, or which volume can attach to multiple instances?**
→ Provisioned IOPS SSD **io2**

---

## 9. Attaching a Volume to an EC2 Instance

**Steps:**
1. Launch instance (as always)
2. Go to Elastic Block Store → click volume → create volume
3. Select storage (ensure that AZ / select AZ same as EC2 instance zone) → select instance → select device name
4. Attach volume
5. Now connect the instance
6. Check volume by command `lsblk`
7. Partition, format and mount:
   - Make partition → `fdisk /dev/nvme1n1`
   - Format / create file system → `mkfs.ext4 /dev/nvme1n1p1`
   - Mount file in /mnt dir → `mount /dev/nvme1n1p1 /mnt`
8. Check file in mnt → `cd /mnt`
9. Finally ur volume is added to EC2 instance and partition is also done

### For Making Partition

| Action | Input |
|---|---|
| Command | `fdisk /dev/nvme1n1` |
| For new partition | type `n` |
| For primary partition | type `p` |
| For partition no | type `1` |
| For 1st partition | default (nothing to type) |
| For 2nd partition | add partition value (+2G etc.) |
| For write and exit | type `w` |

Finally partition is done.

> This is temporary mounting. When we do temporary mounting of EBS volume it will be unmounted automatically when we restart the instance. So we need to manually mount it again into the directory.

### Permanent Mounting of Partition
Permanent mounting does not remove even if instance is restarted.

1. Create volume (Extended volume +10G etc.)
2. Attach it to an EC2 instance
3. Make partition → `fdisk /dev/nvme1n1`
4. Format → `mkfs.ext4 /dev/nvme1n1p1`
5. Edit fstab → `nano /etc/fstab`
6. Add details like:

```
partition name        mounting point   filesystem   permission        priority
/dev/nvme1n1p1        /media           xfs/ext4     defaults          0 0
UUID=de127641-a16f-4fd4-8e52-97db0ddd3941 /media ext4 defaults,nofail 0 2
```
   - For check UUID = `sudo blkid /dev/nvme1n1p1`
   - Save the details
7. Now mount the partition → `mount -a` (this command automatically mounts the details of fstab permanently into /media)
8. Then reload the system → `systemctl daemon-reload`
9. Check by `lsblk`
10. Check either files are present or not

---

## 10. Snapshots (Backup)

### Taking Backup Using Snapshots

**Steps:**
1. Launch an instance
2. Create a volume
3. Make partition → `fdisk /dev/nvme1n1`
4. Format → `mkfs.ext4 /dev/nvme1n1p1`
5. Mount in /mnt dir → `mount /dev/nvme1n1p1 /mnt`
6. Add some data in /mnt directory like files, dir etc. Also add some content in files
7. Now creating snapshot → go to volume → select volume → click on action → select create snapshot
8. Go to snapshot and click on create volume from snapshot
9. Make some configuration
10. Now attach that new volume to the new instance
11. Connect the instance → mount file in /mnt dir
12. And check either previous data is present or not

Finally snapshot is created as well as it has backup of your metadata.

> It's a temporary snapshot. It can't hold backup of data for a long time. If we stop an instance then snapshot will be deleted.

### Lifecycle Management (Automatic Snapshot Creation)

Go to Lifecycle Manager → click on create lifecycle policy → select policy type → custom policy → schedule based policy → EBS Snapshot policy → select volume → target resource tags → select name → enter name → click add → write description → next → schedule details → add details here → review policy → create policy

Finally automatic snapshot will create, and it will show in snapshot section after each hour.

### Copy Snapshot
1. Copy the snapshot
2. Select region where to copy
3. Create new instance
4. Create new volume from snapshot (make sure about region)
5. Attach volume to the instance
6. Connect instance
7. Mount the directory – finally it will show your backup data (which is stored in snapshot)

---

## 11. If Key Pair is Lost – How to Take Backup of EC2 Instance?

**Most important concept:** If key pair is lost then EC2 instance still runs, data still exists, but u can't login into server. Server is alive but locked. Key pair only controls login access and EBS contains data.

**Method 1: Create snapshot / Attach volume to another instance**
1. Stop old instance
2. Detach volume from instance
3. Launch new instance – create new key-pair, new instance
4. Attach old EBS volume to new instance – now new instance can access old disk/data
5. Mount volume in Linux

---

## 12. Filesystem (Simplified Explanation)

### What is a Filesystem?

A filesystem is simply the **method a disk uses to arrange your data**. A disk on its own is just empty space. The filesystem decides where each file is kept, what its name is, who can open it, and how the system finds it again later.

Think of a disk as an empty cupboard. The filesystem is the shelving plan — it decides how many shelves there are, how things are labelled, and who is allowed to open which shelf. Without that plan, the cupboard is just a box you can't use properly.

That is why, after attaching a new EBS volume, we run `mkfs.ext4` — we are telling the blank disk which "shelving plan" to use before storing anything on it.

### What a Filesystem Helps You Do
- Store files and folders
- Read/write data
- Manage permissions (who can view, edit, or delete a file)
- Access data from servers/applications

### Common Filesystems in Linux and AWS

**ext4 – the normal default choice**
This is the filesystem Ubuntu and most Linux EC2 servers use out of the box. It is stable, fast enough for almost everything, and easy to manage. It also has journaling, which means if the server suddenly shuts down, it can recover without losing the whole disk. Best for general-purpose work and small to medium workloads. It is not the best pick for huge-scale data processing.

**XFS – for big, heavy data**
XFS is a high-performance 64-bit journaling filesystem, very popular in enterprise Linux (Red Hat uses it by default). It handles very large files extremely well and can scale to TB/PB of storage without slowing down. Best for databases, big data, and large EBS volumes. Its one drawback: you can grow an XFS filesystem, but shrinking it is very difficult or impossible.

**Btrfs – modern, feature-rich**
Btrfs supports snapshots, compression, and self-healing (copy-on-write). Useful for advanced Linux setups and backup systems. It is more complex and less commonly used in production.

**ZFS – for data protection**
ZFS focuses on keeping data correct and safe. It offers data integrity checks, snapshots, RAID-like protection, and compression, so it prevents silent corruption. Used in storage servers and enterprise systems. The trade-off is that it uses a lot of RAM.

**NTFS – the Windows filesystem**
This is what Windows uses, including Windows EC2 instances and Windows PCs. It supports Windows permissions, large files, and journaling.

**FAT32 – old and simple**
Very old but works almost everywhere (Windows, Linux, USB drives). Its main limitation is that a single file cannot be larger than 4 GB.

**exFAT – improved FAT32**
Made for large USB drives, pen drives, and SD cards. It removes the 4 GB file limit and still works across Windows, Linux, and Mac.

### Quick Comparison

| Filesystem | Mostly used in | Best for | Key point |
|---|---|---|---|
| ext4 | Linux, EC2 Linux servers, Ubuntu | General purpose | Reliable and simple, default choice |
| XFS | Databases, big data, large EBS volumes, RHEL | High performance & large data | Very fast at scale, hard to shrink |
| Btrfs | Advanced Linux setups, backup systems | Snapshots & advanced features | Powerful but complex |
| ZFS | Storage/enterprise servers | Data protection | Prevents corruption, needs more RAM |
| NTFS | Windows | Windows systems & Windows EC2 | Windows permissions, large files |
| FAT32 | Windows/Linux/USB | Compatibility | Max file size 4 GB |
| exFAT | Large USB drives, SD cards | Cross-platform | Large files, works everywhere |

### Swap
Swap is not used for storing files. It acts as **extra RAM space on the disk**. When the RAM becomes full, Linux moves some data into swap so the system keeps running instead of crashing. It is slower than real RAM, so it is a safety net, not a replacement.

### Important Distinction

| Term | What it actually is |
|---|---|
| ext4, XFS, NTFS | **Filesystem formats** – actual filesystem technologies used inside operating systems |
| EFS, FSx | **AWS managed file storage services** – AWS cloud services that already provide managed network filesystems |

In short: ext4 and XFS are something *you* format a disk with. EFS and FSx are ready-made storage services that AWS runs and manages for you.
>>>>>>> 9fb5f7b (AWS notes)

# AWS Notes 
### NFS/EFS, Networking, VPC, Load Balancers & Troubleshooting

---

## 1. NFS – Network File System

### What is NFS?
NFS (Network File System) is a way for computers to share files over a network.

**Easy way to picture it:** Think of it like Google Drive or OneDrive, but for servers inside a network. You create one storage location, and multiple computers (clients) connect to it and use it as if it were their own local disk.

**Key points:**
- Centralized storage
- Region specific
- Attach over the network
- Attach multiple instances

**NFS server** – the machine that has the actual storage and shares it.
**NFS client** – other machines that connect to the server and access files.

The client mounts (attaches) the shared folder and can read/write files just like a normal folder.

### EBS vs EFS – Storage Limit
- **EBS** = max storage 64 TB
- **EFS** = unlimited storage

### Drawbacks of EBS
- Connects to only a single instance
- **Region specific:** tied to only one AZ
- **No simultaneous sharing:** multiple servers can't share data
- **Fixed capacity:** requires manual, upfront provisioning
- **Container limits:** hard to share across container nodes
- EBS is zone-locked, meaning it is restricted to just one AZ inside that region. If that specific zone fails, the EBS volume becomes unavailable, even if the rest of the region is running fine.

**That's why EFS was introduced** — EFS is region-specific but distributed across the entire region (all AZs).

### EFS Features
1. **Centralized storage** – files are stored in one place, not scattered across machines
2. **Shared access** – multiple servers can access the same data
3. **Scalability** – add more clients without copying files everywhere
4. **Transparency** – to the client, it looks like a normal folder/directory
5. **Uses TCP/UDP port 2049** – default port for NFS communication

### Why Do We Need NFS?
- **Without NFS:** every server would have its own local files, making it difficult to share or sync data.
- **With NFS:** all servers point to the same storage, making collaboration and scaling easier.

**Use case:** Hosting a website on multiple servers – all servers can use the same images, code, or logs from NFS.

> In AWS → **EFS (Elastic File System)** is Amazon's managed NFS service.

### Versions of NFS
- **NFSv2** – old version, basic sharing
- **NFSv3** – supports large files, better performance
- **NFSv4** – latest, more secure (supports encryption, ACLs)

AWS EFS uses **NFSv4.1** by default.

### Is NFS Region-Specific or AZ-Specific?
- **NFS (general protocol)** – not tied to region/AZ, depends only on network reachability
- **Amazon EFS (managed NFS):**
  - Region-specific – an EFS file system exists only in one AWS region
  - Multi-AZ – data is stored across multiple AZs within that region
  - Instances in different AZs of the same region can mount the same EFS file system

### Region-Specific vs Region-Isolated
- **Region-specific:** services or resources that are tied to one geographic AWS region (e.g. US East). They can't move or scale outside that boundary natively.
  - Example: EBS is region-specific because a volume created in Northern Virginia can't be attached to a server in Oregon.
- **Region-isolation:** a security and fault-tolerance design principle. AWS completely separates its regions from each other so that a failure, outage, or data leak in one region can't impact or spread to another region.

### EFS Lifecycle Management (Cost Optimization)
Auto-moves old files to cheaper storage to save money. EFS Lifecycle Management automatically moves infrequently accessed files from EFS Standard storage to cheaper storage classes like EFS-IA or EFS Archive after a specified period of inactivity, helping reduce storage costs.

**3 classes of Lifecycle Management in EFS:**
1. **Transition into Standard** – if file is used daily, it stays in Standard
2. **Transition into Infrequent Access (IA)** – if not used for the last 30 days, it automatically moves to IA
3. **Transition into Archive** – if not used for 90 days, it automatically moves to Archive

No need to do this manually.

> NFS port (2049) should be allowed for EFS access.

### Steps: Attaching a Filesystem (EFS) to an Instance
1. Launch an EC2 instance
2. Go to security – ensure port NFS (2049) is enabled
3. In the search bar, search for EFS
4. Create EFS
5. Name the filesystem
6. Select "customized"
7. Ensure security group is same as the instance's security group
8. Go to next step → next step again
9. Finally, EFS (filesystem) is created
10. Select filesystem and click on attach
11. Copy the mounting path (temporary/permanent mounting)
12. Connect to instance → `sudo -i`
13. Run command: `apt update` → `apt install nfs-common` (NFS client)
14. Paste the copied path
15. `df -h` (filesystem is mounted on the selected path/directory)

---

## 2. Basic Networking

Networking is the backbone of modern computing and communication systems. It involves connecting devices to share resources, data, and information efficiently.

### Key Networking Components

**1. IP Address (Internet Protocol Address)**
A unique identifier assigned to each device on a network.
- **IPv4** (e.g. `192.168.1.1`) – 32-bit address
- **IPv6** (e.g. `2001:0db8:85a3:0000:0000:8a2e:0370:7334`) – 128-bit address

**Classes of IPv4 Address (5 total classes)**

| Class | 1st Octet Range | Default Subnet Mask | Network/Host | No. of Networks | Max Nodes/Network |
|---|---|---|---|---|---|
| A | 1–126 | 255.0.0.0 | N.H.H.H | 126 | 16,777,214 |
| B | 128–191 | 255.255.0.0 | N.N.H.H | 16,384 | 65,534 |
| C | 192–223 | 255.255.255.0 | N.N.N.H | 2,097,152 | 254 |
| D | 224–239 | Scientific use | — | — | — |
| E | 240–254 | Future use | — | — | — |

**2. Subnet Mask**
Defines the network and host portions of an IP address (which part of an IP is network and which is host).
- Example: In IPv4, a subnet mask of `255.255.255.0` allows a total of 256 addresses, of which one is for the network and one for broadcast.

**3. Subnet**
A smaller network created from a larger network.

**4. Gateway**
A node that routes traffic from one network to another, typically connecting a private network to the internet.

**5. DNS (Domain Name System)**
Translates human-readable domain names (e.g. `www.example.com`) into IP addresses (e.g. `192.168.0.0`).

**6. MAC Address (Media Access Control)**
A hardware address that identifies a device within a local network. It is a 48-bit address.

### Types of Networks
- **LAN (Local Area Network):** small networks, typically within a single location, such as a home or office
- **WAN (Wide Area Network):** large networks spanning geographic locations, such as the internet
- **VLAN (Virtual Local Area Network):** logical segmentation of a LAN for better management and security

### Networking Protocols
1. **TCP/IP** (Transmission Control Protocol/Internet Protocol) – core protocol suite for communication over the internet
2. **HTTP/HTTPS** – protocols for transferring hypertext data (webpages)
3. **FTP** (File Transfer Protocol) – for transferring files over a network
4. **SSH** (Secure Shell) – for secure remote administration

---

## 3. CIDR (Classless Inter-Domain Routing)

### What is CIDR?
CIDR tells us how many IP addresses are available in the network.

**In simple words:** CIDR is just a short-hand way of writing "how big is this network." Instead of using old fixed classes (A, B, C), CIDR lets you size a network to exactly how many addresses you need — no more, no less.

- CIDR is a way to define the size/range of IP addresses in a network
- CIDR is a method for efficiently allocating IP addresses and routing data
- It replaces the older class-based IP addressing system (Class A, B, C)

**Written like:** `192.168.1.0/24`
- `192.168.1.0` = Network address
- `/24` = CIDR block (this tells how many bits are fixed for the network)
- `/24` means 256 IP addresses, range = `192.168.1.0` – `192.168.1.255`

CIDR range = 0–32, but usable range = 8–31.

### Benefits of CIDR
1. **Efficient IP address allocation** – prevents waste by allowing subnets of variable sizes
2. **Improved routing efficiency** – reduces the size of routing tables by grouping multiple networks under a single prefix
3. **Scalability** – supports hierarchical network design for better scalability

### Common CIDR Values

| CIDR | Total IPs |
|---|---|
| /32 | 1 IP |
| /24 | 256 IPs |
| /16 | 65,536 IPs |
| /8 | 16 million IPs |

> CIDR is important because it's used in VPCs, Subnets, Security Groups, Route Tables, and Firewalls. AWS networking completely depends on CIDR.

**Rule of thumb:** Smaller CIDR number = more IPs, and bigger CIDR number = fewer IPs.

---

## 4. Introduction to VPC

### What is VPC?
Amazon Virtual Private Cloud (VPC) allows you to launch AWS resources in a logically isolated network that you define.

**Easy way to picture it:** A VPC is like your own private section of AWS — a fenced-off area of the cloud where only your resources live, and you decide exactly how the roads (routing), gates (gateways), and fences (security groups) inside it work.

You have complete control over your virtual networking environment, including selecting your own IP address range, creating subnets, and configuring route tables and gateways.

### Key Features of a VPC
1. **Logical isolation** – operates within a region, providing control over network setup
2. **Subnets** – dividing your VPC into smaller segments based on your requirements
3. **Security** – use security groups and network ACLs for fine-grained control
4. **Internet gateway** – attach to a VPC for internet access
5. **Private connectivity** – use VPN or Direct Connect to connect on-premises environments
6. **Elastic IPs** – assign static IP addresses to resources in your VPC

### Types of VPC
1. **Default VPC** – automatically created by AWS in each region. It includes a public subnet in each availability zone, enabling immediate access to AWS services.
2. **Custom VPC** – created manually to meet specific networking requirements, offering full control over the network configuration.

> CIDR calculation for subnets – covered separately in the notebook.

### Steps to Launch an EC2 Instance from VPC (Public & Private Subnet)

1. First, create a VPC
2. Create subnets (public and private subnet)
3. Go to public subnet setting – enable public IP
4. Create Internet Gateway (IGW) for internet access
5. Create NAT Gateway for connecting to private subnet – availability mode = zonal, subnet = private, allocate elastic IP, create NAT gateway
6. Attach IGW to your VPC
7. Create 2 route tables
8. Go to edit route for both (public and private)
9. Add route path (separate for both)
10. Go to actions → edit subnet association (separate for both public and private)
11. Save changes
12. Create EC2 instance
13. Edit network setting → select your VPC
14. Select public subnet (for public instance)
15. Select private subnet (for private instance)
16. Create new security group (at initial launch only)
17. Then select existing security group for private instance launching
18. Connect to instance
19. For connecting with private instance:
    - Go through SSH (because we can't directly access a private subnet's instance)
    - First upload key-pair → `nano key-pair.pem`
    - Upload key pair, save it, and exit
    - Change permission of key-pair → `chmod 400 key-pair.pem`
    - Run command → `ssh -i "key-pair.pem" user-name@ip-address` (use private IP here)
    - You've successfully connected with the private subnet's instance

---

## 5. Internet Gateway (IGW)

An Internet Gateway is a horizontally scaled, highly available, and redundant VPC component that allows communication between your VPC and the internet.

An internet gateway allows resources inside a VPC to communicate with the internet.

**Without IGW:**
- No internet access
- Can't browse websites
- Can't SSH from your laptop to EC2
- Can't install packages using `apt install`

**AWS working flow:**
`Internet → IGW → Route Table → Public Subnet → EC2 Instance`

---

## 6. NAT Gateway (Network Address Translation Gateway)

NAT Gateway allows private subnet instances to access the internet, but prevents the internet from directly accessing them.

**Easy way to picture it:** NAT Gateway is like a one-way mirror — your private server can look out and fetch updates from the internet, but nobody from the internet can look in and reach your private server directly.

NAT gateway is used for communicating with backend, databases, etc., because we can't communicate with backend publicly. It should be private, so we use NAT gateway here.

**AWS architecture:**
`Internet → IGW → Public Subnet → NAT Gateway → Private Subnet → EC2`

---

## 7. VPC Peering

VPC Peering is a networking connection between 2 VPCs that enables you to route traffic between them using private IP addresses.

- VPC peering can only connect 2 VPCs
- For multiple VPC connections, we use **Transit Gateway**

### Steps to Connect 2 VPCs
1. Create 2 VPCs – in different regions (VPC1 & VPC2)
2. Create subnets for both (Subnet1 & Subnet2) → go to actions and enable public IPv4
3. Create 2 IGWs, one for each VPC, and attach to its respective VPC (IGW1 & IGW2)
4. Create route table for both (or use existing route table)
5. Go to edit route → add rule and target (IGW)
6. Go to peering connections → create peering connection
   - Add requester = VPC1 – select region – add accepter = VPC2
7. Launch 2 EC2 instances (one in each VPC)
8. Go to security group of each instance → add all traffic with the other region's VPC IPv4 (for both VPCs)
9. Again go to route table → add the other region's VPC IPv4 → target = peering connection
10. Connect to each EC2 instance and check internet connection using the other instance's private IP

---

## 8. Transit Gateway

AWS Transit Gateway (TGW) is a networking service that connects multiple VPCs and on-premises networks through a single central gateway.

### Why Do We Need Transit Gateway?
- **Without transit gateway:** suppose we have 4 VPCs — we need VPC peering to connect each one to every other one. This creates many connections and becomes difficult to manage.
- **With transit gateway:** each VPC connects only to the transit gateway, instead of connecting to every other VPC individually.

### Benefits
1. Easier management
2. Scalable architecture
3. Centralized routing

---

## 9. Network Interface Controller (NIC) / ENI

### NIC (Network Interface Card)
A hardware component that allows a computer to connect with a network.
- Example: Ethernet port, Wi-Fi card. Without a NIC, there is no internet connection.

A network interface controller (NIC) in AWS is also referred to as an **Elastic Network Interface (ENI)**.

### ENI (Elastic Network Interface)
A virtual network card attached to an EC2 instance. ENI is needed to communicate with the internet, other EC2 instances, and databases. AWS attaches an ENI automatically.

**ENI contains:**
1. Private IP address – used inside VPC
2. Public IP address (optional) – used for internet access
3. MAC address – unique network identifier
4. Security groups – controls who can access the EC2
5. Elastic IP (optional) – permanent public IP

### Types of ENI
1. **Primary ENI** – created automatically when EC2 launches, cannot be detached
2. **Secondary ENI** – additional network interface, can be attached/detached

**Use case:** We use ENIs to separate traffic — for example, application traffic on ENI-1 and management traffic on ENI-2.

### Key Features of NIC
- **Primary Network Interface:** automatically created with every instance and cannot be detached
- **Secondary Network Interface:** can be attached or detached from instances, offering flexibility in multi-network configuration
- **Custom configuration:** security groups, IP addresses, and MAC addresses can be customized

---

## 10. Elastic IP (EIP)

An Elastic IP is a static IPv4 address designed for dynamic cloud computing. You can associate an EIP with your instance or ENI to allow external internet access.

### Key Features
- **Static:** remains unchanged unless manually released
- **Reassigning:** can be reassigned between instances in your account
- **One free IP:** AWS provides one Elastic IP per account without cost, if it is associated with a running instance

---

## 11. Placement Groups

AWS placement groups are logical groupings of instances that allow applications to meet specific performance and redundancy requirements.

### Types of Placement Groups

**1. Cluster Placement Group**
- Instances are placed close together within a single Availability Zone
- High throughput and low latency
- Ideal for HPC (High Performance Computing) and big data workloads

**2. Spread Placement Group**
- Instances are placed across different hardware within an Availability Zone
- Increases fault tolerance
- Ideal for small, critical workloads

**3. Partition Placement Group**
- Instances are divided into logical partitions
- Each partition is isolated from others
- Used for large distributed and replicated workloads such as HDFS, HBase, and Cassandra

---

## 12. Security Group vs NACL

Security Group is a **stateful** firewall attached to EC2 instances, while NACL is a **stateless** firewall attached to subnets that supports both allow and deny rules.

### Security Group
A virtual firewall attached to an EC2 instance. It controls traffic entering and leaving the instance.
- Operates at the instance level
- Example: EC2 → security group
- **Stateful:** automatically allows responses to inbound traffic
  - Example: Laptop → SSH request → EC2. Security group allows port 22. AWS automatically allows the return traffic — you don't need another rule. This is called "stateful."
- Only supports allow rules

### NACL (Network Access Control List)
A firewall attached to a subnet.
- Example: Subnet → NACL → EC2. NACL protects the entire subnet. If a subnet contains 3 EC2 instances, 1 NACL can protect all of them.
- Acts as a firewall for controlling traffic in and out of one or more subnets
- Operates at the subnet level
- **Stateless:** rules need to be explicitly defined for both inbound and outbound traffic
  - Example: NACL is stateless — suppose you allow inbound port 22, AWS does not automatically allow the response traffic. You must separately allow outbound port 22. This is called "stateless."
- Supports rules by rule number, with allow and deny actions

### Comparison

| Feature | Security Group | NACL |
|---|---|---|
| Level | Instance level | Subnet level |
| Acts as | Firewall | Firewall |
| State | Stateful | Stateless |
| Allow rules | Yes | Yes |
| Deny rules | No | Yes |
| Applied to | EC2 | Subnet |
| Return traffic | Automatic | Manual rule required |
| Complexity | Easy | More complex |
| Default behavior | Denies all traffic by default | Allows all traffic by default |

---

## 13. Load Balancer

### Steps to Create a Load Balancer
1. Launch an EC2 instance
2. Install nginx and apache2 server on it
3. Create a target group – go to target option and click "create target"
4. No need to configure a lot – just type the target name
5. Select instances – select the pending instance
6. Go to load balancer → select ALB → click "create" → type name → select AZs → click "create load balancer"
7. Finally, after creation, copy the DNS address and paste it in the browser – you will see your web server

### What is a Load Balancer?
A load balancer in AWS is a service that automatically distributes incoming application traffic across multiple targets, such as Amazon EC2 instances, containers, and IP addresses.

**Easy way to picture it:** A load balancer works like a traffic cop at a busy intersection — it makes sure no single server gets overwhelmed by directing traffic evenly (or smartly) across all available servers.

It acts as a traffic cop, ensuring no single resource is overwhelmed, thereby improving application reliability. Load balancers are designed to handle varying loads of application traffic while automatically scaling up or down based on demand.

> AWS offers **Elastic Load Balancing (ELB)**. By default, load balancers follow the **round-robin** algorithm.

### Types of Load Balancer Algorithms (Interview Question)

1. **Round Robin Algorithm** – requests are distributed one by one, equally (evenly) to all servers.
   - Example: If 10 requests come from clients for 5 servers, each server gets 2 requests each.
2. **Weighted Round Robin Algorithm** – some servers are stronger than others, meaning they have more capacity to handle more traffic. Requests are sent based on capacity.
   - Example: If server 1 has more capacity, it handles 100 requests while other servers handle fewer requests.
3. **Least Connection Algorithm** – requests go to the server having the fewest active connections. The most available server processes the request.
   - Example: If server 1 has more connections/users/traffic and another server has less, the request goes toward the server with less traffic.
4. **IP Hash Algorithm** – load balancer uses the client's IP address; the same user always reaches the same server. The request goes to the server where it was processed earlier.
5. **Least Response Time Algorithm** – traffic goes to the server responding fastest.
   - Example: EC2-1 = 50ms, EC2-2 = 10ms → request goes towards EC2-2.

### Types of Load Balancers

**1. ALB – Application Load Balancer (L7 LB)**
- Works on HTTP, HTTPS protocol
- Cannot handle millions of requests
- Operates at the application layer (Layer 7 of the OSI model)
- Supports advanced request routing, based on URL, hostname, query string, or headers
- Features include WebSocket support, SSL termination, and integration with AWS Web Application Firewall (WAF)
- Example: `amazon.com/login` → goes to login server; `amazon.com/payment` → goes to payment server

**2. NLB – Network Load Balancer (L4 LB)**
- Works on TCP, UDP & TLS traffic protocol
- Operates at the transport layer (Layer 4 of OSI model)
- Best for high-performance use cases that require extremely low latency
- Provides a static IP address and preserves the source IP of the client

**3. GLB – Gateway Load Balancer (L3 LB)**
- Works on IP, routing
- Operates at Layer 3 (network layer) of OSI model
- Designed to deploy, scale, and manage third-party virtual appliances such as firewalls, intrusion detection, and prevention systems

---

## 14. OSI Model (Open System Interconnection)

The Open Systems Interconnection (OSI) model is a conceptual framework created by the ISO to standardize how different computer systems communicate across a network. It divides communication into 7 distinct layers, allowing developers and network engineers to isolate, troubleshoot, and design interoperable hardware and software.

### The 7 Layers (Highest to Lowest)

**Upper Layers (Software-Focused)**
- **Layer 7 – Application Layer:** The layer closest to the end-user. It allows software applications (like web browsers or email clients) to interact with the network. Examples: HTTP, FTP, SMTP.
- **Layer 6 – Presentation Layer:** Acts as the network's translator. It formats, encrypts, and compresses data so the receiving application can correctly understand it.
- **Layer 5 – Session Layer:** Manages communication sessions (the opening, closing, and dialogue of channels) between two devices.

**Lower Layers (Hardware & Data-Focused)**
- **Layer 4 – Transport Layer:** Ensures end-to-end delivery of data by breaking it into chunks (segments), managing flow control, and handling error recovery. Examples: TCP, UDP.
- **Layer 3 – Network Layer:** Handles routing and logical addressing (IP addresses) to send packets across different networks. Example: Routers.
- **Layer 2 – Data Link Layer:** Facilitates data transfer between devices on the same local network. It organizes bits into "frames" and uses MAC addresses for hardware-level identification. Example: Switches.
- **Layer 1 – Physical Layer:** The foundational hardware layer. It transmits raw, unstructured bitstreams (0s and 1s) across a physical medium (like Ethernet cables or Wi-Fi radio waves). Examples: Hubs, cables.

### ALB vs NLB Comparison

| Feature | ALB | NLB |
|---|---|---|
| OSI Layer | Layer 7 (Application layer) | Layer 4 (Transport layer) |
| Traffic Type | HTTP, HTTPS | TCP, UDP, TLS |
| Routing | Content-based (URL, headers, etc.) | Connection-based |
| Performance | Optimized for web applications | High throughput and low latency |
| Source IP Preservation | Not preserved (uses load balancer IP) | Preserved |
| Use Case | Web application, microservices | Gaming, real-time communication |
| Static IP Support | No | Yes |
| WebSocket Support | Yes | No |

---

## 15. Monolithic vs Microservices

### Monolithic (Single Programming Language)
Everything is one big application.
- Example: Login – Payment – Orders – Users = one single application
- If one module fails, the whole app may fail
- Scaling is difficult

### Microservices (Multiple Programming Languages Can Be Used)
The application is split into small, independent services.
- Example: Login service – Payment service – Order service – User service — each runs independently

**Benefits:**
- Easy scaling
- Easier deployment
- Better fault isolation

---

## 16. Load Balancer Troubleshooting

### Why is an Instance Unhealthy? (2 Possible Reasons)
1. Security groups are not configured properly
2. Traffic route path may not be clear

### What is Connection Draining?
Connection draining in AWS is an Elastic Load Balancing (ELB) feature that ensures user requests already in progress are completed before an instance is taken out of service.

**In simple words:** It's like closing a shop's doors for the day but still letting the customers already inside finish paying at the counter before you switch off the lights.

- It allows existing connections to complete before removing an instance from service
- It stops routing new requests to deregistering or unhealthy instances, allowing existing transactions to finish, preventing downtime or disruption

---

## 17. Common HTTP Error Codes (Homework)

| Code | Meaning | Explanation |
|---|---|---|
| 404 | Not Found | The page does not exist |
| 403 | Forbidden | Access denied — the user doesn't have permission |
| 500 | Internal Server Error | Application problem — server received the request but the application failed |
| 502 | Bad Gateway | Load balancer cannot communicate with the backend server. Common causes: application crashed, wrong port, service stopped |
| 503 | Service Unavailable | No healthy servers available (all EC2 instances unhealthy) |
| 504 | Gateway Timeout | Backend server is too slow to respond |