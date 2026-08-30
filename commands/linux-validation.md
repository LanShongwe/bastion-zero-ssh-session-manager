# Linux Validation Quick Reference

## Identity

```bash
whoami
id
```

## Host information

```bash
hostname
hostnamectl
uname -a
```

## IP configuration

```bash
ip addr
```

## Routing

```bash
ip route
```

## DNS

```bash
cat /etc/resolv.conf
```

## Check listening ports

```bash
sudo ss -tulpn
```

## Check SSM Agent

```bash
sudo systemctl status amazon-ssm-agent
```

## Restart SSM Agent

```bash
sudo systemctl restart amazon-ssm-agent
```

## Check SSM Agent logs

```bash
sudo journalctl -u amazon-ssm-agent
```

## Disk usage

```bash
df -h
```

## Memory

```bash
free -h
```

## CPU/processes

```bash
top
```

or:

```bash
ps aux
```

## Connectivity test

```bash
curl -I https://example.com
```

## Quick system check

```bash
hostname
whoami
ip addr
ip route
df -h
free -h
```

## Troubleshooting principle

Do not run commands randomly.

Ask what layer you are testing:

```text
         Identity
            ↓
            OS
            ↓
         Network
            ↓
            DNS
            ↓
          Service
```