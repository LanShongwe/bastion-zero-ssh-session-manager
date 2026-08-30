# Troubleshooting

## Troubleshooting principle

Troubleshoot from the workload outward.

```text
           EC2
            |
            v
     Security Group
            |
            v
          Subnet
            |
            v
      Route Table
            |
            v
  NAT / Internet Gateway
            |
            v
        AWS service
```

Do not randomly change multiple settings at once.

## Session Manager unavailable

Check:

```text
sudo systemctl status amazon-ssm-agent
```

Then check:

- EC2 instance state
- IAM role
- Systems Manager permissions
- SSM Agent
- subnet
- route table
- outbound security-group rules
- NAT Gateway
- general network connectivity

## Instance not appearing in Systems Manager

Check:

```text
           EC2 running?
                |
                v
        IAM role attached?
                |
                v
        SSM Agent running?
                |
                v
      Outbound connectivity?
                |
                v
  Systems Manager communication?
```

## SSH connection fails

First ask:
```text
Should SSH work?
```
For this project, normal administration does not depend on SSH.

Therefore:

```text
SSH unavailable
     ≠
project failure
```
It can be an expected security result.

## Private instance has no internet connectivity

Check in order:

1. Private subnet association.
2. Private route table.
3. Default route.
4. NAT Gateway.
5. Public subnet route.
6. Internet Gateway.
7. Security-group outbound rules.

Expected path:

```text
            Private EC2
                |
                v
        Private Route Table
                |
                v
            NAT Gateway
                |
                v
         Internet Gateway
                |
                v
            Internet
```
## Useful diagnostic commands

```bash
ip addr
ip route
hostname
cat /etc/resolv.conf
ping <known-target>
curl -I https://example.com
```

Use these carefully and understand what each test proves.

## General rule

Change one thing at a time.

Record:

```text
Problem
Observation
Hypothesis
Test
Result
Fix
Validation
```