---
title: "Week 4 Worklog"
date: 2026-07-13
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

- SPRINT 1: Foundation & Infrastructure.
- DevOps & Integration, build AWS foundation (VPC, RDS, S3, ECR, IAM).

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Setup VPC Multi-AZ (Public/Private subnets, IGW, NAT) | 13/07/2026 | 13/07/2026 | |
| 3 | - Provision RDS MySQL in private subnet | 14/07/2026 | 14/07/2026 | |
| 4 | - Setup S3 Buckets, Lifecycle rules, and IAM Roles via CloudFormation | 15/07/2026 | 15/07/2026 | |
| 5 | - Dockerize Frontend & Backend applications | 16/07/2026 | 16/07/2026 | |
| 6 | - Setup ECR and push Docker Images | 17/07/2026 | 17/07/2026 | |

### Week 4 Achievements:

- Completed SPRINT 1 by successfully deploying the foundational Multi-AZ VPC architecture, properly segregating Public/Private subnets, IGW, and NAT Gateway.
- Provisioned and secured Amazon RDS MySQL inside a Private Subnet, ensuring network-level data isolation and security.
- Configured dedicated S3 Buckets (for Frontend, Media, Audio, and Logs) along with Lifecycle policies to optimize long-term storage costs.
- Utilized CloudFormation to automate the creation of IAM Roles and enforced strict IAM security best practices.
- Finalized Dockerfiles for the Frontend and Backend applications, and successfully pushed the container images to Amazon ECR.
