
# Amazon EC2 Architecture

This directory contains the architecture diagram created for **Lab 02 – Amazon Elastic Compute Cloud (EC2)**.

The diagram illustrates the logical components deployed during the laboratory and the secure SSH connection flow from a Windows workstation to an Amazon EC2 instance.

---

# Architecture Overview

The laboratory architecture includes:

- AWS Account
- Amazon EC2 Instance
- Ubuntu Server 24.04 LTS
- Public IPv4 Address
- Security Group
- SSH (TCP Port 22)
- SSH Key Pair Authentication
- Amazon EBS Storage
- Windows PowerShell Client

---

# Files

| File | Description |
|------|-------------|
| `source/ec2.drawio` | Editable Draw.io source file |
| `export/ec2.png` | PNG export for GitHub documentation |
| `export/ec2.svg` | SVG export for high-resolution viewing |

---

# Architecture Flow

```text
Windows PowerShell
        │
        ▼
SSH Connection
        │
        ▼
Security Group
(TCP 22 - My IP)
        │
        ▼
Amazon EC2 Instance
(Ubuntu Server 24.04)
        │
        ▼
Amazon EBS Volume
```

---

# Design Goals

The architecture was designed to demonstrate:

- Secure remote administration
- SSH authentication using Key Pair
- Security Group configuration
- Persistent storage using Amazon EBS
- AWS infrastructure fundamentals

---

# Related Laboratory

- Lab 01 – AWS IAM
- Lab 02 – Amazon EC2
