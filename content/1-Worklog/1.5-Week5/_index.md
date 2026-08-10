---
title: "Week 5 Worklog"
date: 2026-07-20
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

- SPRINT 2: CI/CD Pipeline & Deployment.
- Automate deployment with GitHub Actions and setup ECS, ALB.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Build GitHub Actions CI/CD pipeline (OIDC auth, build, push ECR) | 20/07/2026 | 20/07/2026 | |
| 3 | - Setup ECS cluster (Fargate) and task definitions | 21/07/2026 | 21/07/2026 | |
| 4 | - Configure ALB, Target Groups, and Health Checks | 22/07/2026 | 22/07/2026 | |
| 5 | - Django AWS Configuration (RDS connect, static files) | 23/07/2026 | 23/07/2026 | |
| 6 | - React AWS Configuration (API URL, build args) | 24/07/2026 | 24/07/2026 | |

### Week 5 Achievements:

- Completed SPRINT 2 by establishing an automated CI/CD pipeline via GitHub Actions, implementing secure OIDC authentication with AWS.
- Successfully configured the Amazon ECS cluster (Fargate) and defined Task Definitions with optimized CPU and Memory allocations for the application.
- Deployed an Application Load Balancer (ALB) with Target Groups and configured Health Checks to accurately route traffic and ensure high availability.
- Adjusted Django configurations to securely connect to the RDS database and serve static files directly from S3.
- Modified the React Frontend to dynamically consume the API URL via build arguments, enabling seamless communication with the Backend through the ALB.
