---
title: "Worklog Tuần 6"
date: 2026-07-27
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

- SPRINT 3: Scaling, Monitoring & Go-Live (Phần 1).
- Cấu hình Auto-scaling, CloudFront CDN và giám sát bằng CloudWatch.

### Các công việc cần triển khai trong tuần:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Cấu hình ECS Services và chính sách Auto-Scaling | 27/07/2026 | 27/07/2026 | |
| 3 | - Thiết lập CloudFront CDN cho Frontend và cache media | 28/07/2026 | 28/07/2026 | |
| 4 | - Triển khai CloudWatch dashboard, metrics và alarms | 29/07/2026 | 29/07/2026 | |
| 5 | - Thiết lập Cost Monitoring, AWS Budgets và Alerts | 30/07/2026 | 30/07/2026 | |
| 6 | - Cấu hình CloudWatch Logs + các câu truy vấn Log Insights | 31/07/2026 | 31/07/2026 | |

### Kết quả đạt được tuần 6:

- Hoàn thành phần 1 của SPRINT 3, cấu hình thành công các chính sách Auto-Scaling cho ECS Services, giúp hệ thống tự động co giãn dựa trên tải CPU/Memory.
- Tích hợp thành công Amazon CloudFront CDN, giúp cache các nội dung tĩnh (Media, Frontend) tại các Edge Locations để tăng tốc độ tải trang đáng kể.
- Xây dựng hoàn chỉnh Dashboard giám sát trên Amazon CloudWatch, thiết lập các metrics quan trọng và alarms để cảnh báo khi hệ thống có dấu hiệu quá tải.
- Tối ưu hóa việc thu thập log bằng cách cấu hình CloudWatch Logs, cho phép sử dụng Log Insights để truy vấn và phân tích log của ứng dụng tập trung.
- Triển khai hệ thống cảnh báo chi phí (AWS Budgets & Alerts) nhằm kiểm soát rủi ro phát sinh chi phí ngoài ý muốn trong quá trình vận hành dự án.
