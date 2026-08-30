# Requirements

## Functional requirements

The environment must:

1. Run an Amazon Linux EC2 instance.
2. Place the workload in a private subnet.
3. Provide required outbound connectivity.
4. Allow the instance to communicate with AWS Systems Manager.
5. Allow an administrator to open a shell using Session Manager.
6. Avoid requiring inbound SSH for administration.

## Network requirements

VPC:

```bash 
10.0.0.0/16
```

Public subnet:

```bash
10.0.1.0/24
```

Private subnet:

```bash
10.0.2.0/24
```

The public subnet contains the NAT Gateway infrastructure.

The EC2 workload is placed in the private subnet.

## Security requirements

Inbound SSH:

```bash
Not required.
```
TCP port:
```bash
22
```
Expected inbound SSH:
```bash
None
```
Management mechanism:
```bash
AWS Systems Manager Session Manager
```
## AWS components

- VPC
- Internet Gateway
- NAT Gateway
- Route tables
- Security Group
- IAM role
- EC2
- Systems Manager

## Validation requirements

The final environment must demonstrate:

- EC2 is running.
- EC2 is in the intended private subnet.
- Correct IAM role is attached.
- Instance is visible to Systems Manager.
- Session Manager establishes a shell.
- No inbound SSH rule is required.