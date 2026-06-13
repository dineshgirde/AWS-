# 🔐 AWS IAM (Identity and Access Management)

## 📚 Complete AWS IAM Guide (Beginner → Intermediate → Practical)
### ⚡ Security and Access Management Service in AWS

---

### 🔹 What is IAM?
AWS IAM (Identity and Access Management) is a service used to securely control access to AWS resources.

**👉 It helps you:**
* Create users and groups
* Manage permissions
* Control access to AWS services
* Improve AWS security

---

### 🔹 Why IAM is Needed?
* Secure AWS environment
* Control user permissions
* Implement least privilege access
* Centralized access management

---

### 🔹 Core Components

#### 🔹 IAM Users
Individual identities for people or applications.

**Each user can have:**
* Password
* Access keys
* Permissions

**Example:**
* DevOps Engineer
* Developer
* Admin User

#### 🔹 IAM Groups
Collection of IAM users.
* *Permissions assigned to group apply to all users inside it*

**Example:**
* Developers Group
* Admin Group
* QA Group

#### 🔹 IAM Roles
Temporary access mechanism.

**Used by:**
* EC2
* Lambda
* Applications
* Cross-account access

#### 🔹 IAM Policies
JSON documents that define permissions.

**Example:**
* Allow S3 access
* Deny EC2 deletion

---

### 🔥 IAM Policy Structure
*Example:*

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListBucket"
      ],
      "Resource": "*"
    }
  ]
}
```

---

### 🔹 Important IAM Concepts

#### 🔹 Authentication
Verifies identity.
* *Example:* Username/password, Access keys

#### 🔹 Authorization
Defines what actions are allowed.
* *Example:* Start EC2, Access S3 bucket

#### 🔹 Least Privilege Principle
* Give only required permissions
* Avoid full admin access unnecessarily

---

### 🔥 IAM Users Management

#### Create IAM User Using Console
1. Open IAM Console
2. Click Users
3. Add User
4. Set username
5. Select access type
6. Attach permissions
7. Create user

#### Create User Using AWS CLI
```bash
aws iam create-user --user-name devuser
```

---

### 🔥 IAM Groups

#### Create IAM Group
```bash
aws iam create-group --group-name Developers
```

#### Add User to Group
```bash
aws iam add-user-to-group \
--user-name devuser \
--group-name Developers
```

---

### 🔥 IAM Policies

#### Create Policy
```bash
aws iam create-policy \
--policy-name S3ReadOnlyPolicy \
--policy-document file://policy.json
```

#### Attach Policy to User
```bash
aws iam attach-user-policy \
--user-name devuser \
--policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

---

### 🔥 IAM Roles

#### Create IAM Role
```bash
aws iam create-role \
--role-name EC2S3AccessRole \
--assume-role-policy-document file://trust-policy.json
```

#### Attach Policy to Role
```bash
aws iam attach-role-policy \
--role-name EC2S3AccessRole \
--policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

---

### 🔥 Access Keys
Used for programmatic access.

**Works with:**
* AWS CLI
* SDK
* Terraform
* Applications

#### Create Access Key
```bash
aws iam create-access-key --user-name devuser
```

---

### 🔥 MFA (Multi-Factor Authentication)
* Adds extra security layer
* Requires OTP/device verification

---

### 🔥 Password Policy
Configure:
* Minimum password length
* Symbols requirement
* Password expiration

---

### 🔥 IAM Best Practices
* Enable MFA
* Use roles instead of access keys when possible
* Rotate access keys regularly
* Avoid root user usage
* Follow least privilege principle

---

### 🔥 Root User
* Main AWS account owner
* Has full permissions

**⚠️ Best Practice:**
* Do not use root user daily
* Enable MFA on root account

---

### 🔥 IAM and AWS Services
IAM integrates with:
* EC2
* S3
* Lambda
* RDS
* CloudWatch
* EKS

---

### 🔄 Real Use Cases
* Giving developers S3 access
* EC2 accessing S3 bucket
* Lambda accessing DynamoDB
* Cross-account AWS access

---

### 🔐 Security Features
* MFA
* IAM Policies
* Temporary Credentials
* Access Analyzer
* CloudTrail Integration

---

### 🔍 Monitoring IAM
**Use:**
* AWS CloudTrail
* IAM Access Analyzer
* CloudWatch Logs

---

### ⚠️ Common Mistakes
* Using root account regularly
* Giving AdministratorAccess to everyone
* Hardcoding access keys
* No MFA enabled

---

### 🔒 Best Practices
* Use IAM groups
* Use roles for EC2/Lambda
* Enable MFA everywhere
* Rotate credentials regularly
* Monitor IAM activity using CloudTrail

---

### 🏆 Interview Questions
1. What is IAM?
2. Difference between IAM user and role?
3. What is IAM policy?
4. What is least privilege principle?
5. What is MFA?
6. Difference between inline and managed policies?

---

### 🧪 Practical Commands

#### List IAM Users
```bash
aws iam list-users
```

#### List IAM Groups
```bash
aws iam list-groups
```

#### List IAM Roles
```bash
aws iam list-roles
```

#### Delete IAM User
```bash
aws iam delete-user --user-name devuser
```

#### Detach Policy
```bash
aws iam detach-user-policy \
--user-name devuser \
--policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

---

### 💡 Quick Revision
* **IAM** = Access Management
* **User** = Individual identity
* **Group** = Collection of users
* **Role** = Temporary permissions
* **Policy** = Permission document
* **MFA** = Extra security layer

---

### 🎯 Final Concept
> **AWS IAM** is a security service used to manage authentication and authorization in AWS by controlling who can access which AWS resources securely and efficiently.
