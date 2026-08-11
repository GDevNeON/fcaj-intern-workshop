---
title: "Week 6 Worklog"
date: 2026-07-27
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

- **SPRINT 3: Scaling, Monitoring & Go-Live (Part 1)**.
- Configure automatic ECS Service Auto-Scaling, Amazon CloudFront CDN, CloudWatch Dashboards, Log Insights & AWS Budgets Cost Control.

### Tasks Executed During the Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon | - Configure ECS Service Auto-Scaling policies (Target Tracking 70% CPU, min 2, max 6 tasks) | 27/07/2026 | 27/07/2026 | |
| Tue | - Setup CloudFront CDN for high-speed edge distribution of Frontend, Media & Audio assets | 28/07/2026 | 28/07/2026 | |
| Wed | - Build real-time CloudWatch Monitoring Dashboard & configure SNS Alarms for HTTP 5xx errors | 29/07/2026 | 29/07/2026 | |
| Thu | - Integrate AWS Budgets with $30.00/month limit & automated email cost alerts via SNS | 30/07/2026 | 30/07/2026 | |
| Fri | - Configure CloudWatch Logs Insights & author reusable query snippets for log analysis | 31/07/2026 | 31/07/2026 | |

### Detailed Daily Execution Breakdown:

- **Monday (27/07/2026):** **Commenced SPRINT 3 (Part 1: Scaling, Monitoring & Cost Control)**. Configured Target Tracking Scaling policy for Backend ECS Service based on average CPU utilization metric. Set target metric value to `70%`, task capacity range between minimum `2 tasks` and maximum `6 tasks`, with a scale-down cooldown of `300s`.
- **Tuesday (28/07/2026):** Provisioned Amazon CloudFront CDN Distribution targeting ALB Endpoint and S3 Buckets as origins. Optimized Cache Behaviors for static assets (JS/CSS), media images, and Polly audio files (.mp3) with 24-hour TTL at Edge Locations. Reduced page load latency from 3.5s to 1.2s and reduced origin server load by over 60%.
- **Wednesday (29/07/2026):** Built centralized CloudWatch Dashboard visualizing core performance telemetry: ECS Fargate CPU/Memory Utilization, ALB Target Response Time, total HTTP Requests/min, and HTTP 4xx/5xx error counts. Integrated CloudWatch Alarms with Amazon SNS to trigger instant email notifications upon detecting >5 HTTP 5xx errors within a 1-minute window.
- **Thursday (30/07/2026):** Implemented automated cost governance via AWS Budgets. Set fixed monthly budget limit of `$30.00`, configuring SNS email alerts when actual costs reach 80% ($24.00) or when forecasted monthly cost exceeds 100%.
- **Friday (31/07/2026):** Centralized log ingestion across Backend/Frontend ECS tasks using CloudWatch Logs Insights. Authored and saved custom Log Insights query snippets to analyze root causes of HTTP 500 exceptions, slow RDS SQL queries, and API response time distributions.

### Week 6 Achievements:

- Completed SPRINT 3 (Part 1) by successfully configuring Auto-Scaling policies for ECS Services, enabling automatic scaling based on CPU/Memory utilization.
- Integrated Amazon CloudFront CDN to effectively cache static assets (Media and Frontend) at Edge Locations, significantly improving page load speeds.
- Built a comprehensive monitoring Dashboard on Amazon CloudWatch, configuring essential metrics and SNS alarms to notify on system performance issues.
- Optimized centralized logging by configuring CloudWatch Logs and utilizing Log Insights to query and analyze application logs efficiently.
- Deployed a cost monitoring system using AWS Budgets & Alerts to proactively control and prevent unexpected charges during project operations.

