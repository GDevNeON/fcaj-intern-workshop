---
title: "Worklog Tuần 2"
date: 2026-06-29
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

- Nghiên cứu chuyên sâu các dịch vụ AWS cho triển khai (RDS, ECS Fargate, ECR, CloudWatch, ALB, OIDC).
- Hoàn thiện bản thiết kế kiến trúc hệ thống chi tiết và quy trình CI/CD tự động hóa bảo mật.

### Các công việc triển khai trong tuần:

| Thứ | Công việc thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Nghiên cứu RDS, ECS/ECR và kiến trúc Container Service (Fargate vs EC2 Launch Type) | 29/06/2026 | 29/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Tìm hiểu CloudWatch (Log, Metrics, Alarm), Application Load Balancer (ALB) & Target Groups | 30/06/2026 | 30/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Lựa chọn dịch vụ AWS tối ưu cho hệ thống ứng dụng NeonFoodMap | 01/07/2026 | 01/07/2026 | |
| 5 | - Chốt sơ đồ kiến trúc hạ tầng mạng VPC Multi-AZ (Milestone 1) | 02/07/2026 | 02/07/2026 | |
| 6 | - Xác định quy trình CI/CD và chiến lược Deployment tự động bằng OIDC Auth | 03/07/2026 | 03/07/2026 | |

### Chi tiết công việc thực hiện theo ngày:

- **Thứ 2 (29/06/2026):** Nghiên cứu sâu về công nghệ Container hóa (Docker) và các giải pháp điều phối Container trên AWS: Amazon ECS (Elastic Container Service) với hai chế độ Launch Type (EC2 Launch Type vs Serverless Fargate) và kho lưu trữ Container Images Amazon ECR (Elastic Container Registry). Đánh giá lợi thế của Fargate giúp loại bỏ hoàn toàn gánh nặng quản trị hạ tầng máy chủ ảo (OS patching, scaling group management).
- **Thứ 3 (30/06/2026):** Nghiên cứu dịch vụ quản lý cơ sở dữ liệu quan hệ Amazon RDS MySQL 8.0 chế độ Multi-AZ (tự động tạo Standby Replica ở AZ thứ 2, đồng bộ dữ liệu theo thời gian thực và tự động Failover dưới 60s); Tìm hiểu Application Load Balancer (ALB) điều hướng HTTP/HTTPS traffic và Amazon CloudWatch (Metrics, Log Groups, Alarms).
- **Thứ 4 (01/07/2026):** Chọn giải pháp dịch vụ AWS tối ưu cho kiến trúc NeonFoodMap: RDS MySQL trong Private Subnet cho RDBMS, S3 Buckets lưu trữ tệp tĩnh & file audio thuyết minh Polly, ECS Fargate vận hành Backend Django REST và Frontend React, CloudFront CDN tăng tốc truy cập toàn cầu.
- **Thứ 5 (02/07/2026):** Chốt thiết kế chi tiết hạ tầng mạng Amazon VPC: Dải địa chỉ IP CIDR `10.0.0.0/16` chia làm 2 Availability Zones (`ap-southeast-1a`, `ap-southeast-1b`), bao gồm Public Subnets (`10.0.1.0/24`, `10.0.2.0/24`) đặt ALB & NAT Gateway, và Private Subnets (`10.0.10.0/24`, `10.0.20.0/24`) đặt ECS Tasks & RDS MySQL.
- **Thứ 6 (03/07/2026):** Thiết lập chiến lược CI/CD và quy trình Deployment: Nghiên cứu giải pháp xác thực OpenID Connect (OIDC) giữa GitHub Actions và AWS IAM. Thay vì lưu trữ Access Key/Secret Key tĩnh trong GitHub Secrets, thiết lập OIDC cho phép GitHub Actions nhận IAM Role tạm thời từ AWS STS (Security Token Service), tăng cường độ an toàn bảo mật chuẩn Enterprise.

### Kết quả đạt được tuần 2:

- Nắm vững kiến trúc và cách thức hoạt động của Amazon RDS trong việc lưu trữ cơ sở dữ liệu quan hệ có tính sẵn sàng cao (Multi-AZ Failover).
- Hiểu rõ sự khác biệt giữa các dịch vụ Container của AWS như ECS, ECR và lựa chọn AWS Fargate để triển khai ứng dụng dưới dạng Serverless Compute.
- Nắm bắt được cách sử dụng CloudWatch để giám sát hệ thống (Metrics, Logs, Alarms) và Application Load Balancer để điều phối traffic.
- Chốt sơ đồ kiến trúc hệ thống chi tiết bao gồm các thành phần Network (VPC, Subnet), Database (RDS), Compute (ECS Fargate), và Storage (S3).
- Lên chiến lược triển khai CI/CD hiệu quả, quyết định sử dụng GitHub Actions kết hợp xác thực OIDC an toàn để tự động hóa quá trình build Docker image và deploy lên ECS.

