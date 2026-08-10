---
title: "Worklog Tuần 4"
date: 2026-07-13
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

- SPRINT 1: Foundation & Infrastructure.
- Tích hợp DevOps, xây dựng nền tảng AWS (VPC, RDS, S3, ECR, IAM).

### Các công việc cần triển khai trong tuần:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Setup VPC Multi-AZ (Public/Private subnets, IGW, NAT) | 13/07/2026 | 13/07/2026 | |
| 3 | - Triển khai RDS MySQL trong private subnet | 14/07/2026 | 14/07/2026 | |
| 4 | - Thiết lập S3 Buckets, Lifecycle và IAM Roles bằng CloudFormation | 15/07/2026 | 15/07/2026 | |
| 5 | - Dockerize ứng dụng Frontend & Backend | 16/07/2026 | 16/07/2026 | |
| 6 | - Thiết lập ECR và push Docker Images lên ECR | 17/07/2026 | 17/07/2026 | |

### Kết quả đạt được tuần 4:

- Hoàn thành SPRINT 1, triển khai thành công hạ tầng mạng (VPC) với kiến trúc Multi-AZ, phân chia rõ ràng Public/Private subnets, Internet Gateway và NAT Gateway.
- Khởi tạo và cấu hình thành công Amazon RDS MySQL nằm an toàn trong Private Subnet, đảm bảo bảo mật dữ liệu ở mức network.
- Thiết lập các S3 Buckets chuyên dụng (lưu trữ Frontend, Media, Audio, Logs) với các chính sách Lifecycle hợp lý để tối ưu chi phí lưu trữ dài hạn.
- Triển khai CloudFormation để tự động tạo và quản lý các IAM Roles, áp dụng chặtặt các best practice về phân quyền (IAM Security).
- Hoàn tất việc viết Dockerfile (Dockerize) cho các ứng dụng Frontend và Backend, đồng thời đẩy thành công Docker Images lên Amazon ECR.
