# Troubleshooting

## Problem

EC2 instance was running but the web page was unreachable.

---

## Symptoms

- HTTP timeout
- SSH timeout
- EC2 Instance Connect failed

---

## Investigation

Verified:

- Security Group
- Internet Gateway
- Route Table
- Network ACL
- Public IP
- User Data
- Apache installation

Everything was correctly configured.

---

## Root Cause

The issue was caused by the local browser.

Opening the page in Incognito Mode immediately solved the problem.

---

## Resolution

Access the web page using:

http://Public-IP

or clear browser cache.