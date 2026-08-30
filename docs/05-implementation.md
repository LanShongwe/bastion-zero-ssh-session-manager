# Implementation

## 1. Create the VPC

Create:

```text
Name: bastion-zero-ssh-vpc
CIDR: 10.0.0.0/16
```

## 2. Create the public subnet

```text
Name: bastion-zero-ssh-public-1
CIDR: 10.0.1.0/24
```
## 3. Create the private subnet

```text
Name: bastion-zero-ssh-private-1
CIDR: 10.0.2.0/24
```
Associate the subnet with the project VPC.

## 4. Create the Internet Gateway
Create an Internet Gateway and attach it to:
```text
bastion-zero-ssh-vpc
```
The Internet Gateway provides internet connectivity for resources using
the appropriate public route.

## 5. Create the NAT Gateway
Create the NAT Gateway in the public subnet.

The NAT Gateway requires public connectivity through the Internet Gateway.

## 6. Create route tables

### Public route table
Associate it with the public subnet.

Default route:
```text
0.0.0.0/0 → Internet Gateway
```

### Private route table
Associate it with the private subnet.

Default route:
```text
0.0.0.0/0 → NAT Gateway
```

## 7. Create the security group
Create the security group for the EC2 instance.

The security objective is:.

```text
Inbound TCP/22 = NOT REQUIRED
```
Avoid adding SSH simply because it is common in EC2 tutorials.

## 8. Create the IAM role
Create an EC2 IAM role with the required Systems Manager permissions.

Attach the role to the EC2 instance.

## 9. Launch EC2
Launch an Amazon Linux instance.

Place it in:
```text
VPC:
bastion-zero-ssh-vpc

Subnet:
bastion-zero-ssh-private-1
```

Associate the project security group.
Attach the Systems Manager IAM role.

## 10. Validate
Confirm:

```text
Instance is running.
Instance has a private IP.
Instance is in the private subnet.
IAM role is attached.
Security group has no inbound SSH requirement.
Systems Manager recognizes the instance.
Session Manager opens successfully.
Implementation result
```
The infrastructure was successfully created and the EC2 instance was
successfully managed through Systems Manager.