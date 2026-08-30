# AWS CLI Quick Reference

## Configure AWS CLI

```bash
aws configure
```

## Check identity

```bash
aws sts get-caller-identity
```

## Check region

```bash
aws configure get region
```

## List VPCs

```bash
aws ec2 describe-vpcs
```

## List subnets

```bash
aws ec2 describe-subnets
```

## List route tables

```bash
aws ec2 describe-route-tables
```

## List security groups

```bash
aws ec2 describe-security-groups
```

## List EC2 instances

```bash
aws ec2 describe-instances
```
## Check Systems Manager managed nodes

```bash
aws ssm describe-instance-information
```

## Start a Session Manager session

```bash
aws ssm start-session --target <instance-id>
```

## Check EC2 instance state

```bash
aws ec2 describe-instances \
  --instance-ids <instance-id> \
  --query 'Reservations[].Instances[].State.Name'
```

## Useful filtering pattern

```bash
aws ec2 describe-instances \
  --filters "Name=tag:Name,Values=zero-ssh-target"
```

## General rule

Use:

```bash
aws <service> <operation>
```

When troubleshooting, query the exact AWS resource instead of relying only
on the console.