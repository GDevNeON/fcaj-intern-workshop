---
title : "CloudWatch Logs and Log Insights"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.5.5. </b> "
---

After completing this section, the system will meet the following requirements:

- Log retention period set to **30 days**
- Log Group created for **Application Logs**
- Log Groups provisioned for system log storage and management
- Logs queried using **CloudWatch Logs Insights**
- **VPC Flow Logs** enabled to monitor network traffic within the VPC
- Log collection and analysis capabilities verified

---

### 5.5.5.1 Steps

#### Step 1. Set Log Retention Policy

By default, CloudWatch retains logs indefinitely. To optimize storage costs, configure the log retention period to **30 days**.

1. Sign in to the **AWS Management Console**.
2. Navigate to **CloudWatch**.
3. Select **Log groups**.

![Figure 78.](/images/5-Workshop/5.5-Neon-Operations/image078.png)

4. Select the Log Group to configure.
5. Choose **Actions → Edit retention setting**.

![Figure 79.](/images/5-Workshop/5.5-Neon-Operations/image079.png)

6. Under **Retention setting**, select **30 Days**.
7. Click **Save** to apply the configuration.

![Figure 80.](/images/5-Workshop/5.5-Neon-Operations/image080.png)

> **Note:** Repeat this for all system Log Groups to ensure the retention policy is applied consistently.

---

#### Step 2. Create a Log Group

Log Groups are used to store and manage logs from AWS services such as ECS, Lambda, or VPC Flow Logs.

1. In **CloudWatch**, select **Log groups**.
2. Click **Create log group**.
3. Enter the Log Group name, for example:

```
/ecs/neonfoodmap-task-be
```

or

```
/ecs/neonfoodmap-task-fe
```

4. Keep the default settings.

5. Click **Create** to finish.

6. After creation, the Log Group will appear in the list.

---

#### Step 3. Configure ECS to Write Logs to CloudWatch

To allow ECS containers to write logs directly to CloudWatch, configure the **awslogs Log Driver** in the Task Definition.

1. Go to **Amazon ECS**.
2. Select **Task Definitions** and open the application's Task Definition.
3. Select **Create new revision**.
4. In the **Container Definitions** section, configure:

- **Log driver:** `awslogs`
- **Log group:** `/ecs/neonfoodmap-backend`
- **AWS Region:** `ap-southeast-1`
- **Stream prefix:** `ecs`

5. Save the new Task Definition.
6. Update the ECS Service to use the newly created Revision.
7. After the Deployment is complete, logs will automatically be written to CloudWatch.

![Figure 106.](/images/5-Workshop/5.5-Neon-Operations/image106.png)

---

#### Step 4. Query Logs with CloudWatch Logs Insights

CloudWatch Logs Insights enables real-time log search, aggregation, and analysis.

1. Go to **CloudWatch → Logs Insights**.
2. Select the Log Group to analyze.
3. Enter a Log Insights query or use a saved query.
4. Click **Run query** to execute.

Use cases include:
- Finding entries containing Exceptions.
- Counting Errors over time.
- Finding HTTP Status Code 500 responses.
- Analyzing requests with long processing times.
- Finding the most frequent source IPs.

5. To reuse a query, click **Save query**.
6. Enter a query name and save it.

![Figure 105.](/images/5-Workshop/5.5-Neon-Operations/image105.png)

![Figure 107.](/images/5-Workshop/5.5-Neon-Operations/image107.png)

![Figure 108.](/images/5-Workshop/5.5-Neon-Operations/image108.png)

---

#### Step 5. Configure VPC Flow Logs

VPC Flow Logs capture all inbound and outbound network traffic within the VPC, helping analyze connectivity issues and monitor traffic patterns.

1. Go to **Amazon VPC**.
2. Select **Your VPCs**.
3. Select the system VPC.

![Figure 98.](/images/5-Workshop/5.5-Neon-Operations/image098.png)

4. Select the **Flow logs** tab.
5. Click **Create flow log**.
6. Configure the following settings:

- **Filter:** All
- **Destination:** Send to CloudWatch Logs
- **Destination log group:** Select the Log Group you created
- **IAM Role:** Select the Role with permission to write Logs to CloudWatch

7. Click **Create flow log** to finish.

![Figure 99.](/images/5-Workshop/5.5-Neon-Operations/image099.png)

![Figure 100.](/images/5-Workshop/5.5-Neon-Operations/image100.png)

![Figure 101.](/images/5-Workshop/5.5-Neon-Operations/image101.png)

![Figure 102.](/images/5-Workshop/5.5-Neon-Operations/image102.png)

![Figure 103.](/images/5-Workshop/5.5-Neon-Operations/image103.png)

---

#### Step 6. Verify Log Collection and Querying

After completing the configuration, verify the system's log collection and analysis capabilities.

1. Go to **CloudWatch → Logs Insights**.
2. Select the application's Log Group.
3. Run the queries you created.
4. Verify the results:

- Logs are being recorded completely.
- You can filter by time range.
- Queries return the correct data.
- You can search by keyword or log level.

5. Confirm that new logs continue to be updated as the application runs.
6. Log and Log Insights configuration is complete.
