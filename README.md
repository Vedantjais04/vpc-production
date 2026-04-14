# 🚀 AWS VPC Production Architecture (DevOps Project)

## 📌 Overview

This project demonstrates a **production-grade AWS infrastructure setup** built manually using the AWS Management Console.

Unlike traditional projects, this is **infrastructure-focused**, so this repository serves as **documentation of the architecture and implementation**.

---

## 🏗️ Architecture Summary

The architecture includes:

* VPC with **2 Public + 2 Private Subnets**
* Multi-AZ deployment for high availability
* NAT Gateway for outbound internet access
* Application Load Balancer
* Auto Scaling Group for scalability
* Bastion Host for secure SSH access

---

## 🌐 Architecture Flow

```text
Internet
   ↓
Application Load Balancer (Public Subnet)
   ↓
Auto Scaling Group (Private Subnets)
   ↓
Private EC2 Instances
```

SSH Access Flow:

```text
Local Machine → Bastion Host → Private EC2
```

---

## ⚙️ Implementation Details

This architecture was built **manually using AWS Console (no VS Code or local codebase)**.

### Steps Performed:

1. Created a VPC
2. Created:

   * 2 Public Subnets
   * 2 Private Subnets (across different AZs)
3. Attached Internet Gateway
4. Configured Route Tables
5. Created NAT Gateway in Public Subnet
6. Launched Bastion Host (Public Subnet)
7. Launched EC2 instances in Private Subnets
8. Configured Application Load Balancer
9. Set up Auto Scaling Group

---

## 🔐 Security Architecture

* Private instances are **not publicly accessible**
* SSH access only via **Bastion Host**
* Controlled network flow using route tables and subnets

---

## 💻 Application Setup

A simple web server was hosted using:

```bash
python3 -m http.server
```

### Sample `index.html`

```html
<!DOCTYPE html>
<html>
<head>
    <title>My AWS Project</title>
</head>
<body>
    <h1>Hello from Private EC2 🚀</h1>
</body>
</html>
```

---

## 🛠️ Commands Used

### SSH into Bastion

```bash
ssh -i aws_login.pem ubuntu@<bastion-public-ip>
```

### SSH into Private EC2

```bash
ssh -i aws_login.pem ubuntu@<private-ip>
```

### Copy file using SCP

```bash
scp -i aws_login.pem file ubuntu@<bastion-ip>:/home/ubuntu/
```

---

## 📊 Key Learnings

* Difference between **Public vs Private Subnets**
* Importance of **NAT Gateway**
* How **Bastion Host enables secure access**
* Real-world **high availability architecture**
* How production systems isolate internal services

---

## 📌 Notes

* No local development environment (VS Code) was used
* Entire infrastructure was created via AWS Console
* Repository serves as **documentation + learning reference**

---

## 🔥 Future Improvements

* Convert setup to **Terraform (Infrastructure as Code)**
* Add **CI/CD pipeline**
* Deploy containerized application (Docker)
* Integrate monitoring (CloudWatch)

---

## 👨‍💻 Author

Vedant Jaiswal
