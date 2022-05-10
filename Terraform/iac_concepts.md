---
title: IaC Concepts
parent: Terraform
nav_order: 1
---

# What is IaC?

- Infrastructure as a code
- Automate creation update or destroying cloud infra
- Allows to share, version infrastructure

Manually is faster (the first time) but
- Can be configured wrong
- Difficult to transmit config knowledge

# Some IaC tools

- Two categories
- Declarative
  - Explicit
  - Scripting language JSON YAML HCL etc
  - ARM Templates and Azure Blueprints (Azure)
  - CloudFormation (AWS)
  - Cloud Deployment Manager (Google)
  - Terraforms (Multi)
- Imperative
  - Implicite (Say what you want the rest is filled in)
  - Less Verbose (easy to misconfigure)
  - Can do more
  - Programming languages Python, go, etc.
  - AWS CDK
  - Pulumi(Multi)

> Terraform sits kind of in the middle of the two because even tough is based on HCL, it supports loops, dynamic blocks, variables and complex data structures like maps