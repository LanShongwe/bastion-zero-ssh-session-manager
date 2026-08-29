# 01 — Project Overview

## Project

Bastion Hosts → Zero SSH with AWS Systems Manager Session Manager

## Objective

Build a private AWS EC2 environment that can be securely administered
without exposing inbound SSH (TCP/22) to the internet.

## Problem

Traditional EC2 administration commonly uses:

Engineer → SSH →  Bastion Host  →  SSH  →  Private EC2

This introduces additional infrastructure and an additional attack surface.

## Target

Engineer → AWS Systems Manager Session Manager →  Private EC2

The EC2 instance should:

- have no public IP
- have no inbound SSH rule
- not require an SSH private key for administration
- be reachable through Systems Manager
- remain operational after SSH is completely removed

## AWS Services

- Amazon VPC
- Amazon EC2
- AWS Systems Manager
- AWS Identity and Access Management (IAM)
- Security Groups
- Internet Gateway
- NAT Gateway
- CloudWatch / Systems Manager logging where applicable

## Success Criteria

The project is successful when:

1. A VPC is created.
2. EC2 is deployed into a private subnet.
3. The instance has no public IP.
4. Security Group does not allow inbound TCP/22.
5. EC2 is registered with Systems Manager.
6. Session Manager successfully opens a shell.
7. SSH access is unavailable.
8. Systems Manager remains available.
9. Network and IAM dependencies are documented.
10. Failure scenarios are intentionally tested.

## Engineering Principle

Do not simply make the system work.

Build it, verify it, break it, troubleshoot it,
and document why it works.