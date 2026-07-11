
```markdown
# Interview Questions – AWS IAM

## 1. What is AWS IAM?

IAM is the AWS service used to manage identities, authentication and permissions for access to AWS resources.

## 2. What is the difference between the root user and an IAM user?

The root user has unrestricted access to the AWS account and should only be used for exceptional account-level tasks.

An IAM user is created for daily access and receives only the permissions required for its responsibilities.

## 3. What is the difference between an IAM user and an IAM role?

An IAM user normally represents a person or application with long-term credentials.

An IAM role provides temporary permissions and is assumed by users, applications or AWS services.

## 4. What is an IAM policy?

An IAM policy is a JSON document that defines allowed or denied actions over AWS resources.

## 5. Why should permissions be assigned through groups?

Groups simplify administration and ensure that users with similar responsibilities receive consistent permissions.

## 6. What is MFA?

Multi-Factor Authentication adds a second authentication factor in addition to the password.

## 7. What is the principle of least privilege?

It consists of granting only the minimum permissions necessary to perform a specific task.

## 8. What is an explicit deny?

An explicit deny is a policy statement that blocks an action and takes precedence over an allow statement.

## 9. Are IAM resources regional?

IAM is a global AWS service. Users, groups, roles and policies are not created within a specific AWS region.

## 10. When should an IAM role be used instead of access keys?

A role should be used whenever an AWS service or application requires temporary access to AWS resources, avoiding permanent credentials.
````
