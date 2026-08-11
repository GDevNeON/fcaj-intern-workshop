---
title: "Week 7 Worklog"
date: 2026-08-03
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

- **SPRINT 3: Scaling, Monitoring & Go-Live (Part 2)**.
- Execute End-to-End Testing, Load Testing with Locust (1,000 concurrent users), QA Debugging, RDS Failover drill & Production Go-Live.

### Tasks Executed During the Week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon | - Execute End-to-End Testing on critical user workflows in Staging environment | 03/08/2026 | 03/08/2026 | |
| Tue | - Perform Load Testing with Locust (simulating 1,000 concurrent users) & verify Auto-Scaling | 04/08/2026 | 04/08/2026 | |
| Wed | - Investigate, debug and resolve QA phase issues via CloudWatch Log Insights | 05/08/2026 | 05/08/2026 | |
| Thu | - Validate Real-time Error Tracking & conduct simulated RDS Multi-AZ Failover drill | 06/08/2026 | 06/08/2026 | |
| Fri | - Execute official Production Go-Live & observe real-time system stability | 07/08/2026 | 07/08/2026 | |

### Detailed Daily Execution Breakdown:

- **Monday (03/08/2026):** **Commenced SPRINT 3 (Part 2: QA, Load Testing & Production Go-Live)**. Performed comprehensive End-to-End (E2E) user journey testing on Staging: User Registration/Authentication, GPS radius POI search, AWS Polly automatic audio playback, food tour booking, and payment processing.
- **Tuesday (04/08/2026):** Executed Load Testing using Locust simulating `1,000 concurrent users`. Observed metrics: as CPU utilization spiked to `78%`, ECS Target Tracking Auto-Scaling triggered, scaling out 2 additional ECS Tasks within 45 seconds, reducing average CPU load to `45%` while keeping HTTP 5xx error rate at `0%`.
- **Wednesday (05/08/2026):** Utilized CloudWatch Logs Insights to analyze test logs, identifying and fixing minor QA bottlenecks: optimized POI search API response latency, adjusted Database Connection Pool limits, and tuned ALB Target Group HTTP timeouts.
- **Thursday (06/08/2026):** Validated Real-time Error Tracking alerting mechanisms. Conducted simulated Availability Zone failure drill to verify Amazon RDS MySQL Multi-AZ automatic failover, confirming zero data loss and database reconnect in under 60 seconds.
- **Friday (07/08/2026):** Executed official **Production Go-Live**. Maintained continuous observation via CloudWatch Dashboards, confirming 100% stable operation with zero downtime and achieving High Availability (99.99%).

### Week 7 Achievements:

- Completed SPRINT 3 (Part 2) by successfully performing End-to-End (E2E) testing on critical user flows to ensure system reliability.
- Conducted Load testing with Locust (1,000 users), evaluating system endurance and validating Auto-Scaling performance in pulling CPU load back to a safe 45% with 0% 5xx errors.
- Quickly identified and resolved bugs discovered during the QA phase, optimizing Database Connection Pooling and API Target Response Time.
- Verified that Real-time Error Tracking via CloudWatch and RDS Multi-AZ automatic failover functioned seamlessly under 60 seconds.
- Successfully executed the Production Go-Live, closely observing system stability and ensuring zero downtime during operations.

