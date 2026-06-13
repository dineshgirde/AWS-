# 🌐 AWS Route 53

## 📚 Complete Route 53 Guide (Beginner → Intermediate → Practical)
### ⚡ Scalable DNS and Domain Management Service in AWS

---

### 🔹 What is Route 53?
Amazon Route 53 is a highly available and scalable DNS (Domain Name System) web service in AWS.

**👉 It helps you:**
* Register domains
* Manage DNS records
* Route internet traffic
* Perform health checks
* Improve application availability

---

### 🔹 Why Route 53 is Needed?
* Convert domain names into IP addresses
* Route users to applications
* Improve reliability and failover
* Manage DNS easily

---

### 🔹 What is DNS?
DNS (Domain Name System) converts:
* `google.com` → IP Address

*Example:*
* google.com → 142.250.xx.xx

---

### 🔹 Key Features
* Domain registration
* DNS management
* Traffic routing
* Health checks
* Failover support
* Low latency routing

---

### 🔹 How Route 53 Works
1. User enters domain name
2. DNS request goes to Route 53
3. Route 53 returns correct IP address
4. User reaches application/server

---

### 🔥 Route 53 Architecture

```text
User
  |
Route 53
  |
Web Server / Load Balancer / CloudFront
```

---

### 🔥 Hosted Zones
A hosted zone stores DNS records for a domain.

*Example:*
* `example.com`

**Contains:**
* A records
* CNAME records
* MX records

---

### 🔥 Types of Hosted Zones

#### 🔹 Public Hosted Zone
Accessible from internet.
* **Used for:** Public websites

#### 🔹 Private Hosted Zone
Accessible only inside VPC.
* **Used for:** Internal applications

---

### 🔥 DNS Record Types

| Record Type | Purpose |
| :--- | :--- |
| **A** | Maps domain to IPv4 |
| **AAAA** | Maps domain to IPv6 |
| **CNAME** | Alias to another domain |
| **MX** | Mail server records |
| **TXT** | Verification and text records |
| **NS** | Name servers |
| **PTR** | Reverse DNS lookup |

---

### 🔥 A Record Example
`example.com` → 3.110.xx.xx

---

### 🔥 CNAME Example
`://example.com` → `example.com`

---

### 🔥 Create Hosted Zone Using AWS Console
1. Open Route 53 Dashboard
2. Click Hosted Zones
3. Create Hosted Zone
4. Enter domain name
5. Add DNS records

---

### 🔥 Create Hosted Zone Using AWS CLI

```bash
aws route53 create-hosted-zone \
--name example.com \
--caller-reference 12345
```

---

### 🔥 Create DNS Record Using AWS CLI

```bash
aws route53 change-resource-record-sets \
--hosted-zone-id Z123456789 \
--change-batch file://record.json
```

---

### 🔥 Alias Record
AWS-specific DNS feature.

**Used for:**
* ELB
* CloudFront
* S3 Static Website

**Benefits:**
* No extra DNS query charges

---

### 🔥 Routing Policies

* **🔹 Simple Routing:** Single resource routing.
* **🔹 Weighted Routing:** Distributes traffic by percentage.
  * *Example:* 70% → Server A, 30% → Server B
* **🔹 Latency-Based Routing:** Routes users to nearest region.
  * *Benefits:* Faster response time
* **🔹 Failover Routing:** Routes traffic to backup server if primary fails.
* **🔹 Geolocation Routing:** Routes traffic based on user location.
* **🔹 Multi-Value Routing:** Returns multiple healthy IPs.

---

### 🔥 Health Checks
Continuously monitors application/server health.

**Checks:**
* HTTP
* HTTPS
* TCP

*If unhealthy:* Traffic redirected elsewhere

---

### 🔥 Domain Registration
Route 53 can:
* Register domains
* Renew domains
* Transfer domains

*Example:* `example.com`

---

### 🔥 Route 53 Integrations

#### 🔹 Route 53 with ELB
* **Common architecture:** User → Route 53 → Load Balancer → EC2
* **Benefits:** High availability, Traffic distribution

#### 🔹 Route 53 with CloudFront
* **Used to connect:** Custom domain with CDN
* *Example:* `://example.com` → CloudFront

#### 🔹 Route 53 with S3 Static Website
* Can host static websites using: S3 + Route 53
* *Example:* `://example.com`

#### 🔹 Private Hosted Zone Example
* Used for internal DNS inside VPC.
* *Example:* `internal-app.local`

---

### 🔥 Security in Route 53
**Uses:**
* IAM policies
* DNSSEC support

---

### 🔥 DNS Failover
Automatically redirects traffic if server fails.

**Benefits:**
* Better uptime
* Disaster recovery

---

### 🔥 Monitoring with CloudWatch
**Monitor:**
* Health check status
* DNS query metrics

---

### 🔥 Real Use Cases
* Website hosting
* Load balancer routing
* Multi-region applications
* Disaster recovery

---

### ⚠️ Common Mistakes
* Wrong DNS record values
* Incorrect hosted zone selection
* Missing NS records
* Forgetting TTL settings

---

### 🔒 Best Practices
* Use alias records for AWS services
* Configure health checks
* Use failover routing
* Enable monitoring
* Use least privilege IAM policies

---

### 🏆 Interview Questions
1. What is Route 53?
2. What is DNS?
3. Difference between A record and CNAME?
4. What is hosted zone?
5. What are routing policies?
6. What is failover routing?

---

### 🧪 Troubleshooting Commands

#### Check DNS Resolution
```bash
nslookup example.com
```

#### Check DNS Records
```bash
dig example.com
```

#### Describe Hosted Zones
```bash
aws route53 list-hosted-zones
```

#### Check Health Checks
```bash
aws route53 list-health-checks
```

---

### 💡 Quick Revision
* **Route 53** = DNS Service
* **Hosted Zone** = DNS Record Container
* **A Record** = Domain → IP
* **CNAME** = Domain Alias
* **TTL** = DNS Cache Time
* **Health Check** = Server Monitoring

---

### 🎯 Final Concept
> **Amazon Route 53** is a highly scalable and reliable DNS service in AWS that helps route internet traffic, manage domains, perform health checks, and improve application availability using intelligent routing policies.
