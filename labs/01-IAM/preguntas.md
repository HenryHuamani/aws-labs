# Interview Questions – Amazon EC2

## What is Amazon EC2?

Amazon EC2 provides scalable virtual servers in the AWS cloud.

---

## What is an AMI?

An Amazon Machine Image used to launch EC2 instances.

---

## What is the difference between stopping and terminating an instance?

Stopping preserves the instance and attached EBS volumes.

Terminating permanently deletes the instance.

---

## What is a Security Group?

A virtual firewall that controls inbound and outbound traffic.

---

## What is the purpose of a Key Pair?

To authenticate securely using SSH without passwords.

---

## What is SSH?

Secure Shell protocol for remote administration.

---

## Difference between Security Groups and NACL?

Security Groups are stateful.

Network ACLs are stateless.

---

## What is an EBS volume?

Persistent block storage attached to EC2.

---

## What happens if the .pem file is lost?

You cannot connect using SSH.

A new key must be configured through another access method.

---

## Why should port 22 not be open to 0.0.0.0/0?

Because it exposes SSH to the Internet, increasing the attack surface.
