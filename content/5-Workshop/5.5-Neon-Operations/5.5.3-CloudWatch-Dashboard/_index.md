---
title : "CloudWatch Dashboard"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.5.3. </b> "
---

After completing this section, the system will meet the following requirements:

- Dashboard is visible in CloudWatch
- All Metrics are updated in real time
- Alarms are configured and tested
- Email alarm notifications are working correctly
- CloudWatch Log Insights queries have been prepared

### 5.5.3.1 Steps

#### Step 1. Create a CloudWatch Dashboard

1. Sign in to the **AWS Management Console**.
2. Navigate to **CloudWatch**.
3. Select **Dashboards**.
4. Click **Create dashboard**.

![Figure 66.](/images/5-Workshop/5.5-Neon-Operations/image066.png)

5. Enter a dashboard name (e.g., `NeonFoodMap-Operational-Dashboard`).

![Figure 67.](/images/5-Workshop/5.5-Neon-Operations/image067.png)

6. Select to create a new Dashboard.
7. If you have a JSON Dashboard template ready:
   - Select **Actions** → **View/Edit source**.
   - Paste the JSON template content.
   - Click **Save**.

![Figure 69.](/images/5-Workshop/5.5-Neon-Operations/image069.png)

---

#### Step 2. Add a Widget to Display ECS Metrics

1. Open the Dashboard, select `NeonFoodMap-Operational-Dashboard`, and click **Add widget**.

![Figure 69.](/images/5-Workshop/5.5-Neon-Operations/image069.png)

2. Select Data type: **Metrics**, Preferred experience: **Metrics Console**

3. Select Widget type: **Line**

![Figure 68.](/images/5-Workshop/5.5-Neon-Operations/image068.png)

4. Click **Next**, then navigate to **ECS → ClusterName, ServiceName**.

5. Select the following **Metric Names**:
   - CPU Utilization
   - Memory Utilization

![Figure 46.](/images/5-Workshop/5.5-Neon-Operations/image046.png)

6. Enter an appropriate Widget name, then click **Create widget**.

![Figure 45.](/images/5-Workshop/5.5-Neon-Operations/image045.png)

---

#### Step 3. Add a Widget for Application Load Balancer (ALB) Metrics

1. Open the Dashboard, select `NeonFoodMap-Operational-Dashboard`, and click **Add widget**.

![Figure 69.](/images/5-Workshop/5.5-Neon-Operations/image069.png)

2. Select Data type: **Metrics**, Preferred experience: **Metrics Console**

3. Click **Add widget**.

4. Select **CloudWatch Metrics**, then click **Next**.

![Figure 70.](/images/5-Workshop/5.5-Neon-Operations/image070.png)

5. Select **Per AppELB, per AZ, per TG Metrics** and add the following metrics based on your Target Group configuration from earlier:
   - Healthy Host Count
   - UnHealthy Host Count
   - Target Response Time
   - Request Count
   - HTTPCode_Target_5XX_Count

![Figure 60.](/images/5-Workshop/5.5-Neon-Operations/image060.png)
![Figure 110.](/images/5-Workshop/5.5-Neon-Operations/image110.png)
![Figure 111.](/images/5-Workshop/5.5-Neon-Operations/image111.png)
![Figure 112.](/images/5-Workshop/5.5-Neon-Operations/image112.png)

6. Enter an appropriate Widget name, then click **Create widget**.

![Figure 113.](/images/5-Workshop/5.5-Neon-Operations/image113.png)

---

#### Step 4. Add a Widget for Amazon S3 Metrics

1. Open the Dashboard, select `NeonFoodMap-Operational-Dashboard`, and click **Add widget**.

![Figure 69.](/images/5-Workshop/5.5-Neon-Operations/image069.png)

2. Select Data type: **Metrics**, Preferred experience: **Metrics Console**

3. Click **Add widget**.

4. Select **CloudWatch Metrics**, then click **Next**.

![Figure 68.](/images/5-Workshop/5.5-Neon-Operations/image068.png)

5. In the **Browse** window, select the **S3** namespace, then choose the bucket you want to monitor.

![Figure 114.](/images/5-Workshop/5.5-Neon-Operations/image114.png)

6. Select the Storage Metrics for the `neonfoodmap-frontend-dev` and `neonfoodmap-logs` buckets:
   - **BucketSizeBytes**
   - **NumberOfObjects**

![Figure 115.](/images/5-Workshop/5.5-Neon-Operations/image115.png)

7. Enter an appropriate Widget name, then click **Create widget**.

![Figure 116.](/images/5-Workshop/5.5-Neon-Operations/image116.png)

---

#### Step 5. Add a CloudWatch Log Insights Widget

