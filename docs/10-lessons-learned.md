# Lessons Learned

## 1. Network design comes before troubleshooting

A working EC2 instance is not enough.

You need to understand:

```text
VPC
 |
 +-- Subnet
 |
 +-- Route Table
 |
 +-- Security Group
 |
 +-- NAT / IGW
 |
 +-- EC2
 ```

 Each layer affects connectivity differently.

 ## 2. Private does not mean disconnected

A private EC2 instance can still require outbound connectivity.

Private resources can use a NAT Gateway when internet access is required.

## 3. Security groups are not routing

A security group controls network traffic at the instance level.

It does not replace:

- route tables
- NAT Gateway
- Internet Gateway
- subnet design

## 4. IAM is part of infrastructure

The EC2 instance can be running perfectly while Systems Manager access
fails because the IAM configuration is incorrect.

Identity is part of the architecture.

## 5. Removing SSH changes the operational model

Instead of:

```text
         SSH key
            +
         TCP/22
            +
      public access
```

## 6. Troubleshooting requires layers

When something fails, isolate the layer.

```text
        Application
            ↓
            OS
            ↓
           EC2
            ↓
        Security Group
            ↓
          Subnet
            ↓
        Route Table
            ↓
         NAT / IGW
            ↓
        AWS service
```

## 7. Documentation is part of engineering

The project was documented with:

- architecture diagrams
- configuration notes
- screenshots
- validation results
- troubleshooting procedures
- architecture decisions

This makes the environment easier to understand and reproduce.

## 8. The main takeaway

The most important lesson was not how to click through the AWS console.

It was learning to connect:

```text
        Architecture
            +
        Networking
            +
        Security
            +
           IAM
            +
          Linux
            +
        Operations
```
into one working system.