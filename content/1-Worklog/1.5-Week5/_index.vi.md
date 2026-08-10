---
title: "Worklog Tuần 5"
date: 2026-07-20
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

- SPRINT 2: CI/CD Pipeline & Deployment.
- Tự động hóa quá trình deploy bằng GitHub Actions và thiết lập ECS, ALB.

### Các công việc cần triển khai trong tuần:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Xây dựng GitHub Actions CI/CD pipeline (OIDC auth, build, push ECR) | 20/07/2026 | 20/07/2026 | |
| 3 | - Cấu hình ECS cluster (Fargate) và task definitions | 21/07/2026 | 21/07/2026 | |
| 4 | - Thiết lập ALB, Target Groups và Health Checks | 22/07/2026 | 22/07/2026 | |
| 5 | - Cấu hình Django trên AWS (kết nối RDS, static files) | 23/07/2026 | 23/07/2026 | |
| 6 | - Cấu hình React trên AWS (API URL, build args) | 24/07/2026 | 24/07/2026 | |

### Kết quả đạt được tuần 5:

- Hoàn thành SPRINT 2, thiết lập thành công luồng CI/CD tự động bằng GitHub Actions sử dụng xác thực OIDC an toàn với AWS.
- Cấu hình thành công cụm Amazon ECS (sử dụng Fargate) và các Task Definitions với thông số tài nguyên CPU/Memory tối ưu cho Frontend và Backend.
- Triển khai Application Load Balancer (ALB) kết hợp với Target Groups và cấu hình Health Checks để điều phối traffic và đảm bảo tính sẵn sàng cao.
- Cấu hình thành công ứng dụng Django để kết nối an toàn tới cơ sở dữ liệu RDS và lưu trữ static files trực tiếp trên S3.
- Điều chỉnh ứng dụng React (Frontend) để nhận API URL động thông qua biến môi trường khi build, giúp frontend giao tiếp trơn tru với Backend qua ALB.
