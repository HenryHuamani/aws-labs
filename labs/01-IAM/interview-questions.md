# AWS IAM - Interview Questions

This document contains common technical interview questions related to **AWS Identity and Access Management (IAM)**.

---

# Basic Level

## 1. What is AWS IAM?

AWS Identity and Access Management (IAM) is a global AWS service used to securely manage identities and control access to AWS resources.

---

## 2. Is IAM a Regional or Global service?

IAM is a **Global Service**.

Users, Groups, Roles and Policies are available across all AWS Regions.

---

## 3. What are the core IAM components?

- Users
- Groups
- Roles
- Policies
- MFA

---

## 4. What is the difference between Authentication and Authorization?

Authentication verifies **who you are**.

Authorization determines **what you are allowed to do**.

---

## 5. What is an IAM Policy?

A Policy is a JSON document that defines permissions.

Policies specify:

- Actions
- Resources
- Effect (Allow / Deny)
- Conditions

---

# Intermediate Level

## 6. What is the difference between an IAM User and an IAM Role?

| IAM User | IAM Role |
|----------|----------|
| Permanent identity | Temporary identity |
| Long-term credentials | Temporary credentials (AWS STS) |
| Used by people | Used by AWS services, applications or cross-account access |

---

## 7. Why should you use IAM Groups?

Groups simplify permission management.

Permissions are assigned once to the group instead of individually to every user.

---

## 8. What is the Principle of Least Privilege?

Users should receive only the minimum permissions required to perform their work.

---

## 9. What are AWS Managed Policies?

Policies created and maintained by AWS.

Examples:

- AdministratorAccess
- ReadOnlyAccess
- PowerUserAccess

---

## 10. What is MFA?

Multi-Factor Authentication adds an additional authentication factor beyond the password.

Typical factors:

- Password
- Authenticator App
- Hardware Token

---

# Advanced Level

## 11. Why should the Root User not be used daily?

The Root User has unrestricted permissions.

AWS recommends using it only for account setup and billing-related tasks.

---

## 12. What happens if a user belongs to multiple groups?

The effective permissions are the **union of all allowed permissions**, unless an explicit **Deny** overrides them.

---

## 13. What takes precedence: Allow or Deny?

**Explicit Deny always overrides Allow.**

---

## 14. What is AWS STS?

AWS Security Token Service (STS) provides temporary credentials for IAM Roles.

---

## 15. When should you use IAM Roles instead of Access Keys?

Use IAM Roles whenever AWS resources need to access other AWS services.

Examples:

- EC2 → S3
- Lambda → DynamoDB
- ECS → Secrets Manager

---

## 16. What is Cross-Account Access?

It allows users or services from one AWS Account to assume a Role in another AWS Account without sharing credentials.

---

## 17. What is the difference between an Inline Policy and a Managed Policy?

| Managed Policy | Inline Policy |
|----------------|---------------|
| Reusable | Attached to one identity only |
| Easier to maintain | Tightly coupled to a single User, Group or Role |
| Recommended by AWS | Used for specific scenarios |

---

## 18. What is an IAM Permission Boundary?

A Permission Boundary defines the maximum permissions that an IAM User or Role can receive.

---

## 19. How can IAM activity be audited?

Using:

- AWS CloudTrail
- AWS CloudWatch
- AWS Config

---

## 20. During this laboratory, what resources were created?

- IAM User
- IAM Group
- AWS Managed Policy attachment
- Virtual MFA
- AWS Console Login

---

# Interview Tips

If asked:

> "How would you secure an AWS account?"

A strong answer includes:

- Enable MFA.
- Avoid using the Root User.
- Apply Least Privilege.
- Use IAM Groups.
- Use IAM Roles instead of Access Keys.
- Rotate credentials regularly.
- Enable CloudTrail for auditing.

---

# Key Takeaways

- IAM is Global.
- Policies are written in JSON.
- Roles provide temporary credentials.
- MFA should always be enabled.
- Explicit Deny overrides Allow.
- Least Privilege is an AWS security best practice.
