# secure-aws-network-terraform-project
Production-style AWS network infrastructure using Terraform (VPC, ALB, Bastion host, NAT Gateway, private subnet, EC2)
# 🏗️ Secure AWS Network Architecture (Terraform)

## 📌 Overview

This project implements a secure, scalable, and production-grade AWS network architecture using Terraform. It demonstrates real-world cloud infrastructure design patterns used in modern DevOps environments.

The architecture focuses on:
- Secure network isolation using public and private subnets  
- Controlled administrative access via Bastion host  
- Scalable traffic routing using Application Load Balancer  
- Outbound internet access through NAT Gateway  
- Multi-tier architecture design (web + application layer)  

---

## 🧠 Architecture Diagram

![AWS Architecture](images/aws-architecture.png)

---

## 🏛️ System Architecture

This infrastructure is deployed inside a custom VPC with segmented network layers:

### 🌍 Internet Layer
External users access the system through the Application Load Balancer.

### ⚖️ Public Subnet Layer
- Application Load Balancer (ALB)
- Bastion Host (secure SSH access point)
- NAT Gateway (outbound internet access for private subnet)

### 🔒 Private Subnet Layer
- EC2 Application Server running NGINX / application
- No public IP assigned
- Fully isolated from direct internet access

---

## 🔁 Traffic Flow

### 🌐 User Traffic
User → Application Load Balancer → Private EC2 (Application Server)

### 🔐 Admin Access
Developer Laptop → Bastion Host → Private EC2

### 🌍 Outbound Internet Access
Private EC2 → NAT Gateway → Internet Gateway → Internet

---

## 🧱 Infrastructure Components

- Terraform (Infrastructure as Code)
- AWS VPC (Networking foundation)
- EC2 (Compute layer)
- Application Load Balancer (Traffic distribution)
- NAT Gateway (Outbound connectivity)
- Security Groups (Network security)
- Bastion Host (Secure SSH access layer)

---

## 🔐 Security Design Principles

- No direct public access to application servers  
- Bastion host restricted to trusted IP only  
- Private subnet fully isolated from inbound traffic  
- ALB is the only public entry point  
- NAT Gateway enables controlled outbound internet access  

---

## 🏗️ Project Structure

terraform/
├── main.tf
├── vpc.tf
├── ec2.tf
├── alb.tf
├── security.tf
├── variables.tf
├── outputs.tf

images/
├── aws-architecture.png
├── vpc.png
├── alb.png
├── bastion.png

---

## 🚀 Deployment

terraform init  
terraform plan  
terraform apply  

---

## 📸 Screenshots

### VPC Overview
![VPC](images/vpc.png)

### Load Balancer
![ALB](images/alb.png)

### Bastion Access
![Bastion](images/bastion.png)

---

## 🧠 Key Learnings

- AWS VPC design and subnet segmentation  
- Secure cloud architecture patterns  
- Bastion host access control  
- Load balancer traffic distribution  
- Infrastructure automation using Terraform  
- Real-world DevOps networking design  

---

## 🎯 Outcome

This project demonstrates a production-style AWS network architecture with strong focus on security, scalability, and automation. It reflects real-world DevOps engineering practices used in enterprise cloud environments.

---

## 👨‍💻 Author

DevOps Engineer Portfolio Project  
Focused on Cloud Infrastructure, Automation, and Secure Architecture Design

## 🧪 Validation Proof

- Successfully SSH into Bastion host
- Successfully accessed private EC2 via Bastion
- Verified NAT Gateway internet access using curl
- Confirmed ALB routes traffic to application server
