---
title: "Week 4 Worklog"
date: 2026-07-13
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

- **SPRINT 1: Foundation & Infrastructure**.
- Build foundational AWS cloud infrastructure (VPC Multi-AZ, Amazon RDS MySQL Multi-AZ, S3 Buckets, IAM CloudFormation templates, Dockerization & ECR repositories).

### Tasks Executed During the Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon | - Provision Multi-AZ VPC (Public/Private Subnets, IGW, NAT Gateway & Route Tables) | 13/07/2026 | 13/07/2026 | |
| Tue | - Deploy Amazon RDS MySQL 8.0 Multi-AZ in Private Subnet & configure Security Groups | 14/07/2026 | 14/07/2026 | |
| Wed | - Setup 4 S3 Buckets, S3 Lifecycle Policies & automate IAM Roles via CloudFormation | 15/07/2026 | 15/07/2026 | |
| Thu | - Dockerize ReactJS Frontend & Django REST Backend applications | 16/07/2026 | 16/07/2026 | |
| Fri | - Create Amazon ECR Repositories, authenticate CLI & push Docker Images to ECR | 17/07/2026 | 17/07/2026 | |

### Detailed Daily Execution Breakdown:

- **Monday (13/07/2026):** **Commenced SPRINT 1 (Foundation & Infrastructure)**. Provisioned Amazon VPC Multi-AZ (`10.0.0.0/16`) in Singapore (`ap-southeast-1`). Created 2 Public Subnets (`10.0.1.0/24`, `10.0.2.0/24`), 2 Private Subnets (`10.0.10.0/24`, `10.0.20.0/24`), 1 Internet Gateway (IGW), 1 NAT Gateway in Public Subnet 1, and configured respective Route Tables.
- **Tuesday (14/07/2026):** Configured DB Subnet Group across Private Subnets; provisioned Amazon RDS MySQL 8.0 Multi-AZ (`db.t3.micro`). Configured Security Group `sg-rds-mysql` with inbound rules allowing MySQL port 3306 exclusively from Backend Security Group `sg-ecs-backend`.
- **Wednesday (15/07/2026):** Created 4 Amazon S3 Buckets (`neon-food-map-frontend`, `neon-food-map-media`, `neon-food-map-audio`, `neon-food-map-logs`). Configured S3 Lifecycle rules transitioning logs to S3 Standard-IA after 30 days and Glacier after 90 days. Wrote AWS CloudFormation YAML template to automate IAM Role creation (`ECS-TaskExecutionRole` & `ECS-TaskRole`) adhering to least privilege.
- **Thursday (16/07/2026):** Application Containerization (Dockerize): authored optimized Dockerfiles for Django Backend (`python:3.11-slim` with WSGI Gunicorn) and React Frontend (multi-stage build with Nginx web server). Tested local image builds.
- **Friday (17/07/2026):** Created 2 repositories on Amazon ECR (`neon-food-map-backend` and `neon-food-map-frontend`). Authenticated ECR CLI (`aws ecr get-login-password`), tagged local images, and successfully pushed Docker Images to ECR repos, completing Sprint 1 ahead of schedule.

### Week 4 Achievements:

- Completed SPRINT 1 by successfully deploying the foundational Multi-AZ VPC architecture, properly segregating Public/Private subnets, IGW, and NAT Gateway.
- Provisioned and secured Amazon RDS MySQL inside a Private Subnet, ensuring network-level data isolation and security.
- Configured 4 dedicated S3 Buckets (for Frontend, Media, Audio, and Logs) along with Lifecycle policies to optimize long-term storage costs.
- Utilized CloudFormation to automate the creation of IAM Roles and enforced strict IAM security best practices.
- Finalized Dockerfiles for the Frontend and Backend applications, and successfully pushed the container images to Amazon ECR repositories.

