# Troubleshooting – Amazon EC2 Laboratory

## Case Study: SSH Private Key Permissions on Windows

### Problem

The SSH connection could not authenticate to the EC2 instance.

The following error was displayed:

```text
WARNING: UNPROTECTED PRIVATE KEY FILE!
Permissions for '.\henry-key.pem' are too open.
This private key will be ignored.
Permission denied (publickey).
```

### Initial Diagnosis

Detailed SSH output was generated with:

```powershell
ssh -vvv -i .\henry-key.pem ubuntu@PUBLIC_DNS
```

The output confirmed that:

* The DNS name was resolved.
* TCP port 22 was reachable.
* The SSH handshake was completed.
* The server supported public-key authentication.
* The private key was rejected because its Windows permissions were too open.

### Root Cause

The private key could be read by additional Windows security groups, including:

```text
NT AUTHORITY\Authenticated Users
BUILTIN\Usuarios
```

OpenSSH requires private keys to be accessible only by the owner or trusted system accounts.

### Resolution

Inherited permissions were removed:

```powershell
icacls .\henry-key.pem /inheritance:r
```

Access for authenticated users was removed:

```powershell
icacls .\henry-key.pem /remove "NT AUTHORITY\Authenticated Users"
```

Access for the built-in Users group was removed:

```powershell
icacls .\henry-key.pem /remove "BUILTIN\Usuarios"
```

Read access was granted to the owner:

```powershell
icacls .\henry-key.pem /grant "DESKTOP-MTQQR2P\PC:(R)"
```

The permissions were verified with:

```powershell
icacls .\henry-key.pem
```

The SSH connection was then completed successfully.

## Other Common SSH Problems

### Connection Timed Out

Possible causes:

* Port 22 is not allowed in the Security Group.
* The source IP is incorrect.
* The instance does not have a public IP.
* The route table does not provide Internet access.
* A Network ACL blocks the traffic.

### Permission Denied (Public Key)

Possible causes:

* Incorrect private key.
* Incorrect operating-system username.
* The key pair does not match the instance.
* Private-key permissions are insecure.
* The public key is missing from `authorized_keys`.

### Connection Refused

Possible causes:

* SSH service is not running.
* The operating system has not completed startup.
* The instance firewall blocks TCP port 22.

### Host Key Warning

A warning may appear when the public IP or server identity changes:

```text
REMOTE HOST IDENTIFICATION HAS CHANGED
```

Remove the obsolete entry only after verifying the new server identity:

```powershell
ssh-keygen -R PUBLIC_DNS
```

## Lessons Learned

* Network connectivity and authentication are separate SSH stages.
* Verbose SSH output helps identify the exact failure point.
* Windows permissions can prevent OpenSSH from using a valid private key.
* Security Group rules should restrict SSH access to trusted addresses.
* Private keys must remain outside the repository.

## Best Practices

* Store private keys in the user's `.ssh` directory.
* Never commit `.pem` files to Git.
* Use `.gitignore` as an additional protection.
* Use IAM roles for AWS access from EC2.
* Prefer temporary credentials.
* Consider AWS Systems Manager Session Manager to reduce direct SSH exposure.
