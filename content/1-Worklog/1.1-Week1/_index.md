---
title: "Week 1 Worklog"
date: 2026-06-22
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

- Understand AWS Global Infrastructure fundamentals and IAM security best practices.
- Initialize project scope, analyze business requirements, and design the NeonFoodMap system architecture.

### Tasks Executed During the Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon | - Attend FCAJ Onboarding at AWS Vietnam office (Bitexco) <br> - Learn AWS Global Infrastructure (Region, AZ, Edge) & IAM Best Practices | 22/06/2026 | 22/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Tue | - Study core AWS services: VPC, EC2, S3, RDS <br> - Setup AWS Free Tier account, configure AWS CLI & verify IAM credentials | 23/06/2026 | 23/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Discuss and finalize project topic (**NeonFoodMap**) <br> - Analyze business requirements and core features (POI Search, Audio Commentary) | 24/06/2026 | 24/06/2026 | |
| Thu | - Select and define AWS deployment components and service architecture | 25/06/2026 | 25/06/2026 | |
| Fri | - Design overall system architecture diagram & Data Flow Diagram (DFD) | 26/06/2026 | 26/06/2026 | |

### Detailed Daily Execution Breakdown:

- **Monday (22/06/2026):** Attended the FCAJ orientation session at AWS Vietnam (26th floor, Bitexco Financial Tower). Studied AWS Global Infrastructure concepts: Region (`ap-southeast-1` Singapore), Availability Zones (Multi-AZ resilience), and Edge Locations. Learned AWS IAM Best Practices: locking root user access keys, enforcing Multi-Factor Authentication (MFA), creating dedicated IAM Admin Users, and applying the Principle of Least Privilege.
- **Tuesday (23/06/2026):** Explored core AWS cloud service pillars: Compute (EC2, ECS), Storage (S3, EBS), Networking (VPC), Database (RDS). Successfully created an AWS Free Tier account with MFA protection. Installed and configured AWS CLI on local machine (`aws configure` with region `ap-southeast-1` and output `json`), verifying identity via `aws sts get-caller-identity`.
- **Wednesday (24/06/2026):** Conducted team brainstorming session and selected project topic: **NeonFoodMap**—an interactive food location application featuring real-time GPS tracking, radius POI search, and automated text-to-speech audio commentaries. Defined functional and non-functional requirements (high availability Multi-AZ, scalability, OIDC security).
- **Thursday (25/06/2026):** Mapped application requirements to AWS services: Amazon VPC Multi-AZ (Public/Private subnets, IGW, NAT Gateway), Amazon RDS MySQL 8.0, Amazon S3 Buckets, Amazon ECS Fargate container orchestration, Amazon CloudFront CDN, and Amazon CloudWatch monitoring.
- **Friday (26/06/2026):** Designed the system Architecture Diagram and Data Flow Diagram (DFD Level 0 & Level 1) using Draw.io. Presented Week 1 progress report to AWS technical mentors.

### Week 1 Achievements:

- Mastered foundational AWS concepts and Global Infrastructure components including Regions, Availability Zones, and Edge Locations.
- Clearly differentiated the roles of core services such as Compute (EC2, ECS), Storage (S3, EBS), Networking (VPC), and Database (RDS MySQL).
- Successfully set up and secured an AWS Free Tier account, practicing the principle of least privilege using IAM.
- Became proficient with the AWS Management Console and configured the AWS CLI to interact with AWS resources from the command line.
- Defined the NeonFoodMap project topic, completed business requirement gathering, and drafted the initial Data Flow Diagram (DFD) and system architecture.

