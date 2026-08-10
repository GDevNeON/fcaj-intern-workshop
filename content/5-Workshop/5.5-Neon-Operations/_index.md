---
title : "NeonFoodMap Operations and Monitoring"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

### Objectives

In this section, you will operate and test the NeonFoodMap system following a clear end-to-end flow. The content is organized step by step — from creating ECS services, enabling auto-scaling, configuring CloudFront, setting up CloudWatch, to testing the complete user workflow and cleaning up resources if needed.

### Operations Flow Overview

The implementation flow consists of the following main stages:

1. Initialize ECS service and configure rolling update
2. Enable auto-scaling for the backend service
3. Configure CloudFront to serve the frontend and proxy the API
4. Monitor resources using CloudWatch dashboard and alarms
5. Set up log retention, VPC Flow Logs, and cost monitoring
6. Run end-to-end testing on critical user flows
7. Clean up resources when finished
