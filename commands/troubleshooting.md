# Troubleshooting Quick Reference

## SSH / network

### Test connectivity

```bash
ping <host>
```

## Test a TCP port

```bash
nc -vz <host> <port>
```

## Detailed SSH debugging

```bash
ssh -vvv user@host
```

For this project, TCP/22 is intentionally not required.

## EC2 / Linux

Check instance identity

```bash
hostname
whoami
id
```

Check network

```bash
ip addr
ip route
```

Check DNS

```bash
cat /etc/resolv.conf
```

Check listening services

```bash
sudo ss -tulpn
```

## SSM

Check agent

```bash
sudo systemctl status amazon-ssm-agent
```

## Restart agent

```bash
sudo systemctl restart amazon-ssm-agent
```

## View logs

```bash
sudo journalctl -u amazon-ssm-agent
```

## AWS troubleshooting order

```text
1. Is the resource running?
          ↓
2. Correct VPC/subnet?
          ↓
3. Correct security group?
          ↓
4. Correct route table?
          ↓
5. NAT / IGW working?
          ↓
6. IAM correct?
          ↓
7. Service/agent running?
          ↓
8. Check logs
```

## Session Manager failure checklist

```text
EC2 running?
     ↓
IAM role attached?
     ↓
SSM permissions?
     ↓
SSM Agent running?
     ↓
Outbound connectivity?
     ↓
Route table?
     ↓
NAT Gateway?
     ↓
Session Manager
```

## Troubleshooting notes

Record incidents using:

```bash
Problem:
Observation:
Hypothesis:
Test:
Result:
Fix:
Validation:
```

Do not change several components at the same time unless there is a
specific reason.

The goal is to identify the failing layer.