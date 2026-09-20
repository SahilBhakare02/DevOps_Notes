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
