# 06 — Subnets

## Public Subnet
```
CIDR:

10.0.1.0/24

Purpose:

Provides connectivity for public-facing network infrastructure
such as the NAT Gateway.
```
## Private Subnet
```
CIDR:

10.0.2.0/24

Purpose:

Hosts the EC2 workload.

The EC2 instance should not receive a public IPv4 address.
``` 
## Architecture

```
VPC
│
├── Public Subnet
│   └── NAT Gateway
│
└── Private Subnet
    └── EC2
```


## Security Principle

The workload is separated from direct internet ingress.

## Evidence

See:

screenshots/02-subnets/