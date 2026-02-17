# AWS Landing Zone Custom Lens

A custom lens for the [AWS Well-Architected Tool](https://aws.amazon.com/well-architected-tool/) focused on best practices for designing, implementing, and managing AWS Landing Zones. It addresses key considerations specific to multi-account environments, account lifecycle management, and organizational governance.

## Overview

This lens provides a structured review framework across **4 pillars** with **28 questions** to evaluate the maturity of your AWS Landing Zone implementation.

| Pillar | Questions | Focus Areas |
|--------|-----------|-------------|
| Operational Excellence | 10 | Logging, observability, tagging, patching, Service Catalog, backup, resource inventory, health notifications, alternate contacts |
| Security | 12 | IAM Identity Center, federation strategy, compliance, data classification, incident response, emergency access, CloudTrail, golden AMIs, region restrictions, security baselines, security groups |
| Cost Optimization | 3 | Cost dashboards, sandbox lifecycle, third-party software procurement |
| Performance Efficiency | 3 | Organization structure, network connectivity, IPAM/CIDR management |

## Pillar Details

### Operational Excellence (10 Questions)

| ID | Topic |
|----|-------|
| operational_q1 | Centralized logging across the Landing Zone |
| operational_q2 | Observability baselines per Organizational Unit |
| operational_q3 | Organization-wide metrics aggregation and visualization |
| operational_q4 | Tagging strategy enforcement |
| operational_q5 | Centralized patch management |
| operational_q6 | AWS Service Catalog for standardized provisioning |
| operational_q7 | Backup policy enforcement across all accounts |
| operational_q8 | Centralized resource inventory using AWS Config |
| operational_q9 | AWS Health notification dashboard |
| operational_q10 | Alternate contact management |

### Security (12 Questions)

| ID | Topic |
|----|-------|
| security_q1 | Centralized IAM Identity Center |
| security_q2 | IAM strategy (federated vs. native, IdP, SSO) |
| security_q3 | Centralized compliance management |
| security_q4 | Compliance standards across the Landing Zone |
| security_q5 | Data classification |
| security_q6 | Automated incident response |
| security_q7 | Emergency access / break glass accounts |
| security_q8 | CloudTrail log storage and retention |
| security_q9 | Approved AMIs (Golden Images) enforcement |
| security_q10 | Region restriction enforcement |
| security_q11 | Security baseline (GuardDuty, Security Hub, VPC Flow Logs) |
| security_q12 | Default security group rules standardization |
