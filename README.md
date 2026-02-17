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

### Cost Optimization (3 Questions)

| ID | Topic |
|----|-------|
| cost_q1 | Cost monitoring and management (CUDOS, Cost Explorer) |
| cost_q2 | Sandbox environment cost and lifecycle management |
| cost_q3 | Third-party software procurement (Private Marketplace, License Manager) |

### Performance Efficiency (3 Questions)

| ID | Topic |
|----|-------|
| performance_q1 | AWS Organization structure design |
| performance_q2 | Network connectivity for new accounts (Transit Gateway) |
| performance_q3 | IPAM and CIDR range management |

## Risk Levels

Each question uses risk rules to evaluate your current posture:

| Risk Level | Meaning |
|------------|---------|
| NO_RISK | All recommended practices are in place |
| MEDIUM_RISK | Partial implementation; key areas need improvement |
| HIGH_RISK | Critical gaps; immediate action recommended |

## How to Use

### Import the Custom Lens

1. Sign in to the [AWS Management Console](https://console.aws.amazon.com/)
2. Navigate to the [AWS Well-Architected Tool](https://console.aws.amazon.com/wellarchitected/)
3. In the left navigation pane, click **Custom lenses**
4. Click **Create custom lens**
5. Under **JSON file**, click **Choose file** and select `Custom_lens_Landingzone.json`
6. Click **Submit and create**
7. The lens will appear in your custom lenses list with a status of **DRAFT**

### Publish the Lens

1. In **Custom lenses**, select the newly created lens
2. Click **Publish lens**
3. Enter a version name (e.g., `1.0.0`) and an optional description of changes
4. Click **Publish**
5. The lens status will change to **PUBLISHED** and is now available for workload reviews

### Share the Lens Across Accounts (Optional)

To use this lens in other AWS accounts within your organization:

1. In **Custom lenses**, select the published lens
2. Click **Shares** tab, then **Create share**
3. Choose to share with individual AWS account IDs or your entire AWS Organization
4. The receiving accounts must accept the share before the lens becomes available in their console
5. Shared lenses appear under **Custom lenses** in the receiving account

### Create a Workload Review

1. In the Well-Architected Tool, go to **Workloads**
2. Create a new workload or select an existing one
3. Under **Lenses**, apply the **Landing Zone lens**
4. Answer each question based on your current implementation
5. Review the generated improvement plan


## File Structure

```
├── Custom_lens_Landingzone.json   # The custom lens definition
└── README.md                      # This file
```

## Schema

This lens follows the [AWS Well-Architected Custom Lens schema](https://docs.aws.amazon.com/wellarchitected/latest/userguide/lenses-format-specification.html) version `2021-11-01`.

## Key AWS Services Referenced

- AWS Organizations, Control Tower, Service Control Policies
- IAM Identity Center, IAM Access Analyzer
- AWS Config, Security Hub, GuardDuty
- CloudTrail, CloudWatch, EventBridge
- AWS Backup, Systems Manager (Patch Manager, Inventory, Maintenance Windows)
- VPC IPAM, Transit Gateway, Network Firewall
- EC2 Image Builder, Service Catalog
- AWS Cost Explorer, AWS Budgets, License Manager
- AWS Health, Amazon Macie

## Contributing

When adding or modifying questions:

1. Follow the existing JSON structure and naming conventions (`<pillar>_q<number>`)
2. Each choice must include a `helpfulResource` with a `displayText` (and optionally a `url`) and an `improvementPlan`
3. Risk rules should use only `NO_RISK`, `MEDIUM_RISK`, and `HIGH_RISK` levels
4. Always include a `default` condition as the last risk rule for catch-all coverage
5. Run `check_urls.sh` after adding new URLs to verify they are valid
6. Validate the JSON syntax before committing (e.g., `python3 -m json.tool Custom_lens_Landingzone.json`)
