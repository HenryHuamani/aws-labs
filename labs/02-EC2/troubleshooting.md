# Amazon EC2 - Troubleshooting Guide

This document describes the issues encountered during **Lab 02 – Amazon Elastic Compute Cloud (EC2)** and the corresponding solutions.

---

# Issue 1 - SSH Permission Denied (publickey)

## Symptoms

```
Permission denied (publickey)
```

Connection could not be established using SSH.

---

## Possible Causes

- Incorrect username.
- Wrong private key.
- Invalid Key Pair.
- Incorrect file permissions.
- Security Group blocking port 22.

---

## Resolution

Verify:

- Instance is running.
- Correct username (`ubuntu`).
- Correct Key Pair.
- SSH port (22) is allowed.
- Private key permissions.

Successful command:

```powershell
ssh -i .\henry-key.pem ubuntu@ec2-public-dns
```

---

# Issue 2 - Unprotected Private Key File

## Symptoms

```
WARNING: UNPROTECTED PRIVATE KEY FILE!
```

```
Permissions are too open.
```

OpenSSH refused to use the private key.

---

## Cause

Windows ACL permissions allowed other users to access the `.pem` file.

OpenSSH requires that only the owner has read access.

---

## Resolution

Disable inherited permissions:

```powershell
icacls .\henry-key.pem /inheritance:r
```

Remove the built-in Users group:

```powershell
icacls .\henry-key.pem /remove "BUILTIN\Users"
```

Verify permissions:

```powershell
icacls .\henry-key.pem
```

Expected result:

```
DESKTOP-XXXX\User:(R)
SYSTEM:(F)
Administrators:(F)
```

Retry the SSH connection:

```powershell
ssh -i .\henry-key.pem ubuntu@ec2-public-dns
```

---

# Issue 3 - Connection Closed by Port 22

## Symptoms

```
Connection closed by <ip-address> port 22
```

---

## Possible Causes

- Incorrect username.
- SSH daemon not accepting authentication.
- Invalid Key Pair.

---

## Resolution

Confirm:

- Username is `ubuntu`.
- Correct Key Pair is used.
- Instance is fully initialized.
- Security Group allows SSH.

---

# Issue 4 - Unable to Connect Using SSH

## Symptoms

SSH connection times out.

---

## Possible Causes

- Port 22 blocked.
- Wrong Public IP or DNS.
- Instance stopped.
- Network connectivity issues.

---

## Resolution

Verify:

- EC2 instance is in **Running** state.
- Public IPv4 address.
- Public DNS name.
- Security Group inbound rules.
- Internet connection.

---

# Issue 5 - Security Group Misconfiguration

## Symptoms

Connection refused or timeout.

---

## Cause

Inbound rule for SSH (TCP 22) was missing or restricted.

---

## Resolution

Configure the Security Group:

| Type | Protocol | Port | Source |
|------|----------|------|--------|
| SSH | TCP | 22 | My IP |

Avoid opening SSH to:

```
0.0.0.0/0
```

unless absolutely necessary.

---

# Issue 6 - Lost Private Key

## Problem

The `.pem` file is deleted or lost.

---

## Impact

SSH authentication is no longer possible using the original Key Pair.

---

## Resolution

Possible recovery options:

- Create a new instance.
- Attach the EBS volume to another instance.
- Replace the authorized SSH key using recovery procedures.

---

# Issue 7 - EC2 Instance Not Reachable

## Symptoms

The instance appears online but cannot be accessed.

---

## Possible Causes

- Security Group configuration.
- Incorrect Public IP.
- SSH service stopped.
- Operating system issue.

---

## Resolution

Verify:

- EC2 Status Checks.
- Security Group.
- Public IPv4 address.
- Instance System Log.
- EC2 Instance Connect (if available).

---

# Commands Used During Troubleshooting

```powershell
ssh -vvv -i .\henry-key.pem ubuntu@ec2-public-dns
```

```powershell
icacls .\henry-key.pem
```

```powershell
icacls .\henry-key.pem /inheritance:r
```

```powershell
icacls .\henry-key.pem /remove "BUILTIN\Users"
```

```powershell
ssh -i .\henry-key.pem ubuntu@ec2-public-dns
```

---

# Lessons Learned

- Windows file permissions can prevent OpenSSH from using a private key.
- Security Groups are the first component to verify when SSH fails.
- Always keep a backup of the private key.
- Use verbose mode (`ssh -vvv`) to diagnose connection issues.
- Restrict SSH access to trusted IP addresses.

---

# Laboratory Outcome

Successfully completed:

- EC2 Instance deployment.
- Security Group configuration.
- SSH connectivity.
- Windows private key permission correction.
- Secure remote administration using PowerShell.