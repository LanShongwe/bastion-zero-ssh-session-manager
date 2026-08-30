# Architecture Decisions

## Security Group

The EC2 target instance will not expose inbound SSH access.

Inbound TCP/22 is intentionally not configured.

Server administration will be performed using AWS Systems Manager
Session Manager.

This reduces the need to expose SSH to the network and removes the
requirement for a publicly reachable management port.