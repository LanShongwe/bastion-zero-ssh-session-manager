# Zero SSH Security Model

## Objective

The project intentionally avoids using inbound SSH as the normal
administrative access path.

## Traditional model

```text
            Internet
                |
                | TCP/22
                v
          Security Group
                |
                v
               EC2
```
This requires an administrative port to be reachable.

## Project model

```text
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
```

## Security group

The EC2 security group does not require:

```text
Inbound TCP 22
```
## Private workload

The EC2 instance is placed in the private subnet.

This prevents the architecture from depending on direct public access to
the workload.

## IAM

Access to Systems Manager is controlled through AWS IAM.

This moves an important part of access control from network exposure toward
identity and AWS permissions.

## Private key considerations

The project does not depend on an EC2 SSH private key for normal
administration.

This reduces the need to distribute or manage SSH keys for routine access.

## Important security principle

Removing SSH does not automatically make an environment secure.

Security still depends on:

- IAM permissions
- security groups
- network design
- operating-system security
- patching
- logging
- access control
- monitoring

## Main lesson

The goal is not:

```text
"SSH is bad."
```

The goal is:

```text
"Do not expose an administrative interface when the architecture does not
require it."
```