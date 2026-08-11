---
title : "Clean up AWS Resources"
date : 2026-08-10
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

### Objectives

Upon completing the **NeonFoodMap** workshop exercises and verifying system functionality, you should clean up all AWS resources created during the project. This ensures your AWS account does not incur unintended charges from continuously running resources such as NAT Gateways, ECS Tasks, RDS Instances, or Load Balancers.

### Resource Cleanup Principles

AWS resources often have interdependencies. Therefore, cleanup must be executed in the **strict reverse order** of creation—starting from top-layer applications, CDN, and Load Balancers down to Databases, S3 Storage, and finally the VPC Networking layer.

---

### Step-by-Step Detailed Cleanup Procedure

#### 1. Terminate ECS Services and Draining Tasks (Amazon ECS Fargate)
1. Open the **AWS Management Console** -> search for **Elastic Container Service (ECS)**.
2. Select Cluster `cls-neonfoodmap` (or `NeonFoodmap-cluster`).
3. Under the **Services** tab, select active services: `svc-neonfoodmap-be` and `svc-neonfoodmap-fe`.
4. Click **Update service** -> set **Desired tasks** to `0` -> click **Update**.
5. Once running task count reaches `0`, select the services again -> click **Delete**.
6. Type `delete` in the confirmation dialog -> click **Delete**.
7. Navigate to **Task Definitions**, select `task-neonfoodmap-be` and `task-neonfoodmap-fe` -> select all Revisions -> click **Actions** -> **Deregister**.

---

#### 2. Disable and Delete CDN (Amazon CloudFront Distribution)
1. Navigate to the **CloudFront Console**.
2. Select Distribution `neonfoodmap-frontend-cdn` currently in `Enabled` state.
3. Click **Disable** -> confirm disabling.
4. Wait 3–5 minutes until status changes to `Disabled`.
5. Select the distribution once more -> click **Delete**.

---

#### 3. Delete Application Load Balancer and Target Groups
1. Open the **EC2 Console** -> click **Load Balancers** from the left navigation panel.
2. Select Application Load Balancer `alb-neonfoodmap`.
3. Click **Actions** -> **Delete load balancer** -> confirm deletion.
4. Navigate to **Target Groups**.
5. Select Target Groups `tg-neonfoodmap-be` and `tg-neonfoodmap-fe`.
6. Click **Actions** -> **Delete** -> confirm **Yes, delete**.

---

#### 4. Delete Amazon RDS MySQL Database
1. Open the **Amazon RDS Console** -> click **Databases**.
2. Select DB Instance `rds-neonfoodmap-db`.
3. Click **Actions** -> **Delete**.
4. In the deletion confirmation screen:
   - Uncheck **Create final snapshot?** (unless a backup is needed).
   - Check **I acknowledge that upon database deletion, Automated backups...**.
   - Type `delete me` into the text box -> click **Delete**.
5. Navigate to **Subnet groups** -> select DB Subnet Group `dbsg-neonfoodmap` -> click **Delete**.

---

#### 5. Empty and Delete Amazon S3 Buckets
1. Open the **Amazon S3 Console**.
2. For each bucket (`neon-food-map-frontend`, `neon-food-map-media`, `neon-food-map-audio`, `neon-food-map-logs`):
   - Click the bucket name -> click **Empty**.
   - Type `permanently delete` -> click **Empty** to wipe all stored objects and log files.
   - Once emptied, return to Buckets list -> select the bucket -> click **Delete**.
   - Type the full bucket name to confirm -> click **Delete bucket**.

---

#### 6. Delete Amazon ECR Repositories
1. Open the **Amazon ECR Console** -> select **Repositories**.
2. Select repositories `neon-food-map-backend` and `neon-food-map-frontend`.
3. Click **Delete**.
4. Type `delete` in the confirmation box to erase the repositories and all contained Docker images.

---

#### 7. Delete CloudWatch Alarms, Dashboards & AWS Budgets
1. Open the **Amazon CloudWatch Console**.
2. **Dashboards**: select `NeonFoodMap-Operational-Dashboard` -> click **Delete dashboard**.
3. **Alarms**: select alarms `ALB-5XX-Error-Alarm`, `ECS-CPU-Alarm` -> click **Actions** -> **Delete**.
4. **Log groups**: select log groups `/ecs/neon-food-map`, `/aws/alb/neonfoodmap` -> click **Actions** -> **Delete log group**.
5. Open the **AWS Budgets Console** -> select the budget alert -> click **Delete**.

---

#### 8. Delete CloudFormation Stacks & IAM Roles
1. Open the **AWS CloudFormation Console**.
2. Select Stack `NeonFoodMap-IAM-Stack` -> click **Delete** -> confirm **Delete stack**.
3. If created manually in **IAM Console**:
   - Under **Roles**: delete `ECS-TaskExecutionRole`, `ECS-TaskRole`, and `GitHubActions-ECR-ECS-DeployRole`.
   - Under **Identity Providers**: select OIDC provider `token.actions.githubusercontent.com` -> click **Delete**.

---

#### 9. Delete NAT Gateway, Elastic IP, and Amazon VPC
1. Open the **Amazon VPC Console**.
2. **NAT Gateways**: select the NAT Gateway in the Public Subnet -> click **Actions** -> **Delete NAT gateway**.
3. **Elastic IPs**: select the Elastic IP allocated to the NAT Gateway -> click **Actions** -> **Release Elastic IP addresses**.
4. **Security Groups**: delete custom Security Groups `sg-rds-mysql`, `sg-ecs-backend`, `sg-alb` (detach dependencies first).
5. **Your VPCs**: select VPC `vpc-neonfoodmap` -> click **Actions** -> **Delete VPC**.
   - AWS will automatically delete all attached Subnets, Route Tables, Internet Gateways, and Network ACLs belonging to this VPC.

---

### Verification of Complete Cleanup

Once all 9 steps are finished, verify via the **AWS Billing & Cost Management Dashboard** or **Resource Groups & Tag Editor** to ensure no paid active resources remain running in your account.
