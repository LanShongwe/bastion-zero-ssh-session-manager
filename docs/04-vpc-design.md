# 04 — VPC Design

## CIDR

10.0.0.0/16

## Purpose

The VPC provides the isolated network boundary for the project.

## Network Design

| Component | CIDR | Purpose |
|---|---|---|
| VPC | 10.0.0.0/16 | Network boundary |
| Public subnet | 10.0.1.0/24 | NAT Gateway |
| Private subnet | 10.0.2.0/24 | EC2 workload |

## Design Decision

The EC2 workload is placed in a private subnet.

The project intentionally avoids assigning a public IP to
the workload instance.

## Security Objective

The EC2 instance should not require inbound SSH from the internet.

## Evidence

See:

screenshots/01-vpc/01-vpc-overview.png