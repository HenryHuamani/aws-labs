```markdown
# Commands and Technical References – AWS IAM

This laboratory was mainly completed through the AWS Management Console.

No AWS CLI commands were required.

## Useful AWS CLI Commands

### Display the current authenticated identity

```bash
aws sts get-caller-identity
List IAM users
aws iam list-users
List IAM groups
aws iam list-groups
List users belonging to a group
aws iam get-group --group-name Administrators
List policies attached to a group
aws iam list-attached-group-policies --group-name Administrators
List MFA devices
aws iam list-mfa-devices --user-name henry.admin
Important Security Warning

Never publish the following values in GitHub:

AWS access key ID.
AWS secret access key.
Session token.
Passwords.
MFA recovery codes.
Account identifiers when unnecessary.
