# Validation Results

## Objective

Confirm that the EC2 instance can be administered through AWS Systems Manager
without requiring inbound SSH access.

---

## Test 1 — EC2 Instance

Expected:

- Instance running
- Correct VPC
- Correct subnet
- Correct security group

Result:

PASS

Evidence:

screenshots/08-validation/01-instance-running.png

---

## Test 2 — Systems Manager

Expected:

EC2 instance appears as a managed node.

Result:

PASS

Evidence:

screenshots/08-validation/02-ssm-managed.png

---

## Test 3 — Session Manager

Expected:

Administrator can establish a shell session.

Result:

PASS

Evidence:

screenshots/08-validation/03-session-connected.png

---

## Test 4 — SSH

Expected:

No inbound SSH management path.

Result:

PASS

Evidence:

screenshots/08-validation/05-no-inbound-ssh.png

---

## Overall Result

The environment successfully met the primary project objective:

EC2 administration was achieved using AWS Systems Manager Session Manager
without requiring inbound SSH access.