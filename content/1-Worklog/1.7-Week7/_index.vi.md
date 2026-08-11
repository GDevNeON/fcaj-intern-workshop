---
title: "Worklog Tuần 7"
date: 2026-08-03
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

- **SPRINT 3: Scaling, Monitoring & Go-Live (Phần 2)**.
- Thực hiện End-to-End Testing, Load Testing với Locust (1.000 users), QA Debugging, kiểm thử RDS Failover và cắt chuyển Production (Go-Live).

### Các công việc triển khai trong tuần:

| Thứ | Công việc thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Thực hiện End-to-End Testing toàn bộ luồng nghiệp vụ chính trên môi trường Staging | 03/08/2026 | 03/08/2026 | |
| 3 | - Tiến hành Load Testing với Locust (giả lập 1.000 concurrent users) & kiểm chứng Auto-Scaling | 04/08/2026 | 04/08/2026 | |
| 4 | - Xử lý, debug và khắc phục các lỗi phát sinh trong quá trình QA qua CloudWatch Log Insights | 05/08/2026 | 05/08/2026 | |
| 5 | - Kiểm tra hệ thống Real-time Error Tracking & diễn tập RDS Multi-AZ Failover | 06/08/2026 | 06/08/2026 | |
| 6 | - Cắt chuyển hệ thống lên môi trường Production (Go-Live) & theo dõi tính ổn định | 07/08/2026 | 07/08/2026 | |

### Chi tiết công việc thực hiện theo ngày:

- **Thứ 2 (03/08/2026):** **Bắt đầu SPRINT 3 (Part 2: QA, Load Testing & Production Go-Live)**. Thực hiện bài kiểm thử End-to-End (E2E Testing) toàn bộ luồng nghiệp vụ ứng dụng NeonFoodMap trên môi trường Staging: Đăng ký/Đăng nhập tài khoản, Tìm kiếm địa điểm POI theo bán kính GPS, Phát âm thanh thuyết minh tự động Polly, Đặt tour và Thanh toán đơn hàng.
- **Thứ 3 (04/08/2026):** Tiến hành bài kiểm thử chịu tải (Load Testing) bằng công cụ Locust giả lập `1.000 người dùng truy cập đồng thời`. Kết quả ghi nhận: Khi CPU tăng lên `78%`, chính sách ECS Auto-Scaling kích hoạt thành công, tự động bổ sung thêm 2 ECS Tasks mới sau 45 giây, kéo CPU bình quân về `45%`, tỷ lệ lỗi HTTP 5xx giữ ở mức `0%`.
- **Thứ 4 (05/08/2026):** Sử dụng CloudWatch Logs Insights để phân tích log kiểm thử, phát hiện và khắc phục các lỗi phát sinh trong quá trình QA: xử lý điểm nghẽn latency nhỏ tại API tìm kiếm POI, tinh chỉnh lại Database Connection Pool và ALB Target Group Timeout.
- **Thứ 5 (06/08/2026):** Đánh giá tính sẵn sàng của cơ chế Real-time Error Tracking qua CloudWatch. Thực hiện diễn tập cắt thử 1 Availability Zone để kiểm chứng tính năng tự động Failover của Amazon RDS MySQL Multi-AZ, đảm bảo dữ liệu không bị thất thoát và ứng dụng tự động khôi phục kết nối dưới 60 giây.
- **Thứ 6 (07/08/2026):** Thực hiện cắt chuyển ứng dụng chính thức lên môi trường Production (**Go-Live Production**). Theo dõi sát sao các chỉ số trên CloudWatch Dashboard, đảm bảo hệ thống vận hành ổn định 100%, không có downtime và đạt tiêu chuẩn sẵn sàng cao (High Availability 99.99%).

### Kết quả đạt được tuần 7:

- Hoàn thành phần 2 của SPRINT 3, thực hiện thành công các kịch bản End-to-End (E2E) testing trên các luồng người dùng chính yếu của hệ thống.
- Thực hiện Load testing thành công với Locust (1.000 users), đánh giá sức chịu tải và kiểm chứng Auto-Scaling kéo CPU bình quân về mức an toàn 45% với 0% lỗi 5xx.
- Phát hiện và khắc phục nhanh chóng các lỗi (bugs) sinh ra trong quá trình QA, tối ưu hóa Database Connection Pool và API Target Response Time.
- Đánh giá và xác nhận hệ thống Real-time Error Tracking qua CloudWatch và khả năng RDS Multi-AZ Failover hoạt động chuẩn xác dưới 60 giây.
- Triển khai thành công ứng dụng lên môi trường Production (Go-Live) và duy trì sự ổn định, không có downtime trong quá trình theo dõi hệ thống.

