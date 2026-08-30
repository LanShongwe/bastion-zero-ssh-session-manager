# VPC Design

## VPC

Name:

```text
bastion-zero-ssh-vpc
```

CIDR:
```text
10.0.0.0/16
```
The /16 network provides a private address space for the project.

## Subnet design

### Public subnet

Name:
```text
bastion-zero-ssh-public-1
```
CIDR:
```text
10.0.1.0/24
```
Purpose:

- Public network infrastructure
- NAT Gateway

### Private subnet

Name:
```text
bastion-zero-ssh-private-1
```
CIDR:
```text
10.0.2.0/24
```
Purpose:

- EC2 workload
- No direct public exposure

## Network layout

```text
VPC
10.0.0.0/16
│
├── Public subnet
│   10.0.1.0/24
│   │
│   └── NAT Gateway
│
└── Private subnet
    10.0.2.0/24
    │
    └── EC2
```
### Route design

Public subnet:
```text
    0.0.0.0/0
        |
        v
Internet Gateway
```

Private subnet:
```text
    0.0.0.0/0
        |
        v
    NAT Gateway
```