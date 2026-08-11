---
title: "Worklog Tuần 6"
date: 2026-07-27
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

- **SPRINT 3: Scaling, Monitoring & Go-Live (Phần 1)**.
- Cấu hình ECS Service Auto-Scaling chịu tải tự động, Amazon CloudFront CDN, CloudWatch Dashboards, Log Insights & AWS Budgets Cost Control.

### Các công việc triển khai trong tuần:

| Thứ | Công việc thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Cấu hình ECS Services Auto-Scaling (Target Tracking Scaling 70% CPU, min 2 tasks, max 6 tasks) | 27/07/2026 | 27/07/2026 | |
| 3 | - Thiết lập CloudFront CDN phân phối nội dung tốc độ cao cho Frontend, Media & Audio files từ Edge | 28/07/2026 | 28/07/2026 | |
| 4 | - Xây dựng CloudWatch Dashboard giám sát tài nguyên thời gian thực & cấu hình SNS Alarms báo lỗi 5xx | 29/07/2026 | 29/07/2026 | |
| 5 | - Tích hợp AWS Budgets thiết lập ngân sách $30.00/tháng và cảnh báo chi phí tự động qua email | 30/07/2026 | 30/07/2026 | |
| 6 | - Cấu hình CloudWatch Logs Insights & biên soạn các câu truy vấn mẫu phân tích log hệ thống | 31/07/2026 | 31/07/2026 | |

### Chi tiết công việc thực hiện theo ngày:

- **Thứ 2 (27/07/2026):** **Bắt đầu SPRINT 3 (Part 1: Scaling, Monitoring & Cost Control)**. Cấu hình cơ chế Auto-Scaling (Target Tracking Scaling) cho Backend ECS Service dựa trên chỉ số CPU Utilization trung bình. Đặt ngưỡng kích hoạt target `70%`, giới hạn số lượng Task từ tối thiểu `2 tasks` đến tối đa `6 tasks`, thời gian chờ scale-down `300s`.
- **Thứ 3 (28/07/2026):** Khởi tạo Amazon CloudFront CDN Distribution trỏ Origin về ALB Endpoint và S3 Buckets. Cấu hình Cache Behavior tối ưu cho tệp tĩnh (JS/CSS), hình ảnh media địa điểm và file audio thuyết minh (.mp3), lưu đệm 24h tại trạm Edge Locations. Kết quả giảm độ trễ tải trang từ 3.5s xuống 1.2s và giảm 60% request trực tiếp tới origin server.
- **Thứ 4 (29/07/2026):** Thiết lập CloudWatch Dashboard trực quan hóa các chỉ số vận hành chính: CPU/Memory Utilization của cụm ECS Fargate, Target Response Time của ALB, tổng số HTTP Requests/phút và số lượng lỗi HTTP 4xx/5xx. Cấu hình CloudWatch Alarm tích hợp Amazon SNS (Simple Notification Service) tự động phát email cảnh báo ngay lập tức khi phát sinh trên 5 lỗi HTTP 5xx trong 1 phút.
- **Thứ 5 (30/07/2026):** Thiết lập cơ chế kiểm soát chi phí đám mây tự động bằng AWS Budgets. Đặt ngân sách cố định `$30.00/tháng`, cài đặt cảnh báo qua email SNS khi chi phí thực tế đạt 80% ($24.00) hoặc khi chi phí dự báo (forecasted cost) vượt 100%.
- **Thứ 6 (31/07/2026):** Cấu hình CloudWatch Logs Insights tập trung toàn bộ log từ Backend/Frontend ECS tasks. Viết và lưu trữ các câu truy vấn mẫu (query snippets) để chủ động phân tích nguyên nhân lỗi HTTP 500, truy vấn SQL chậm trên RDS và thống kê thời gian phản hồi của các REST APIs.

### Kết quả đạt được tuần 6:

- Hoàn thành phần 1 của SPRINT 3, cấu hình thành công các chính sách Auto-Scaling cho ECS Services, giúp hệ thống tự động co giãn dựa trên tải CPU/Memory.
- Tích hợp thành công Amazon CloudFront CDN, giúp cache các nội dung tĩnh (Media, Frontend) tại các Edge Locations để tăng tốc độ tải trang đáng kể.
- Xây dựng hoàn chỉnh Dashboard giám sát trên Amazon CloudWatch, thiết lập các metrics quan trọng và alarms SNS để cảnh báo khi hệ thống có dấu hiệu quá tải.
- Tối ưu hóa việc thu thập log bằng cách cấu hình CloudWatch Logs, cho phép sử dụng Log Insights để truy vấn và phân tích log của ứng dụng tập trung.
- Triển khai hệ thống cảnh báo chi phí (AWS Budgets & Alerts) nhằm kiểm soát rủi ro phát sinh chi phí ngoài ý muốn trong quá trình vận hành dự án.

