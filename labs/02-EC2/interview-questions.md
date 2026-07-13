# Amazon EC2 - Interview Questions

This document contains common interview questions related to **Amazon Elastic Compute Cloud (EC2)**, from basic concepts to advanced architectural scenarios.

---

# Basic Level

## 1. What is Amazon EC2?

Amazon EC2 (Elastic Compute Cloud) is AWS's Infrastructure as a Service (IaaS) that provides scalable virtual servers in the cloud.

It allows users to launch, manage, and terminate virtual machines without owning physical hardware.

---

## 2. What is an EC2 Instance?

An EC2 Instance is a virtual machine running on AWS infrastructure.

It consists of:

- CPU
- Memory
- Storage
- Network
- Operating System

---

## 3. What is an AMI?

An Amazon Machine Image (AMI) is a template used to launch EC2 instances.

It contains:

- Operating System
- Installed Software
- Configuration
- Storage Mapping

---

## 4. What is an Instance Type?

Instance Types define the hardware resources allocated to an EC2 instance.

Examples:

- t2.micro
- t3.medium
- m5.large
- c6i.large
- r6g.large

---

## 5. What is Amazon EBS?

Amazon Elastic Block Store (EBS) provides persistent block storage for EC2 instances.

EBS volumes remain available even if an instance is stopped.

---

# Intermediate Level

## 6. What is a Security Group?

A Security Group is a virtual firewall attached to an EC2 instance.

It controls:

- Inbound traffic
- Outbound traffic

Security Groups are **stateful**.

---

## 7. What is a Key Pair?

A Key Pair is used to securely authenticate to an EC2 instance using SSH.

It consists of:

- Public Key (stored by AWS)
- Private Key (.pem) (stored by the administrator)

---

## 8. Why is password authentication disabled by default on Ubuntu EC2 instances?

Because SSH key authentication is significantly more secure than password-based authentication.

---

## 9. What is the EC2 Instance Lifecycle?

The lifecycle is:

Pending

↓

Running

↓

Stopping

↓

Stopped

↓

Starting

↓

Running

↓

Terminated

---

## 10. What happens when an EC2 instance is stopped?

- Compute billing stops.
- EBS volumes remain.
- Public IPv4 may change (unless using Elastic IP).
- Data stored on EBS persists.

---

# Advanced Level

## 11. What is the difference between Stop, Reboot, and Terminate?

| Action | Result |
|----------|--------|
| Stop | Instance shuts down, EBS persists |
| Reboot | Operating system restarts |
| Terminate | Instance is permanently deleted |

---

## 12. What is the difference between Security Groups and Network ACLs?

| Security Group | Network ACL |
|----------------|-------------|
| Instance level | Subnet level |
| Stateful | Stateless |
| Allow rules only | Allow and Deny rules |

---

## 13. What are the EC2 purchasing options?

- On-Demand
- Reserved Instances
- Spot Instances
- Savings Plans
- Dedicated Hosts

---

## 14. When would you use Spot Instances?

Spot Instances are ideal for interruptible workloads such as:

- Batch processing
- Data analytics
- Rendering
- CI/CD jobs

---

## 15. Why would you use an Elastic IP?

Elastic IP provides a static public IPv4 address that remains associated with your AWS account until released.

---

## 16. How can you improve EC2 security?

Possible answers:

- Use Security Groups.
- Enable IAM Roles.
- Restrict SSH to trusted IPs.
- Enable CloudTrail.
- Keep the OS updated.
- Use MFA for administrators.
- Avoid using the Root User.

---

## 17. What is User Data?

User Data is a startup script executed automatically when an EC2 instance launches.

It is commonly used to:

- Install packages
- Configure services
- Deploy applications
- Initialize environments

---

## 18. How would you make an EC2 application highly available?

Typical architecture:

- Multiple EC2 instances
- Multiple Availability Zones
- Application Load Balancer
- Auto Scaling Group
- Amazon RDS Multi-AZ

---

## 19. How would you reduce EC2 costs?

Possible answers:

- Stop unused instances.
- Use Spot Instances.
- Use Reserved Instances.
- Right-size instances.
- Monitor utilization with CloudWatch.

---

## 20. During this laboratory, what resources were created?

- EC2 Instance
- Security Group
- Key Pair
- EBS Volume
- Public IPv4 Address

---

# Scenario-Based Questions

## Scenario 1

Your SSH connection suddenly stops working.

What would you check first?

Expected answer:

- Security Group rules
- Public IP
- Instance state
- Key Pair
- SSH service
- Network connectivity

---

## Scenario 2

You accidentally delete your private key (.pem).

Can you connect to the instance?

Expected answer:

No.

You must either:

- Create a new Key Pair through a recovery process, or
- Attach the EBS volume to another instance to recover access.

---

## Scenario 3

You need to host a public website.

Which AWS services would you combine?

Possible answer:

- EC2
- Security Groups
- Application Load Balancer
- Route 53
- Amazon RDS
- CloudFront
- ACM

---

# Interview Tips

A strong EC2 interview answer should include:

- Security considerations
- Scalability
- Cost optimization
- High availability
- Monitoring
- Best practices

---

# Key Takeaways

- EC2 provides virtual machines in AWS.
- AMIs define the operating system template.
- EBS provides persistent storage.
- Security Groups protect network access.
- SSH uses Key Pair authentication.
- Elastic IP provides a static public address.
- EC2 supports multiple purchasing models for cost optimization.