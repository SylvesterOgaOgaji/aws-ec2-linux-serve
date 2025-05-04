# AWS EC2 Implementation Guide

## Table of Contents
1. [Account Setup](#1-account-setup)  
2. [EC2 Instance Creation](#2-ec2-instance-creation)  
3. [Post-Launch Configuration](#3-post-launch-configuration)  
4. [System Maintenance](#4-system-maintenance)  
5. [Implementation Summary](#5-implementation-summary)  

---

## 1. Account Setup

### 1.1 Accessing AWS Free Tier
![Free Tier Landing](./img/1.%20AWS%20landing%20page.png)
1. Navigate to `aws.amazon.com/free`
2. Click "Sign In to the Console"
3. Key elements:
   - "Gain free, hands-on experience" header
   - AWS Certification promotions
   - Free Tier eligibility details

### 1.2 Authentication Process
#### User Type Selection
![Login Type](./img/2.%20login%20page.png)
- Selected: **Root user**
- Email: `ogaoogil21@gmail.com`

#### Password Entry
![Password Screen](./img/2a.%20login%20password.png)
- Completed password field
- Security notice: "Forgot password?" link

### 1.3 Console Navigation
![AWS Dashboard](./img/3.%20AWS%20welcome%20page.png)
- Account ID: `7392-7543-8151`
- Active Region: **US East (N. Virginia)**
- Key sections:
  - Getting Started
  - Training & Certification
  - Health Dashboard

---

## 2. EC2 Instance Creation

### 2.1 Service Access
![EC2 Search](./img/4.%20Search%20for%20ec2.png)
1. Console search for "ec2"
2. Select: **EC2 Virtual Servers in the Cloud**

### 2.2 Instance Launch Interface
![Empty Instance List](./img/5.%20instance.png)
- Status: **No instances** in region
- Action: Click "Launch instances"

### 2.3 Instance Configuration
#### AMI Selection
![OS Selection](./img/7.%20create%20instance.png)
- **Selected AMI**: Ubuntu Server 24.04 LTS (HVM)
- AMI ID: `ami-084568db438326d4d`
- Virtualization: `hvm`
- Root Device: `ebs`

#### Instance Specifications
![Type Selection](./img/8.%20create%20a%20new%20key.png)
- **Type**: t2.micro
- Specs:
  - vCPUs: 1
  - Memory: 1 GiB
  - Pricing: $0.0116/hr (Linux)

#### Storage Configuration
![Storage Setup](./img/10%20configure%20storage.png)
- Volume: 16 GiB gp3
- Security Note: "Rules with source 0.0.0.0/0 allow all IPs"

#### Key Pair Creation
![Key Configuration](./img/9.%20creating%20on%20progress.png)
- **Key Name**: `key`
- Type: RSA
- Format: .pem
- Warning: "Store private key securely"

### 2.4 Launch Process
![Launch Progress](./img/11.%20instance%20lunching.png)
- Status: 80% complete
- Message: "Do not close your browser"

### 2.5 Launch Completion
![Launch Success](./img/12.%20successful.png)
**Next Steps:**
- Create billing alerts
- Enable detailed monitoring
- Configure security groups

---

## 3. Post-Launch Configuration

### 3.1 Key Verification
![Key Location](./img/13.%20located%20key%20dot%20pem.png)

```bash
$ ls -l ~/Downloads
-rw-r--r-- 1 Sylvester 197121 1675 May  2 13:00 key.pem
```

### 3.2 Instance Details
![Public IP](./img/14.%20fatching%20public%20Ip.png)

Live Configuration:
- Field	Value
- Name	Linux_Server
- Public IP	34.230.44.226
- AZ	us-east-1b
- Type	t2.micro

### 3.3 SSH Connection
![Terminal Access](./img/15.%20connected%20to%20the%20AWS.png)
```bash
$ ssh -i "C:\Users\Sylvester\Downloads\key.pem" ubuntu@34.230.44.226
```
Initial System Status:
- Metric	Value
- Load	0.08
- Disk Usage	11.6%
- Memory	20%

## 3. System Maintenance
### 4.1 Package Updates
![Update Process](./img/16%20update.png)
```bash
$ sudo apt update
82 packages can be upgraded
38 security updates available
```

### 4.2 Package Management
Installation
![Tree Installation](./img/17.%20tree.png)
```bash
$ sudo apt install tree
Setting up tree (2.1.1-2ubuntu3)...
```

Verification
![Directory Check](./img/18%20confirm%20the%20installation.png)
```bash
$ tree ~/Downloads
0 directories, 0 files
```

Package Removal
![Package Cleanup](./img/20.%20package%20removed.png)
```bash
$ sudo apt remove tree
111 kB disk space freed
```

### 4.3 System Upgrades
![System Upgrade](./img/19.%20Upgrade%20successful.png)
```bash
$ sudo apt upgrade
The following NEW packages will be installed:
linux-aws-headers=6.8.0-1028
linux-aws-tools=6.8.0-1028