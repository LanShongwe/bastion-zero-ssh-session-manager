# Validation

## Objective

Confirm that the environment meets the original security and connectivity
requirements.

## Test 1 — EC2

Check:

- Instance is running.
- Correct VPC.
- Correct private subnet.
- Correct security group.

Result:
```text
PASS
```
---

## Test 2 — IAM

Check:

- Correct IAM role is attached.
- Required Systems Manager permissions are available.

Result:

```text
PASS
```

---

## Test 3 — Systems Manager

Check:

- Instance appears as a managed node.

Result:

```text
PASS
```

---

## Test 4 — Session Manager

Open a Session Manager shell.

Run:

```bash
whoami
hostname
pwd
```
Result:

```text
PASS
```

## Test 5 — SSH

Verify the security group does not provide an inbound TCP/22 management
path.

Result:

```text
PASS
```

## Validation flow

```text
            EC2 running
                |
                v
        Private subnet
                |
                v
        IAM role attached
                |
                v
            SSM managed
                |
                v
     Session Manager works
                |
                v
     No inbound SSH required
                |
                v
      PROJECT OBJECTIVE MET
```

## Evidence

Supporting screenshots are stored under:

```text
screenshots/08-validation/
```

## Final result

The environment successfully demonstrated administrative access to a
private EC2 instance through Systems Manager without requiring inbound SSH.