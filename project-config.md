# Project Configuration

## AWS Region

Region:
us-east-1

## VPC

Name:
bastion-zero-ssh-vpc

CIDR:
10.0.0.0/16

## Subnets

Public subnet: ```bastion-zero-ssh-public-1```

10.0.1.0/24

Private subnet: ```bastion-zero-ssh-private-1```

10.0.2.0/24

## EC2

Name:
zero-ssh-target

OS:
Amazon Linux

## Security objective

No inbound SSH access required.

SSH port:
22

Expected inbound SSH:
None

Expected management mechanism:
AWS Systems Manager Session Manager

## Security Group

Name:

````zero-ssh-target-sg```

Purpose:

```Security group for the private EC2 target.```

Inbound:

```
Inbound rules
┌──────────┬──────────┬────────────┬─────────────┐
│ Type     │ Protocol │ Port       │ Source      │
├──────────┼──────────┼────────────┼─────────────┤
│          │          │            │             │
│ NONE     │          │            │             │
└──────────┴──────────┴────────────┴─────────────┘
```

Outbound:

```
All traffic
0.0.0.0/0
```

Security objective:

```No inbound SSH access.```