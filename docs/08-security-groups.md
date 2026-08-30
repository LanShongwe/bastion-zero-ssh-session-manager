# Security Groups

## Purpose

Security groups act as stateful virtual firewalls for EC2 instances.

This project intentionally uses a security group with no inbound rules.

The target EC2 instance will be managed through AWS Systems Manager Session Manager instead of inbound SSH.

---

## Project Security Group

Name:

```zero-ssh-target-sg```

VPC:

```bastion-zero-ssh-vpc```

Purpose:

```Private EC2 management without inbound SSH.```

---

## Inbound Rules

None.

TCP port 22 is intentionally not allowed.

No:

- SSH from the internet
- SSH from personal IP
- SSH from a bastion host

---

## Outbound Rules

Default:

All traffic → 0.0.0.0/0

The private instance requires outbound connectivity for management and other required operations.

---

## Architecture
```
        Internet
        |
        X TCP/22
        |
        Private EC2
        |
        | HTTPS / 443
        v
        AWS Systems Manager
        |
        v
        Session Manager
```
---

## Why No SSH?

Traditional model:

Administrator
     |
     | TCP/22
     v
Bastion
     |
     | TCP/22
     v
Private EC2

This requires:

- SSH keys
- SSH access rules
- bastion management
- patching
- additional attack surface

Target model:

Administrator
     |
     v
AWS Systems Manager
     |
     | secure outbound connection
     v
Private EC2

No inbound management port is required.

---

## Validation

Check:

- Security group attached to correct VPC
- No inbound rules
- No TCP/22 inbound rule
- Outbound connectivity available
- Security group ID recorded

---

## Troubleshooting

If Session Manager later fails:

Check in order:

1. EC2 instance role
2. SSM Agent
3. Private subnet route
4. NAT Gateway
5. DNS
6. Outbound HTTPS
7. Systems Manager endpoints
8. Instance registration in Systems Manager

---

## Evidence

Screenshot:

screenshots/04-security-groups/01-zero-ssh-target-sg.png

Validation:

evidence/validation-results.md