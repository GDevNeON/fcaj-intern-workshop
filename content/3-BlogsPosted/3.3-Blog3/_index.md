---
title: "Blog 3"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# BUYING SAVINGS PLANS BEFORE RIGHTSIZING MIGHT CAUSE YOU TO OPTIMIZE COSTS IN THE WRONG ORDER

When EC2 bills start rising, a common reaction for many teams is to purchase Savings Plans as quickly as possible.

This approach helps reduce the unit cost of compute, but it doesn't necessarily make the system truly efficient.

If a workload is still over-provisioned, you are simply buying a better price for resources that aren't needed in the first place.

On July 16, 2026, AWS added a Cost Efficiency widget to the Billing and Cost Management Dashboards. This widget allows you to track the level of optimization over time, per AWS account or Region, and links directly to the Cost Optimization Hub to act on savings opportunities.

The key takeaway is not just that AWS added a new chart, but rather how AWS defines "cost optimization."

## COST EFFICIENCY IS NOT "HOW MUCH WAS SAVED THIS MONTH"

AWS calculates Cost Efficiency using the following formula:

**Cost Efficiency = [1 − Potential Savings / Total Optimizable Spend] × 100%**

For example, if an enterprise has $100,000 in optimizable spend and the Cost Optimization Hub identifies $10,000 in potential savings, the Cost Efficiency would be 90%.

The metric is updated daily, based on the cost over the last 30 days and the existing savings opportunities. It aggregates:

– Idle resources
– Rightsizing
– Savings Plans and Reserved Instances
– Appropriate instance type selection
– Optimization recommendations across EC2, ECS, EKS, EBS, RDS, Lambda, DynamoDB, OpenSearch, and many other services

## 3 IMPORTANT LESSONS FOR AWS COST OPTIMIZATION

### 1️⃣ RIGHTSIZE FIRST, COMMIT LATER

The logical order should be:

Eliminate idle resources → Rightsize workload → Upgrade to newer generation instances or Graviton where appropriate → Only then purchase Savings Plans or Reserved Instances.

If you purchase a commitment first, you might lock your spending commitment into an over-provisioned workload. When rightsizing later, the released capacity might not reduce your bill correspondingly because the commitment is still active.

AWS has also noted that large customers who combine rightsizing with Savings Plans improve their Cost Efficiency approximately four times faster than those relying primarily on Savings Plans alone.

### 2️⃣ WITHOUT MEMORY METRICS, EC2 RIGHTSIZING FLIES BLIND

By default, CloudWatch collects many EC2 metrics, but it does not automatically capture memory utilization data from inside the operating system.

When memory data is lacking, Compute Optimizer may not have sufficient information to determine if an instance has excess RAM or to recommend a smaller configuration.

In an analysis of over 71,000 opted-in AWS customers, only 17.7% of eligible workloads had enabled memory metrics. Having this data correlates with savings per recommendation that are 8 to 30 percentage points higher, depending on the instance type.

Therefore, before concluding that EC2 "has nothing left to optimize," check whether your CloudWatch Agent or observability tool is actually sending memory metrics.

### 3️⃣ DON'T TURN COST OPTIMIZATION INTO A QUARTERLY CAMPAIGN

Cost Efficiency updates daily and can now be placed alongside Cost Explorer, Budgets, Savings Plans coverage, and Reserved Instance utilization on a unified dashboard.

The dashboard can also be shared cross-account, exported as CSV/PDF, or sent as periodic reports via email.

A practical workflow might look like:

- **Weekly**: Check for accounts or Regions where Cost Efficiency has significantly dropped.
- **Monthly**: Review recommendations that offer high savings with low effort and rollback capabilities.
- **Quarterly**: Adjust commitments based on rightsized workloads, rather than relying solely on current spending levels.

## CONCLUSION

Savings Plans do not replace architectural optimization.

Rightsizing does not replace commitment discounts.

A strong FinOps strategy must execute in the right order:

**Eliminate waste → Optimize resources → Standardize workloads → Then commit spending.**

The new AWS Cost Efficiency widget helps transform this process from a disjointed list of recommendations into a measurable feedback loop over time.

---

## Link

- [Link post at AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj/posts/2234324983999128)

**References:**

- [Cost Efficiency widget in Billing and Cost Management Dashboards — AWS, 16/07/2026.](https://aws.amazon.com/about-aws/whats-new/2026/07/monitor-cost-efficiency-using-dashboards)
- [The AWS State of Cost Efficiency Report — AWS Cloud Financial Management, 09/06/2026.](https://aws.amazon.com/blogs/aws-cloud-financial-management/the-aws-state-of-cost-efficiency-report/)
- [Understanding your cost efficiency metric — AWS Cost Management Documentation.](https://docs.aws.amazon.com/cost-management/latest/userguide/coh-cost-efficiency.html)


![](/images/3-Blog/blog3.jpg)

Ho Chi Minh City, August 04, 2026 <br>
Bui Bao Long