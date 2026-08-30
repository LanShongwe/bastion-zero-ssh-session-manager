# Systems Manager Management

## Purpose

AWS Systems Manager Session Manager provides shell access to the EC2
instance without requiring inbound SSH.

## Connection model

```text
          Administrator
                |
                v
         Session Manager
                |
                v
             SSM Agent
                |
                v
            Private EC2
```
## Requirements

The EC2 instance requires:
```text
SSM Agent
Appropriate IAM role
Required outbound connectivity
Systems Manager availability
```

## Session flow

The EC2 instance requires:#

1. Administrator opens Session Manager.
2. Systems Manager identifies the managed       instance.
3. A session is established.
4. The SSM Agent communicates with Systems Manager.
5. Administrator receives a shell.

## Validation

Inside the session, basic Linux commands can be used:

```bash
whoami
hostname
pwd
uname -a
```

## Why this is useful

Session Manager removes the need to expose an administrative SSH endpoint
for normal management.

It also allows access to be controlled through AWS IAM.

## Operational model

Instead of managing:

```text
Public IP
Security Group TCP/22
SSH keys
SSH access
```

the administrator can manage access through:

```text
AWS IAM
Systems Manager
Session Manager
```

## Important

Session Manager does not mean networking no longer matters.

The EC2 instance still requires correct IAM, agent operation, and required
network connectivity.