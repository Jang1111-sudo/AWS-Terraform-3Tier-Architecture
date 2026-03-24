# AWS-Terraform-3Tier-Architecture
Project4

# Terraform AWS 3-Tier Architecture (PART 1: EC2 Setup)

## 📌 Overview

This project demonstrates how to build AWS infrastructure using Terraform.

In this phase, a basic network and compute layer is provisioned, including:

- VPC
  
- Public / Private Subnets

- Internet Gateway

- Route Table

- Security Group

- EC2 Instance with Nginx

---

## 🏗️ Architecture


Internet

↓

Internet Gateway


↓

Public Route Table (0.0.0.0/0 → IGW)

↓

Public Subnet

↓

EC2 (Nginx)


---

## ⚙️ Technologies Used

- AWS (VPC, EC2, IAM)

- Terraform

- Amazon Linux 2023

- Nginx

---

## 🚀 Features


- Infrastructure as Code (IaC) using Terraform

- Automatic dependency management via Terraform graph

- Dynamic AMI selection using Terraform data source

- EC2 bootstrapping with user_data (Nginx auto-install)

- Public web server deployment

---

## 📂 Project Structure


.

├── provider.tf

├── variables.tf

├── terraform.tfvars

├── vpc.tf

├── subnets.tf

├── igw.tf

├── route_tables.tf

├── security_groups.tf

├── ec2.tf

├── data.tf

├── outputs.tf


---

## 🔑 Key Concepts Learned

### 1. Terraform Provider

- Connects Terraform to AWS API

### 2. Resource

- Defines infrastructure components (VPC, EC2, etc.)

### 3. State

- Tracks current infrastructure

### 4. Dependency Graph

- Automatically determines creation order

---

## 🧠 Improvements Made

- Removed hardcoded AMI

- Used `data "aws_ami"` to dynamically fetch latest Amazon Linux 2023

- Improved code modularity and readability

---

## 🌐 Access

After deployment:


http://<EC2_PUBLIC_IP>

<img width="1080" height="363" alt="image" src="https://github.com/user-attachments/assets/9796348d-52c2-4a17-99d9-80469f1c8ce5" />

---

## ⚠️ Notes

- HTTPS is not configured (HTTP only)

- Security Group allows ports:

  - 22 (SSH)

  - 80 (HTTP)

---

## 🧹 Cleanup

To avoid AWS charges:

##terraform destroy

```bash
📈 Next Steps
Launch Template
Auto Scaling Group
Application Load Balancer (ALB)
HTTPS with ACM
```
---

# Terraform AWS 3-Tier Architecture (PART 2: Setup ALB, TG and ASG)

## 📌 Overview

This project demonstrates how to build scalable AWS infrastructure using Terraform.

Starting from a basic VPC setup, the architecture evolves into a production-like environment with:

- Load Balancing (ALB)

- Auto Scaling (ASG)

- Multi-AZ deployment

- Infrastructure as Code (IaC)

---

## 🏗️ Architecture

### 🔹 Final Architecture


Client

↓

Application Load Balancer (ALB)

↓

Target Group

↓

Auto Scaling Group (ASG)

↓

EC2 Instances (Nginx)

---

### 🔹 Network Structure


VPC (10.0.0.0/16)

├── Public Subnet (AZ-a)

├── Public Subnet (AZ-c)

├── Private Subnet (AZ-a)

├── Private Subnet (AZ-c)

└── Internet Gateway


---

## ⚙️ Technologies Used

- AWS (VPC, EC2, ALB, ASG, IAM)

- Terraform

- Amazon Linux 2023

- Nginx

---

## 🚀 Features

- Infrastructure provisioning using Terraform

- Dynamic AMI selection (no hardcoding)

- Load balancing across multiple EC2 instances

- Auto scaling for high availability

- Multi-AZ architecture

- Automated EC2 setup using `user_data`

---

## 📂 Project Structure


.

├── provider.tf

├── variables.tf

├── terraform.tfvars

├── vpc.tf

├── subnets.tf

├── igw.tf

├── route_tables.tf

├── security_groups.tf

├── data.tf

├── alb.tf

├── asg.tf

├── outputs.tf


---

## 🔑 Key Concepts Learned

### 1. Terraform Provider

- Connects Terraform to AWS APIs

### 2. Resources

- Define infrastructure components (VPC, EC2, ALB, etc.)

### 3. State

- Tracks real infrastructure vs code

### 4. Dependency Graph

- Automatically determines resource creation order

---

## 🔄 Infrastructure Evolution

### Step 1

- VPC + Subnet + IGW + Route Table

### Step 2

- EC2 + Security Group + Nginx

### Step 3

- Dynamic AMI using data source

### Step 4

- Multi-AZ Subnet architecture

### Step 5 (Final)

- ALB + Target Group + Auto Scaling Group

---

## 🌐 Access

After deployment:

http://<ALB_DNS_NAME>

result:

<img width="1844" height="381" alt="image" src="https://github.com/user-attachments/assets/598e0f4a-daf6-437b-a8c3-0e67f55f9398" />


<ASG in aws console>


<img width="1844" height="381" alt="image" src="https://github.com/user-attachments/assets/a0afa144-2a99-4282-be79-e0f2b6803cb9" />


<ALB in aws console>


<img width="1844" height="381" alt="image" src="https://github.com/user-attachments/assets/06951993-b937-4db9-ad99-f81cd9d15489" />

<Result of access ALB DNS Name>




---

## 🧪 Testing

- Verified load balancing via ALB

- Tested Auto Scaling by terminating instances

- Confirmed high availability across AZs

---

## ⚠️ Notes

- HTTP only (HTTPS not configured yet)

- EC2 instances are in public subnets (for simplicity)

- Private subnet & NAT Gateway planned for future improvement

---

## 🧹 Cleanup

To avoid AWS charges:

```bash
**terraform destroy**

📈 Future Improvements
Move EC2 instances to private subnets
Add NAT Gateway
Configure HTTPS using ACM
Domain setup with Route53
CI/CD pipeline integration

🧠 What I Learned
How Terraform manages infrastructure lifecycle
How AWS networking components interact
Importance of dependency graph in IaC
Designing scalable and fault-tolerant architectures
```
👨‍💻 Author
Tae Young Jang


