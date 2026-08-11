---
title: "Week 5 Worklog"
date: 2026-07-20
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

- **SPRINT 2: CI/CD Pipeline & Deployment**.
- Automate CI/CD pipeline using GitHub Actions with secure OIDC authentication, provision Amazon ECS Fargate cluster, and Application Load Balancer (ALB).

### Tasks Executed During the Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon | - Author GitHub Actions CI/CD workflow (passwordless OIDC auth, build, push ECR & deploy ECS) | 20/07/2026 | 20/07/2026 | |
| Tue | - Configure Amazon ECS Cluster (Serverless Fargate) and define ECS Task Definitions | 21/07/2026 | 21/07/2026 | |
| Wed | - Provision Application Load Balancer (ALB), Target Groups & configure Health Check paths | 22/07/2026 | 22/07/2026 | |
| Thu | - Configure Django Backend RDS MySQL connection & S3 bucket static/media storage | 23/07/2026 | 23/07/2026 | |
| Fri | - Configure React Frontend dynamic API URL via Docker build args & test end-to-end CI/CD | 24/07/2026 | 24/07/2026 | |

### Detailed Daily Execution Breakdown:

- **Monday (20/07/2026):** **Commenced SPRINT 2 (CI/CD Pipeline & Deployment)**. Established OpenID Connect (OIDC) federation between GitHub Actions and AWS IAM. Created IAM Identity Provider `token.actions.githubusercontent.com` and IAM Role `GitHubActions-ECR-ECS-DeployRole` with trust relationship restricted to repo `gdevneon/fcaj-intern-workshop` and `main` branch. Authored `.github/workflows/deploy.yml` for automated building, pushing to ECR, and triggering ECS deployment.
- **Tuesday (21/07/2026):** Created Amazon ECS Cluster (`cls-neonfoodmap`) using AWS Fargate serverless launch type. Authored ECS Task Definitions for Backend (`0.5 vCPU`, `1GB RAM`) and Frontend (`0.25 vCPU`, `0.5GB RAM`), configuring `awslogs` log driver to send stdout/stderr to CloudWatch Log Group `/ecs/neon-food-map`.
- **Wednesday (22/07/2026):** Deployed Application Load Balancer `alb-neonfoodmap` across Public Subnets. Created Target Group `tg-neonfoodmap-be` (port 8000, Health Check `/api/health/`) and Target Group `tg-neonfoodmap-fe` (port 80, Health Check `/`). Configured ALB Listener rules routing path pattern `/api/*` to Backend and `/` to Frontend.
- **Thursday (23/07/2026):** Configured Django Backend ECS Tasks: injected environment variables for Private Subnet RDS MySQL connection (`DB_HOST`, `DB_NAME`, `DB_USER`, `DB_PASSWORD`), integrated `django-storages` and `boto3` for direct S3 media/static asset handling.
- **Friday (24/07/2026):** Configured React Frontend to accept dynamic API Endpoint URL via Docker build args. Conducted 100% automated CI/CD pipeline verification: git push to `main` branch triggered GitHub Actions, automatically built images, pushed to ECR, and completed Rolling Update on ECS Fargate in under 3 minutes.

### Week 5 Achievements:

- Completed SPRINT 2 by establishing an automated CI/CD pipeline via GitHub Actions, implementing secure OIDC authentication with AWS STS.
- Successfully configured the Amazon ECS cluster (Fargate) and defined Task Definitions with optimized CPU and Memory allocations for the application.
- Deployed an Application Load Balancer (ALB) with Target Groups and configured Health Checks to accurately route traffic and ensure high availability.
- Adjusted Django configurations to securely connect to the RDS database and serve static/media files directly from S3.
- Modified the React Frontend to dynamically consume the API URL via build arguments, enabling seamless communication with the Backend through the ALB.

