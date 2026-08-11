---
title: "Worklog Tuần 5"
date: 2026-07-20
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

- **SPRINT 2: CI/CD Pipeline & Deployment**.
- Tự động hóa quy trình CI/CD bằng GitHub Actions (xác thực OIDC an toàn), khởi tạo cụm Amazon ECS Fargate và Application Load Balancer (ALB).

### Các công việc triển khai trong tuần:

| Thứ | Công việc thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Xây dựng GitHub Actions CI/CD workflow (xác thực OIDC không mật khẩu, build, push ECR & deploy ECS) | 20/07/2026 | 20/07/2026 | |
| 3 | - Cấu hình cụm Amazon ECS Cluster (Serverless Fargate) và biên soạn ECS Task Definitions | 21/07/2026 | 21/07/2026 | |
| 4 | - Khởi tạo Application Load Balancer (ALB), Target Groups & cấu hình đường dẫn Health Checks | 22/07/2026 | 22/07/2026 | |
| 5 | - Cấu hình Django Backend kết nối RDS MySQL & lưu trữ media/static trực tiếp trên Amazon S3 | 23/07/2026 | 23/07/2026 | |
| 6 | - Cấu hình React Frontend nhận API URL qua Docker build args & kiểm thử luồng CI/CD Deployment tự động | 24/07/2026 | 24/07/2026 | |

### Chi tiết công việc thực hiện theo ngày:

- **Thứ 2 (20/07/2026):** **Bắt đầu SPRINT 2 (CI/CD Pipeline & Deployment)**. Cấu hình xác thực OpenID Connect (OIDC) giữa GitHub Actions và AWS IAM. Tạo IAM Identity Provider `token.actions.githubusercontent.com` và IAM Role `GitHubActions-ECR-ECS-DeployRole` kèm Trust Relationship an toàn chỉ chấp nhận repo `gdevneon/fcaj-intern-workshop` và branch `main`. Viết file workflow `.github/workflows/deploy.yml` tự động build Docker image, push ECR và update ECS Service.
- **Thứ 3 (21/07/2026):** Khởi tạo cụm Amazon ECS Cluster (`cls-neonfoodmap`) mô hình Fargate (Serverless Compute). Biên soạn Task Definitions cho Backend (`0.5 vCPU`, `1GB RAM`) và Frontend (`0.25 vCPU`, `0.5GB RAM`), gán `awslogs` driver gửi stdout/stderr logs tập trung về Amazon CloudWatch Logs Group `/ecs/neon-food-map`.
- **Thứ 4 (22/07/2026):** Khởi tạo Application Load Balancer (ALB) `alb-neonfoodmap` tại Public Subnets. Tạo Target Group `tg-neonfoodmap-be` (cổng 8000, Health Check path `/api/health/`) và Target Group `tg-neonfoodmap-fe` (cổng 80, Health Check path `/`). Cấu hình ALB Listener Rules điều hướng request có tiền tố `/api/*` về Backend và `/` về Frontend.
- **Thứ 5 (23/07/2026):** Cấu hình ứng dụng Django Backend trên cụm ECS Fargate: thiết lập các biến môi trường kết nối tới Amazon RDS MySQL trong Private Subnet (`DB_HOST`, `DB_NAME`, `DB_USER`, `DB_PASSWORD`), tích hợp thư viện `django-storages` và `boto3` để upload/serve trực tiếp static và media files từ S3 Buckets.
- **Thứ 6 (24/07/2026):** Cấu hình ứng dụng React Frontend nhận API Endpoint URL động thông qua biến môi trường build-args trong Dockerfile. Kiểm thử luồng CI/CD tự động 100%: push git commit lên branch `main`, GitHub Actions tự động kích hoạt workflow build Docker images, đẩy lên ECR và thực hiện Rolling Update ECS Services thành công trong thời gian dưới 3 phút.

### Kết quả đạt được tuần 5:

- Hoàn thành SPRINT 2, thiết lập thành công luồng CI/CD tự động bằng GitHub Actions sử dụng xác thực OIDC an toàn với AWS STS.
- Cấu hình thành công cụm Amazon ECS (sử dụng Fargate) và các Task Definitions với thông số tài nguyên CPU/Memory tối ưu cho Frontend và Backend.
- Triển khai Application Load Balancer (ALB) kết hợp với Target Groups và cấu hình Health Checks để điều phối traffic và đảm bảo tính sẵn sàng cao.
- Cấu hình thành công ứng dụng Django để kết nối an toàn tới cơ sở dữ liệu RDS và lưu trữ static/media files trực tiếp trên S3.
- Điều chỉnh ứng dụng React (Frontend) để nhận API URL động thông qua biến môi trường khi build, giúp frontend giao tiếp trơn tru với Backend qua ALB.

