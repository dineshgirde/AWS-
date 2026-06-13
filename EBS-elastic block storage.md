# 💽 AWS EBS (Elastic Block Store)

## 📚 Complete EBS Guide (Beginner → Intermediate → Practical)
### ⚡ Block Storage Service in AWS

---

### 🔹 What is EBS?
Amazon EBS (Elastic Block Store) is a block-level storage service used with EC2 instances.

**👉 It helps you:**
* Store operating systems
* Store application data
* Persist data after EC2 stop/start
* Provide high-performance storage

---

### 🔹 Why EBS is Needed?
* Persistent storage for EC2
* Faster disk performance
* Data backup with snapshots
* Reliable storage for applications

---

### 🔹 Key Features
* Persistent storage
* High availability
* Low latency
* Snapshot support
* Encryption support
* Different volume types

---

### 🔹 How EBS Works
1. Create EBS volume
2. Attach volume to EC2
3. Format and mount disk
4. Store data persistently

---

### 🔥 EBS Architecture

```text
EC2 Instance
     |
Amazon EBS Volume
```

---

### 🔥 EBS vs EFS vs S3

| Feature | EBS | EFS | S3 |
| :--- | :--- | :--- | :--- |
| **Type** | Block Storage | File Storage | Object Storage |
| **Attached To** | Single EC2 | Multiple EC2 | Access via API |
| **Mount Multiple Instances** | No | Yes | No |
| **Protocol** | Block Device | NFS | HTTP/API |
| **Use Case** | OS & Database | Shared Files | Backup & Static Files |

---

### 🔥 EBS Volume Types

#### 🔹 General Purpose SSD (gp2 / gp3)
* **Best for:** Boot volumes, General applications
* **Features:** Balanced performance and cost

#### 🔹 Provisioned IOPS SSD (io1 / io2)
* **Best for:** Databases, Critical applications
* **Features:** High IOPS performance

#### 🔹 Throughput Optimized HDD (st1)
* **Best for:** Big data, Log processing

#### 🔹 Cold HDD (sc1)
* **Best for:** Infrequent access, Archival workloads

---

### 🔥 Create EBS Volume Using AWS Console
1. Open EC2 Dashboard
2. Click Volumes
3. Create Volume
4. Select size and type
5. Choose Availability Zone
6. Create and attach volume

---

### 🔥 Create EBS Volume Using AWS CLI

#### Create Volume
```bash
aws ec2 create-volume \
--availability-zone us-east-1a \
--size 10 \
--volume-type gp3
```

#### Attach Volume
```bash
aws ec2 attach-volume \
--volume-id vol-12345678 \
--instance-id i-12345678 \
--device /dev/xvdf
```

---

### 🔥 Linux Mount Commands

#### Check Attached Disk
```bash
lsblk
```

#### Format EBS Volume
```bash
sudo mkfs -t ext4 /dev/xvdf
```

#### Create Mount Directory
```bash
sudo mkdir /data
```

#### Mount EBS Volume
```bash
sudo mount /dev/xvdf /data
```
--- 
### 🔥 Permanent Mount
Edit `/etc/fstab` and add:
```text
/dev/xvdf /data ext4 defaults,nofail 0 2
```

---

### 🔥 EBS Snapshots
> **Snapshot** = Backup of EBS volume stored in S3 internally.

**Benefits:**
* Backup
* Disaster recovery
* Restore storage

#### Create Snapshot
```bash
aws ec2 create-snapshot \
--volume-id vol-12345678 \
--description "My Backup"
```

#### Restore Volume from Snapshot
```bash
aws ec2 create-volume \
--snapshot-id snap-12345678 \
--availability-zone us-east-1a
```

---

### 🔥 Encryption in EBS
* **Supports:** Encryption at rest
* **Uses:** AWS KMS
* **Benefits:** Secure storage

---

### 🔥 Resize EBS Volume
*Increase volume size without data loss:*
```bash
aws ec2 modify-volume \
--volume-id vol-12345678 \
--size 20
```

---

### 🔥 Volume Management Configuration

#### 🔹 Delete on Termination
Controls whether EBS volume deletes when EC2 terminates.
* **Options:** Enabled / Disabled

#### 🔹 Root Volume
Main operating system disk attached to EC2.
* *Examples:* Ubuntu root disk, Amazon Linux root disk

#### 🔹 Additional Volumes
Extra storage attached to EC2.
* *Used for:* Databases, Application data, Logs

---

### 🔥 Monitoring with CloudWatch
Monitor metrics:
* Read/write operations
* Volume queue length
* Throughput
* IOPS

---

### 🔥 High Availability & Advanced Features

#### 🔹 High Availability
* EBS volume exists inside a **Single Availability Zone**.
* For backup: Use snapshots.

#### 🔹 Multi-Attach Feature
* Supported with **io1/io2** volumes.
* Allows **Multiple EC2 instances** to access the same volume.

---

### 🔥 Real Use Cases
* EC2 operating system storage
* Database storage
* Application storage
* Boot volumes

---

### ⚠️ Common Mistakes
* Forgetting snapshots
* Wrong Availability Zone
* Not mounting volume properly
* Deleting important EBS volume accidentally

---

### 🔒 Best Practices
* Take regular snapshots
* Enable encryption
* Use gp3 for better performance
* Monitor storage metrics
* Separate OS and application data volumes

---

### 🏆 Interview Questions
1. What is EBS?
2. Difference between EBS and EFS?
3. What are EBS volume types?
4. What is snapshot?
5. Can EBS attach to multiple instances?
6. What happens to EBS after EC2 stop/start?

---

### 🧪 Troubleshooting Commands

* **List Disks**
  ```bash
  lsblk
  ```
* **Check Mounted Volumes**
  ```bash
  df -h
  ```
* **View File System UUID**
  ```bash
  sudo blkid
  ```
* **Describe EBS Volumes**
  ```bash
  aws ec2 describe-volumes
  ```
* **Describe Snapshots**
  ```bash
  aws ec2 describe-snapshots
  ```

---

### 💡 Quick Revision
* **EBS** = Block Storage
* **Snapshot** = Backup
* **gp3** = General SSD
* **io1/io2** = High Performance SSD
* **Root Volume** = OS Disk
* **AZ** = Single Zone Storage

---

### 🎯 Final Concept
> **Amazon EBS** is a high-performance persistent block storage service in AWS that provides reliable storage for EC2 instances, supporting operating systems, databases, and enterprise applications with backup and encryption capabilities.
