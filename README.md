# AWS-Terraform-3Tier-Architecture
Project4

# Terraform AWS 3-Tier Architecture (Step 1: EC2 Setup)

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


---

## ⚠️ Notes

- HTTPS is not configured (HTTP only)

- Security Group allows ports:

  - 22 (SSH)

  - 80 (HTTP)

---

## 🧹 Cleanup

To avoid AWS charges:

#terraform destroy

```bash
📈 Next Steps
Launch Template
Auto Scaling Group
Application Load Balancer (ALB)
HTTPS with ACM
```
