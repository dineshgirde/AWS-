# 🗄️ AWS RDS (Relational Database Service)

## 📚 Complete RDS Guide (Beginner → Intermediate → Practical)
### ⚡ Managed Relational Database Service in AWS

---

## 🔹 What is RDS?
Amazon RDS (Relational Database Service) is a fully managed database service in AWS.

**👉 It helps you:**
* Run relational databases easily
* Automate backups
* Handle scaling
* Improve availability
* Reduce manual database management

---

## 🔹 Why RDS is Needed?
* No manual database maintenance
* Automated backups
* High availability
* Easy scaling
* Secure database management

---

## 🔹 Supported Database Engines
RDS supports:
* MySQL
* PostgreSQL
* MariaDB
* Oracle
* Microsoft SQL Server
* Amazon Aurora

---

## 🔹 Key Features
* Fully managed service
* Automated backups
* Multi-AZ deployment
* Read replicas
* Monitoring with CloudWatch
* Automatic patching

---

## 🔹 How RDS Works
1. Create database instance
2. Configure storage and security
3. Connect application to RDS endpoint
4. AWS manages maintenance and backups

---

## 🔥 RDS Architecture

```text
Application
     |
RDS Endpoint
     |
Database Instance
```

---

## 🔥 DB Instance
A database server running in AWS.

**Contains:**
* CPU
* Memory
* Storage
* Database engine

---

## 🔥 Create RDS Using AWS Console
1. Open RDS Dashboard
2. Click Create Database
3. Select database engine
4. Configure instance settings
5. Set username/password
6. Configure storage and security
7. Launch database

---

## 🔥 Create RDS Using AWS CLI

#### Create MySQL RDS Instance
```bash
aws rds create-db-instance \
--db-instance-identifier mydb \
--db-instance-class db.t3.micro \
--engine mysql \
--master-username admin \
--master-user-password MyPassword123 \
--allocated-storage 20
```

---

## 🔥 Connect to MySQL RDS
```bash
mysql -h mydb.xxxxxx.us-east-1.rds.amazonaws.com \
-u admin \
-p
```

---

## 🔥 Multi-AZ Deployment
Creates standby database in another Availability Zone.

**Benefits:**
* High availability
* Automatic failover

---

## 🔥 Read Replicas
**Used to:**
* Improve read performance

**Benefits:**
* Load balancing for read queries

---

## 🔥 Storage Types

* **🔹 General Purpose SSD (gp2/gp3):** Best for General applications
* **🔹 Provisioned IOPS SSD:** Best for High-performance databases
* **🔹 Magnetic Storage:** Older and low-cost storage type.

---

## 🔥 Automated Backups
AWS automatically creates:
* Daily backups
* Transaction logs

**Benefits:**
* Point-in-time recovery

---

## 🔥 Manual Snapshots
User-created backups.

**Benefits:**
* Long-term backup storage

### Create Snapshot
```bash
aws rds create-db-snapshot \
--db-instance-identifier mydb \
--db-snapshot-identifier mydb-snapshot
```

### Restore from Snapshot
```bash
aws rds restore-db-instance-from-db-snapshot \
--db-instance-identifier restored-db \
--db-snapshot-identifier mydb-snapshot
```

---

## 🔥 Security in RDS
**Uses:**
* Security Groups
* IAM Authentication
* Encryption

### 🔹 Encryption
* **Supports:** Encryption at rest, Encryption in transit (SSL/TLS)
* **Uses:** AWS KMS

---

## 🔥 RDS Security Group
Allow database ports:

| Database | Port |
| :--- | :--- |
| MySQL | 3306 |
| PostgreSQL | 5432 |
| SQL Server | 1433 |
| Oracle | 1521 |

---

## 🔥 Monitoring with CloudWatch
**Monitor:**
* CPU usage
* Free storage
* Database connections
* Read/write latency

---

## 🔥 Maintenance Window
AWS performs:
* Patching
* Updates
* Maintenance

*During scheduled maintenance window.*

---

## 🔥 Parameter Groups
Used to customize **Database settings**.

**Examples:**
* `max_connections`
* query cache

---

## 🔥 Option Groups
Used for **Additional database features**.

**Examples:**
* Oracle options
* SQL Server features

---

## 🔥 Scaling in RDS

#### 🔹 Vertical Scaling
**Increase:**
* CPU
* RAM
* Storage

### 🔹 Storage Auto Scaling
Automatically increases storage when needed.

---

## 🔥 High Availability
* **Achieved using:** Multi-AZ deployment

---

## 🔥 RDS vs EC2 Database

| Feature | RDS | Database on EC2 |
| :--- | :--- | :--- |
| **Managed Service** | Yes | No |
| **Automated Backups** | Yes | Manual |
| **Patching** | Automatic | Manual |
| **Scaling** | Easy | Manual |
| **High Availability** | Built-in | Manual |

---

## 🔥 Real Use Cases
* Web applications
* E-commerce applications
* ERP systems
* Banking applications

---

## ⚠️ Common Mistakes
* Publicly exposing database
* No backups configured
* Wrong security group rules
* Using small storage size

---

## 🔒 Best Practices
* Enable Multi-AZ
* Use automated backups
* Enable encryption
* Restrict public access
* Monitor database metrics

---

## 🏆 Interview Questions
1. What is RDS?
2. Difference between RDS and EC2 database?
3. What is Multi-AZ?
4. What are read replicas?
5. What is automated backup?
6. Which databases are supported in RDS?

---

## 🧪 Troubleshooting Commands

#### Describe RDS Instances
```bash
aws rds describe-db-instances
```

#### Describe Snapshots
```bash
aws rds describe-db-snapshots
```

#### Reboot RDS Instance
```bash
aws rds reboot-db-instance \
--db-instance-identifier mydb
```

#### Check Database Connectivity
```bash
telnet mydb.xxxxxx.us-east-1.rds.amazonaws.com 3306
```

---

## 💡 Quick Revision
* **RDS** = Managed Database
* **Multi-AZ** = High Availability
* **Read Replica** = Read Scaling
* **Snapshot** = Backup
* **3306** = MySQL Port
* **KMS** = Encryption Service

---

### 🎯 Final Concept
> **Amazon RDS** is a fully managed relational database service in AWS that simplifies database administration by providing automated backups, scaling, monitoring, security, and high availability for enterprise applications.
