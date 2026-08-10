---
title: "Worklog Tuần 2"
date: 2026-06-29
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

- Tìm hiểu các dịch vụ AWS phục vụ triển khai (RDS, ECS, ECR, CloudWatch, API Gateway).
- Hoàn thiện thiết kế hệ thống và quy trình CI/CD.

### Các công việc cần triển khai trong tuần:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu RDS, ECS/ECR và kiến trúc Container Service | 29/06/2026 | 29/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Tìm hiểu CloudWatch (Log, Metrics, Alarm), API Gateway và Load Balancers | 30/06/2026 | 30/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Lựa chọn dịch vụ AWS phù hợp cho NeonFoodMap | 01/07/2026 | 01/07/2026 | |
| 5 | - Hoàn thiện sơ đồ kiến trúc triển khai (Milestone) | 02/07/2026 | 02/07/2026 | |
| 6 | - Xác định quy trình CI/CD và Deployment | 03/07/2026 | 03/07/2026 | |

### Kết quả đạt được tuần 2:

- Nắm vững kiến trúc và cách thức hoạt động của Amazon RDS trong việc lưu trữ cơ sở dữ liệu quan hệ có tính sẵn sàng cao (Multi-AZ).
- Hiểu rõ sự khác biệt giữa các dịch vụ Container của AWS như ECS, ECR và lựa chọn AWS Fargate để triển khai ứng dụng dưới dạng Serverless Compute.
- Nắm bắt được cách sử dụng CloudWatch để giám sát hệ thống (Metrics, Logs, Alarms) và API Gateway, Load Balancer để điều phối traffic.
- Chốt sơ đồ kiến trúc hệ thống chi tiết bao gồm các thành phần Network (VPC, Subnet), Database (RDS), Compute (ECS), và Storage (S3).
- Lên chiến lược triển khai CI/CD hiệu quả, quyết định sử dụng GitHub Actions để tự động hóa quá trình build Docker image và deploy lên ECS.
