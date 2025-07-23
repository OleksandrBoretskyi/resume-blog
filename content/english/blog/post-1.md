---
title: "Securing Your Infrastructure with a Bastion Host on AWS"
meta_title: "How to set up a Bastion Host using Terraform"
description: "Learn how to deploy a secure Bastion Host on AWS using Terraform and control SSH access to private instances."
date: 2025-07-23T08:00:00Z
image: "/images/bastion-host-cover.png"
categories: ["Infrastructure", "Security"]
author: "Oleksandr Boretskyi"
tags: ["aws", "terraform", "bastion", "devops"]
draft: false
---

A Bastion Host is a critical security component used to securely access private resources within a cloud network. In this post, I’ll show you how I implemented a Bastion Host on AWS using Terraform, as part of a minimal but production-grade setup.

Private EC2 instances should not be exposed to the internet directly. Instead, a Bastion Host acts as a secure entry point, allowing controlled SSH access only to specific users.

## Project Goal

The goal of this project was to demonstrate how to create a secure infrastructure setup where private instances are only accessible via a Bastion Host. The setup was automated using Terraform and includes security groups, subnets, and routing logic.

> SSH access to private servers is only allowed through the Bastion Host, reducing the attack surface.

## Key Components

- **AWS EC2**: A t3.micro instance used as the Bastion Host.
- **VPC & Subnets**: One public and one private subnet with correct routing.
- **Security Groups**: Restrictive rules allowing SSH only from trusted IPs.
- **Terraform**: All infrastructure as code.
- **Cost Tags**: Tags like `Project=bastion-host` and `Environment=dev` for tracking costs.

## Deployment

To deploy the setup, simply clone the repo and run:

```bash
terraform init
terraform apply
