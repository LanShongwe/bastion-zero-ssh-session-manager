# Bastion Hosts - Zero SSH with AWS Systems Manager Session Manager

## Overview

This project demonstrates how to manage an Amazon EC2 Linux server without
requiring inbound SSH access.

The environment uses AWS Systems Manager Session Manager as the primary
management mechanism.

The goal was to design a small AWS environment where:

- EC2 does not require inbound TCP/22
- Administrative access is provided through Systems Manager
- The EC2 instance runs inside a private subnet
- IAM controls access to the instance
- Network connectivity is explicitly designed and documented
- The configuration can be validated and troubleshot systematically

---

## Problem

Traditional EC2 administration commonly relies on SSH.

A typical architecture may expose:

```text
Internet
   |
   v
Security Group
   |
TCP/22
   |
EC2
```

Although SSH can be secured, exposing an administrative port creates
additional network attack surface.

This project explores an alternative:

``` text
Internet
   |
AWS Systems Manager
   |
SSM Agent
   |
Private EC2
```

No inbound SSH access is required.

---

## Architecture

![Target Architecture](diagrams/01-target-architecture.png)

![VPC Network](diagrams/02-vpc-network.png)

---

## AWS Components

| Component | Purpose |
|---|---|
| VPC | Isolated AWS network |
| Public subnet | NAT Gateway infrastructure |
| Private subnet | EC2 workload |
| Internet Gateway | Internet connectivity for public resources |
| NAT Gateway | Outbound connectivity from private subnet |
| Route tables | Control network traffic |
| Security Group | Instance-level network control |
| IAM role | Allows EC2 to communicate with Systems Manager |
| EC2 | Linux workload |
| Systems Manager | Remote management |

---

## Network Design

VPC:

10.0.0.0/16

Public subnet:

10.0.1.0/24

Private subnet:

10.0.2.0/24

The EC2 instance is placed in the private subnet.

The private subnet uses the NAT Gateway for outbound connectivity where
required.

---

## Management Model

Traditional:

Administrator
     |
     | SSH / TCP 22
     v
EC2

This project:

Administrator
     |
     v
AWS Systems Manager
     |
     v
SSM Agent
     |
     v
Private EC2

---

## Security Objective

The primary security objective is:

> No inbound SSH access is required for normal instance administration.

TCP/22 is not used as the management path.

---

## Validation

The environment was tested to confirm:

- EC2 instance is running
- EC2 is located in the intended subnet
- IAM role is attached
- Systems Manager recognizes the instance
- Session Manager can establish a shell session
- Administrative access works without an inbound SSH rule

Evidence is stored in:

screenshots/

evidence/

---

## Key Lessons

This project reinforced several practical AWS concepts:

- VPC design
- subnet segmentation
- route tables
- NAT Gateway behaviour
- security groups
- IAM instance roles
- Systems Manager
- private EC2 management
- troubleshooting network connectivity
- security-oriented architecture

---

## Project Status

Completed.

The environment was successfully built and tested.

This is a learning project designed to reproduce a realistic AWS
infrastructure and operations scenario.
