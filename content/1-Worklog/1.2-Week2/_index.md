---
title: "Week 2 Worklog"
date: 2026-06-29
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

- Deep dive into AWS deployment services (RDS, ECS Fargate, ECR, CloudWatch, ALB, OIDC).
- Finalize detailed system architecture design and automated secure CI/CD pipeline strategy.

### Tasks Executed During the Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon | - Study RDS, ECS/ECR and Container Service architecture (Fargate vs EC2 Launch Type) | 29/06/2026 | 29/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Tue | - Explore CloudWatch (Logs, Metrics, Alarms), Application Load Balancers (ALB) & Target Groups | 30/06/2026 | 30/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Select optimal AWS service stack for NeonFoodMap system | 01/07/2026 | 01/07/2026 | |
| Thu | - Finalize detailed Multi-AZ VPC network deployment architecture (Milestone 1) | 02/07/2026 | 02/07/2026 | |
| Fri | - Define CI/CD workflow & deployment strategy utilizing OIDC authentication | 03/07/2026 | 03/07/2026 | |

### Detailed Daily Execution Breakdown:

- **Monday (29/06/2026):** Researched containerization technology (Docker) and AWS container orchestration solutions: Amazon ECS (Elastic Container Service) with EC2 Launch Type vs Serverless Fargate, and Amazon ECR (Elastic Container Registry). Evaluated AWS Fargate advantages in eliminating server management overhead (OS patching, capacity management).
- **Tuesday (30/06/2026):** Analyzed Amazon RDS MySQL 8.0 Multi-AZ deployment (synchronous replication to standby instance in second AZ, automatic failover under 60 seconds); studied Application Load Balancer (ALB) HTTP/HTTPS traffic routing, target groups, and Amazon CloudWatch observability (Metrics, Log Groups, Alarms).
- **Wednesday (01/07/2026):** Finalized service selection for NeonFoodMap: RDS MySQL in Private Subnets for RDBMS, Amazon S3 for static assets and Polly audio files, ECS Fargate for running React Frontend and Django REST Backend, and Amazon CloudFront CDN for global content acceleration.
- **Thursday (02/07/2026):** Locked Amazon VPC network architecture: CIDR `10.0.0.0/16` spanning 2 Availability Zones (`ap-southeast-1a`, `ap-southeast-1b`), comprising Public Subnets (`10.0.1.0/24`, `10.0.2.0/24`) for ALB & NAT Gateways, and Private Subnets (`10.0.10.0/24`, `10.0.20.0/24`) for ECS Tasks & RDS MySQL.
- **Friday (03/07/2026):** Established CI/CD deployment strategy: researched OpenID Connect (OIDC) authentication between GitHub Actions and AWS IAM. Replaced static AWS credentials with short-lived STS tokens issued via GitHub OIDC provider, ensuring enterprise-grade pipeline security.

### Week 2 Achievements:

- Gained a solid understanding of Amazon RDS architecture and its Multi-AZ high availability failover features.
- Comprehended the differences between AWS Container services (ECS vs ECR) and selected AWS Fargate for serverless compute deployment.
- Learned to utilize CloudWatch for system monitoring (Metrics, Logs, Alarms) and understood traffic routing using Application Load Balancers.
- Finalized the detailed system architecture covering Network (VPC, Subnets), Database (RDS), Compute (ECS Fargate), and Storage (S3).
- Established an effective CI/CD strategy, deciding on GitHub Actions with secure OIDC authentication to automate Docker image builds and ECS deployments.

