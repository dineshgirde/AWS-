# 🖥️ AWS EC2 (Elastic Compute Cloud)

## 📚 Complete EC2 Guide (Beginner → Intermediate → Practical)
### ⚡ Virtual Server Service in AWS

---

### 🔹 What is EC2?
Amazon EC2 (Elastic Compute Cloud) is a web service that provides resizable virtual servers in the cloud.

**👉 It helps you:**
* Run applications
* Host websites
* Deploy servers
* Scale infrastructure easily

---

### 🔹 Why EC2 is Needed?
* On-demand virtual machines
* Flexible scaling
* Cost-effective infrastructure
* Full control over servers

---

### 🔹 Core Components

#### 🔹 AMI (Amazon Machine Image)
Template used to launch EC2 instances.

**Contains:**
* Operating System
* Application software
* Configuration

**Examples:**
* Ubuntu
* Amazon Linux
* Red Hat

#### 🔹 Instance Type
**Defines:**
* CPU
* RAM
* Storage
* Network performance

**Examples:**
* t2.micro
* t3.medium
* m5.large

#### 🔹 Key Pair
Used for secure SSH login.

**Contains:**
* Public key
* Private key (.pem file)

#### 🔹 Security Group
Acts like a virtual firewall.

**Controls:**
* Inbound traffic
* Outbound traffic

**Example:**
* Allow SSH → Port 22
* Allow HTTP → Port 80

#### 🔹 EBS (Elastic Block Store)
Persistent storage attached to EC2.

**Features:**
* SSD/HDD storage
* Snapshot support
* Data persistence

#### 🔹 Elastic IP
Static public IP address.

**Used when:**
* Public IP should not change

---

### 🔥 EC2 Instance Lifecycle
* Launch
* Running
* Stop
* Start
* Reboot
* Terminate

---

### 🔥 Launch EC2 Instance (Console)
1. Open EC2 Dashboard
2. Click Launch Instance
3. Choose AMI
4. Select instance type
5. Configure instance
6. Add storage
7. Configure security group
8. Create/select key pair
9. Launch instance

---

### 🔥 Launch EC2 Using AWS CLI
```bash
aws ec2 run-instances \
--image-id ami-12345678 \
--count 1 \
--instance-type t2.micro \
--key-name my-key \
--security-group-ids sg-12345678 \
--subnet-id subnet-12345678
```

---

### 🔥 Connect to EC2

#### Linux/macOS SSH
```bash
ssh -i my-key.pem ubuntu@public-ip
```

#### Change Permission of Key
```bash
chmod 400 my-key.pem
```

---

### 🔥 Common Ports

| Service | Port |
| :--- | :--- |
| SSH | 22 |
| HTTP | 80 |
| HTTPS | 443 |
| MySQL | 3306 |
| Jenkins | 8080 |

---

### 🔥 EC2 Storage Types

* **🔹 EBS:** Persistent block storage (Most commonly used)
* **🔹 Instance Store:** Temporary storage (Data lost after stop/terminate)

---

### 🔥 EC2 Purchasing Options

* **🔹 On-Demand:** Pay per use, Flexible
* **🔹 Reserved Instances:** Long-term commitment, Lower cost
* **🔹 Spot Instances:** Cheapest option, Can terminate anytime
* **🔹 Dedicated Hosts:** Physical server dedicated to one customer

---

### 🔥 Auto Scaling
Automatically increases/decreases instances based on load.

**Benefits:**
* High availability
* Cost optimization
* Better performance

---

### 🔥 Load Balancer Integration
Used to distribute traffic across EC2 instances.

**Types:**
* Application Load Balancer (ALB)
* Network Load Balancer (NLB)
* Classic Load Balancer (CLB)

---

### 🔥 EC2 Monitoring
**Use:**
* CloudWatch Metrics
* CloudWatch Alarms
* CloudTrail Logs

**Metrics:**
* CPU Utilization
* Network In/Out
* Disk Usage

---

### 🔥 Security Best Practices
* Use Security Groups properly
* Disable root login
* Use IAM roles
* Enable MFA
* Keep software updated

---

### 🔥 IAM Role for EC2
Attach IAM role to EC2 instance for secure AWS access.

**Example:**
* EC2 accessing S3 bucket

---

### 🔥 Create AMI from Instance
1. Select EC2 instance
2. Actions
3. Image and Templates
4. Create Image

**Used for:**
* Backup
* Cloning
* Auto Scaling

---

### 🔥 EBS Snapshot
Used for backup of EBS volumes.

**Create Snapshot:**
```bash
aws ec2 create-snapshot \
--volume-id vol-12345678 \
--description "Backup Snapshot"
```

---

### 🔥 User Data Script
Used to automate server setup during launch.

**Example:**
```bash
#!/bin/bash
sudo apt update -y
sudo apt install nginx -y
sudo systemctl start nginx
```

---

### 🔥 Elastic IP Commands

#### Allocate Elastic IP:
```bash
aws ec2 allocate-address
```

#### Associate Elastic IP:
```bash
aws ec2 associate-address \
--instance-id i-12345678 \
--allocation-id eipalloc-12345678
```

---

### 🔥 Practical Commands

#### List Instances
```bash
aws ec2 describe-instances
```

#### Start Instance
```bash
aws ec2 start-instances --instance-ids i-12345678
```

#### Stop Instance
```bash
aws ec2 stop-instances --instance-ids i-12345678
```

#### Reboot Instance
```bash
aws ec2 reboot-instances --instance-ids i-12345678
```

#### Terminate Instance
```bash
aws ec2 terminate-instances --instance-ids i-12345678
```

---

### 🔄 Real Use Cases
* Hosting websites
* Running Jenkins server
* Deploying Kubernetes worker nodes
* Running databases
* Hosting applications

---

### ⚠️ Common Mistakes
* Opening SSH to everyone (0.0.0.0/0)
* Forgetting backups
* Not using security groups properly
* Using root user

---

### 🔒 Best Practices
* Use least privilege access
* Enable monitoring
* Use Auto Scaling
* Take regular snapshots
* Use IAM roles instead of access keys

---

### 🏆 Interview Questions
1. What is EC2?
2. Difference between Security Group and NACL?
3. Difference between EBS and Instance Store?
4. What is AMI?
5. What is Auto Scaling?
6. What is Elastic IP?

---

### 🧪 Troubleshooting Commands

#### Check Disk Usage
```bash
df -h
```

#### Check Memory Usage
```bash
free -m
```

#### Check Running Processes
```bash
top
```

#### Check Open Ports
```bash
netstat -tulnp
```

#### Check Instance Logs
```bash
sudo journalctl -xe
```

---

### 💡 Quick Revision
* **EC2** = Virtual Server
* **AMI** = OS Template
* **EBS** = Storage
* **Security Group** = Firewall
* **Key Pair** = SSH Login
* **Elastic IP** = Static IP

---

### 🎯 Final Concept
> **Amazon EC2** is a scalable cloud computing service that provides secure and resizable virtual servers used for hosting applications, websites, databases, and enterprise workloads in AWS.
