# IAM for Systems Manager

## Objective

Allow the EC2 instance to communicate with AWS Systems Manager
without storing AWS access keys on the instance.

## IAM Role

Role:

```zero-ssh-ssm-role```

Trusted service:

```EC2```

Policy:

```AmazonSSMManagedInstanceCore```

## Architecture
```
EC2
 |
 | assumes IAM role
 v
zero-ssh-ssm-role
 |
 v
AWS Systems Manager
```
## Security principle

The EC2 instance receives temporary AWS permissions through an IAM
role instead of storing long-term AWS credentials.

## Validation

The role will be attached to the EC2 instance during the EC2 build
phase.

SSM registration will be validated after the instance is running.