1. Open the Dashboard, select `NeonFoodMap-Operational-Dashboard`, and click **Add widget**.

![Figure 69.](/images/5-Workshop/5.5-Neon-Operations/image069.png)

2. Select **Log query**. Choose the Log Groups for **ECS**, **Application**, and **ALB**.

![Figure 74.](/images/5-Workshop/5.5-Neon-Operations/image074.png)

3. Enter the following query in **CloudWatch Log Insights** to retrieve log entries containing errors (`ERROR`, `Exception`, or status code `500`) from the last 7 days.

```sql
SOURCE "arn:aws:logs:ap-southeast-1:497172038341:log-group:/ecs/neonfoodmap-backend" START=-604800s END=0s
| SOURCE "arn:aws:logs:ap-southeast-1:497172038341:log-group:/ecs/neonfoodmap-task-be"
| fields @timestamp, @message
| filter @message like /ERROR|Exception|500/
| sort @timestamp desc
| limit 20
```

![Figure 75.](/images/5-Workshop/5.5-Neon-Operations/image075.png)

4. Review the returned results, save the Widget to the Dashboard by clicking **Create**, then click **Save** on the `DashboardsNeonFoodMap-Operational-Dashboard` screen to save all widgets.

![Figure 76.](/images/5-Workshop/5.5-Neon-Operations/image076.png)

---

#### Step 6. Add a Widget for Amazon RDS Metrics

Repeat the same process as the steps above:

1. Click **Add widget**.
2. Select metrics from **Amazon RDS**.
3. Select the Database Instance.
4. Add the following Metrics:
   - CPU Utilization
   - Database Connections
   - Read Latency
   - Write Latency
   - Free Storage Space
5. Save the Widget.

---

#### Step 7. Create CloudWatch Alarms

CloudWatch Alarms monitor system metrics and automatically detect when resources exceed defined thresholds. In this step, create an alarm to monitor ECS Service CPU usage.

1. Go to **CloudWatch** → **Alarms**.

2. Click **Create alarm**.

3. In the **Specify metric and conditions** step, click **Select metric** to choose the metric to monitor.

4. In the metric list, select:
   - **ECS**
   - **ClusterName, ServiceName**

5. Select the **CPUUtilization** metric for the ECS Service, then click **Select metric**.

6. Configure the alarm trigger conditions:
   - **Statistic:** Average
   - **Period:** 5 minutes
   - **Threshold type:** Static
   - **Whenever CPUUtilization is:** Greater than
   - **Threshold value:** 80

CloudWatch will switch the Alarm to **ALARM** state when average CPU usage exceeds **80%** during the evaluation period.

7. In the **Configure actions** step, choose the action to take when the Alarm triggers. You can send notifications via an **SNS Topic** or skip this if you only need to monitor the alarm state.

![Figure 57.](/images/5-Workshop/5.5-Neon-Operations/image057.png)

8. Enter a name for the Alarm, for example:
   - **Alarm name:** `ECS-Backend-High-CPU-Alarm`

You can also add a description to make it easier to manage later.

![Figure 55.](/images/5-Workshop/5.5-Neon-Operations/image055.png)

9. Review the entire configuration and click **Create alarm** to finalize.

![Figure 64.](/images/5-Workshop/5.5-Neon-Operations/image064.png)

10. After successful creation, the Alarm will appear in the **CloudWatch Alarms** list with an initial status of **OK**. When the CPU value exceeds the threshold, the status will automatically change to **ALARM**.

![Figure 65.](/images/5-Workshop/5.5-Neon-Operations/image065.png)

> **Note:** Similarly, you can create additional CloudWatch Alarms to monitor the system, such as:
>
> - **HTTPCode_Target_5XX_Count** > 10 errors/minute.
> - **MemoryUtilization** > 80%.
> - **TargetResponseTime** exceeding the desired threshold.
> - **HealthyHostCount** dropping below the minimum count.

#### Step 8. Create an SNS Topic for Notifications and Subscribe an Email Address

1. Go to **Amazon SNS**, select **Topics**, and click **Create topic**.

2. Select type **Standard**.

3. Enter a topic name (e.g., `NeonFoodMap-Alerts-Topic`).

4. Complete the topic creation.

![Figure 47.](/images/5-Workshop/5.5-Neon-Operations/image047.png)

5. Open the newly created Topic and click **Create subscription**.

![Figure 48.](/images/5-Workshop/5.5-Neon-Operations/image048.png)

6. Protocol: select **Email**.

7. Enter the operations team email address or a personal email address.

8. Submit the Subscription, open your email, and click **Confirm Subscription** to activate it.

![Figure 49.](/images/5-Workshop/5.5-Neon-Operations/image049.png)

---
