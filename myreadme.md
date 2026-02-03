# Pulumi EC2 Instance Provisioning (AWS)

This repository provisions an AWS EC2 instance using Pulumi (TypeScript) with an enterprise-grade, configuration-driven architecture.

## Features

- EC2 provisioning
- Primary & secondary ENI (public + private subnet)
- Config-driven Security Groups
- Optional Elastic IP
- IAM Role & Instance Profile
- Encrypted EBS volumes
- GitLab CI integration

## Architecture

Resources created:

- EC2 Instance
- Primary ENI (public subnet)
- Optional secondary ENI (private subnet)
- Security Group with dynamic ingress rules
- IAM Role + Instance Profile
- Encrypted EBS root volume
- Optional Elastic IP

## Setup

### Install dependencies

yarn install

### Configure environment

cp example.env .env

### Deploy locally

pulumi preview
pulumi up

### Destroy

pulumi destroy

## Environment Configuration Example

EC2_NAME=EVOTABVPN_PULUMI
VPC_ID=vpc-xxxxxxxx
EC2_AMI_ID=ami-xxxxxxxx
EC2_INSTANCE_TYPE=c7gn.large

EC2_ENABLE_EIP=true
EC2_ENABLE_SECONDARY_ENI=true

EC2_ALLOWED_INGRESS_CIDRS=[
  {
    "ports": { "from": 22, "to": 22 },
    "cidrIps": ["0.0.0.0/0"],
    "ipProtocol": "tcp",
    "description": "SSH Access"
  }
]

## CI/CD

Integrated with GitLab shared templates.

## Maintainers

DevOps / Cloud Infrastructure Team
