# Architecture Decisions

## Decision 1 — Private EC2

### Decision

Place the EC2 workload inside a private subnet.

### Reason

The instance does not need to accept direct administrative connections
from the public internet.

### Benefit

Reduces direct network exposure.

---

## Decision 2 — Session Manager

### Decision

Use AWS Systems Manager Session Manager for administrative access.

### Reason

It removes the requirement for inbound SSH connectivity.

### Benefit

Administrative access can be controlled through IAM and AWS Systems Manager.

---

## Decision 3 — No TCP/22

### Decision

Do not create an inbound security-group rule for SSH.

### Reason

SSH is not required for the intended management workflow.

### Benefit

Reduces exposed administrative attack surface.

---

## Decision 4 — NAT Gateway

### Decision

Provide outbound internet connectivity from the private subnet through
a NAT Gateway.

### Reason

Private resources may require outbound communication for package updates,
agent communication, or other external services.

### Important

NAT Gateway provides outbound connectivity. It does not make the private
EC2 instance directly reachable from the internet.