---
title: "Worklog Tuần 4"
date: 2026-07-13
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

- **SPRINT 1: Foundation & Infrastructure**.
- Triển khai nền tảng hạ tầng đám mây AWS (VPC Multi-AZ, RDS MySQL Multi-AZ, S3 Buckets, IAM Roles CloudFormation, Dockerize & Amazon ECR).

### Các công việc triển khai trong tuần:

| Thứ | Công việc thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Thiết lập VPC Multi-AZ (Public/Private Subnets, Internet Gateway, NAT Gateway & Route Tables) | 13/07/2026 | 13/07/2026 | |
| 3 | - Triển khai cơ sở dữ liệu Amazon RDS MySQL 8.0 Multi-AZ trong Private Subnet & cấu hình Security Groups | 14/07/2026 | 14/07/2026 | |
| 4 | - Khởi tạo 4 S3 Buckets, S3 Lifecycle Policies & quản lý IAM Roles tự động bằng AWS CloudFormation | 15/07/2026 | 15/07/2026 | |
| 5 | - Thực hiện đóng gói Container (Dockerize) cho ứng dụng Frontend ReactJS và Backend Django REST | 16/07/2026 | 16/07/2026 | |
| 6 | - Khởi tạo Amazon ECR Repositories, xác thực CLI và push Docker Images lên ECR thành công | 17/07/2026 | 17/07/2026 | |

### Chi tiết công việc thực hiện theo ngày:

- **Thứ 2 (13/07/2026):** **Bắt đầu SPRINT 1 (Foundation & Infrastructure)**. Khởi tạo Amazon VPC Multi-AZ (`10.0.0.0/16`) tại Region Singapore (`ap-southeast-1`). Tạo 2 Public Subnets (`10.0.1.0/24`, `10.0.2.0/24`), 2 Private Subnets (`10.0.10.0/24`, `10.0.20.0/24`), 1 Internet Gateway (IGW) gán cho VPC, 1 NAT Gateway gán cho Public Subnet 1, và cấu hình các Route Tables tương ứng.
- **Thứ 3 (14/07/2026):** Khởi tạo DB Subnet Group bao gồm các Private Subnets; Triển khai Amazon RDS MySQL 8.0 chế độ Multi-AZ (`db.t3.micro`). Cấu hình Security Group `sg-rds-mysql` thiết lập Inbound Rule chỉ chấp nhận kết nối cổng 3306 từ Security Group của cụm Backend `sg-ecs-backend`.
- **Thứ 4 (15/07/2026):** Khởi tạo 4 Amazon S3 Buckets (`neon-food-map-frontend`, `neon-food-map-media`, `neon-food-map-audio`, `neon-food-map-logs`). Cấu hình S3 Lifecycle Policy tự động chuyển file log sang S3 Standard-IA sau 30 ngày và S3 Glacier sau 90 ngày. Khởi tạo template AWS CloudFormation tự động gán IAM Roles (`ECS-TaskExecutionRole` & `ECS-TaskRole`) theo đúng nguyên tắc phân quyền Least Privilege.
- **Thứ 5 (16/07/2026):** Thực hiện đóng gói Container (Dockerize) ứng dụng. Viết Dockerfile cho Backend Django (dùng base image `python:3.11-slim`, WSGI gunicorn server) và Dockerfile cho Frontend React (multi-stage build với Node.js build & Nginx serving). Build thử nghiệm cả 2 Docker Images tại local và kiểm tra tính tương thích.
- **Thứ 6 (17/07/2026):** Khởi tạo 2 repositories trên Amazon ECR (`neon-food-map-backend` và `neon-food-map-frontend`). Thực hiện xác thực AWS ECR CLI (`aws ecr get-login-password`), thực hiện gắn nhãn (tagging image) và push thành công 2 Docker Images lên ECR repos. Hoàn tất Sprint 1 vượt tiến độ.

### Kết quả đạt được tuần 4:

- Hoàn thành SPRINT 1, triển khai thành công hạ tầng mạng (VPC) với kiến trúc Multi-AZ, phân chia rõ ràng Public/Private subnets, Internet Gateway và NAT Gateway.
- Khởi tạo và cấu hình thành công Amazon RDS MySQL nằm an toàn trong Private Subnet, đảm bảo bảo mật dữ liệu ở mức network.
- Thiết lập 4 S3 Buckets chuyên dụng (lưu trữ Frontend, Media, Audio, Logs) với các chính sách Lifecycle hợp lý để tối ưu chi phí lưu trữ dài hạn.
- Triển khai CloudFormation để tự động tạo và quản lý các IAM Roles, áp dụng chặt chẽ các best practice về phân quyền (IAM Security).
- Hoàn tất việc viết Dockerfile (Dockerize) cho các ứng dụng Frontend và Backend, đồng thời đẩy thành công Docker Images lên Amazon ECR.

