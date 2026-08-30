# Failure Tests

## Test 01 — SSH access

Objective:

```Verify that inbound SSH is not available to the EC2 instance.```

Expected:

```SSH connection should not be possible.```

Security Group:

```zero-ssh-target-sg```

Inbound TCP/22:

```Not configured```

Result:

```PASS```

Conclusion:

```The instance does not expose inbound SSH as a management mechanism.```