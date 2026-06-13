# 📂 AWS EFS (Elastic File System)

## 📚 Complete EFS Guide (Beginner → Intermediate → Practical)
### ⚡ Fully Managed File Storage Service in AWS

---

### 🔹 What is EFS?
Amazon EFS (Elastic File System) is a fully managed scalable file storage service for Linux-based workloads in AWS.

**👉 It helps you:**
* Share files across multiple servers
* Store application data
* Scale storage automatically
* Provide high availability

---

### 🔹 Why EFS is Needed?
* Shared storage for multiple EC2 instances
* Automatic scaling
* Highly available storage
* Centralized file system

---

### 🔹 Key Features
* Fully managed
* Scalable storage
* Shared file system
* Multi-AZ availability
* NFS protocol support
* Pay only for used storage

---

### 🔹 How EFS Works
1. Create EFS file system
2. Mount EFS on EC2 instances
3. Read/write files from multiple servers simultaneously

---

### 🔥 EFS Architecture

```text
        Amazon EFS
             |
--------------------------------

|              |              |
EC2-1         EC2-2         EC2-3
```
*All instances can access the same files.*

---

### 🔥 EFS vs EBS vs S3

| Feature | EFS | EBS | S3 |
| :--- | :--- | :--- | :--- |
| **Type** | File Storage | Block Storage | Object Storage |
| **Shared Access** | Yes | No | Yes |
| **Mount on Multiple EC2** | Yes | No | No |
| **Scaling** | Automatic | Manual | Automatic |
| **Protocol** | NFS | Attached Disk | API/HTTP |
| **Use Case** | OS & Database | Shared Files | Backup & Static Files |

---

### 🔥 Storage Classes

* **🔹 Standard:** Frequently accessed files, Low latency
* **🔹 Infrequent Access (IA):** Lower cost, Rarely accessed files
* **🔹 Archive:** Lowest cost, Long-term storage

---

### 🔥 Performance Modes

* **🔹 General Purpose:** Best for Web servers, CMS, Small applications
* **🔹 Max I/O:** Best for Big data, High throughput workloads

---

### 🔥 Throughput Modes

* **🔹 Bursting Throughput:** Performance depends on storage size.
* **🔹 Provisioned Throughput:** Manually define throughput.
* **🔹 Elastic Throughput:** Automatically scales throughput.

---

### 🔥 Create EFS Using AWS Console
1. Open EFS Dashboard
2. Click Create File System
3. Select VPC
4. Configure security groups
5. Create EFS

---

### 🔥 Create EFS Using AWS CLI

#### Create File System
```bash
aws efs create-file-system \
--creation-token my-efs
```

#### Create Mount Target
```bash
aws efs create-mount-target \
--file-system-id fs-12345678 \
--subnet-id subnet-12345678 \
--security-groups sg-12345678
```

---

### 🔥 Mount EFS on EC2

#### Install NFS Utilities

**Ubuntu:**
```bash
sudo apt update
sudo apt install nfs-common -y
```

**Amazon Linux:**
```bash
sudo yum install -y amazon-efs-utils
```

#### Create Mount Directory
```bash
sudo mkdir /mnt/efs
```

#### Mount EFS
```bash
sudo mount -t efs fs-12345678:/ /mnt/efs
```

#### Permanent Mount
Add entry in `/etc/fstab`:
```text
fs-12345678:/ /mnt/efs efs defaults,_netdev 0 0
```

---

### 🔥 Security in EFS
**Uses:**
* Security Groups
* IAM Policies
* Encryption

#### 🔹 Encryption
**Supports:**
* Encryption at rest
* Encryption in transit

#### 🔹 EFS Security Group Rules
**Allow:** NFS Port 2049

| Type | Port |
| :--- | :--- |
| NFS | 2049 |

---

### 🔥 Backup and Recovery
* **Supports:** AWS Backup
* **Snapshots via AWS Backup**

---

### 🔥 EFS Lifecycle Management
* Automatically moves files from **Standard → IA**
* **Benefits:** Cost optimization

---

### 🔥 Monitoring with CloudWatch
**Monitor:**
* Throughput
* Connections
* Storage usage
* IOPS

---

### 🔥 High Availability & Integration

#### 🔹 High Availability
* EFS stores data across **Multiple Availability Zones**.
* **Benefits:** Fault tolerance, High durability

#### 🔹 EFS with Kubernetes (EKS)
* **Used as:** Persistent shared storage
* *Example:* Multiple pods sharing same data

#### 🔹 EFS with Auto Scaling
* New EC2 instances can automatically mount same shared storage.
* **Benefits:** Consistent data access

---

### 🔥 Real Use Cases
* Shared web hosting
* Kubernetes persistent storage
* WordPress shared storage
* CI/CD shared workspace

---

### ⚠️ Common Mistakes
* Missing NFS port 2049
* Wrong security group rules
* Mount target missing in subnet
* Using EFS for ultra-low latency database workloads

---

### 🔒 Best Practices
* Enable encryption
* Use lifecycle policies
* Configure proper security groups
* Use EFS for shared workloads only
* Monitor storage usage

---

### 🏆 Interview Questions
1. What is EFS?
2. Difference between EFS and EBS?
3. Which protocol does EFS use?
4. Can multiple EC2 instances use EFS?
5. What is lifecycle management in EFS?
6. Which port is used by EFS?

---

### 🧪 Troubleshooting Commands

* **Check Mounted File Systems**
  ```bash
  df -h
  ```
* **Verify EFS Mount**
  ```bash
  mount | grep efs
  ```
* **Test Connectivity**
  ```bash
  telnet fs-12345678.efs.us-east-1.amazonaws.com 2049
  ```
* **Check Security Group Rules**
  ```bash
  aws ec2 describe-security-groups
  ```

---

### 💡 Quick Revision
* **EFS** = Shared File Storage
* **NFS** = File Sharing Protocol
* **Mount Target** = Access Point in Subnet
* **2049** = NFS Port
* **Shared Access** = Multiple EC2 Instances

---

### 🎯 Final Concept
> **Amazon EFS** is a fully managed, scalable, and highly available shared file storage service in AWS that allows multiple Linux-based EC2 instances and applications to access the same file system simultaneously
