# Project Overview

## Project

Bastion Hosts - Zero SSH with AWS Systems Manager Session Manager

## Objective

Build and validate an AWS environment where an EC2 Linux server can be
administrated without requiring inbound SSH access.

The project uses AWS Systems Manager Session Manager as the primary
management mechanism.

## Problem

Traditional EC2 administration often uses SSH:

```bash
 Engineer
   |
   | TCP/22
   v
  EC2
```
This requires SSH to be reachable and creates an additional administrative
network exposure.

The target design removes this requirement:

Engineer
   |
   v
AWS Systems Manager
   |
   v
SSM Agent
   |
   v
Private EC2

## What was built

- Custom VPC
- Public subnet
- Private subnet
- Internet Gateway
- NAT Gateway
- Public and private route tables
- Security group
- IAM role for Systems Manager
- Amazon Linux EC2 instance
- Systems Manager Session Manager access

## Security objective

The EC2 instance does not require an inbound TCP/22 rule for normal
administration.

## Result

The environment was successfully built and tested.

The EC2 instance can be accessed through Session Manager without using
inbound SSH.

## Key AWS concepts

- VPC
- CIDR addressing
- Subnets
- Route tables
- Internet Gateway
- NAT Gateway
- Security Groups
- IAM
- EC2
- Systems Manager
- Session Manager

## Project type

Hands-on AWS infrastructure and DevOps learning project focused on
networking, security, Linux administration, and operational access.