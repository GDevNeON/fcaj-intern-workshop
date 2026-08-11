---
title: "Worklog Tuần 3"
date: 2026-07-06
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

- Phát triển hoàn thiện mã nguồn ứng dụng NeonFoodMap (ReactJS Frontend & Django REST Backend).
- Thiết kế Database Schema, xây dựng RESTful APIs và tích hợp AWS Polly Text-to-Speech trước khi triển khai lên AWS Cloud.

### Các công việc triển khai trong tuần:

| Thứ | Công việc thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Thiết lập môi trường phát triển cục bộ (Local Dev: Python 3.11, Django, Node.js/React, MySQL) | 06/07/2026 | 06/07/2026 | |
| 3 | - Thiết kế Database Schema (Users, POIs, Audios, Reviews) & khởi tạo Django ORM Migrations | 07/07/2026 | 07/07/2026 | |
| 4 | - Xây dựng RESTful APIs: JWT Authentication, POI Radius Search & tích hợp AWS Polly Text-to-Speech | 08/07/2026 | 08/07/2026 | |
| 5 | - Xây dựng giao diện ReactJS UI: Bản đồ tương tác Leaflet/Mapbox, Audio Player thuyết minh & trang POI | 09/07/2026 | 09/07/2026 | |
| 6 | - Kiểm thử API bằng Postman, tích hợp Frontend-Backend local & kiểm tra Responsive UI | 10/07/2026 | 10/07/2026 | |

### Chi tiết công việc thực hiện theo ngày:

- **Thứ 2 (06/07/2026):** Thiết lập môi trường phát triển cục bộ (Local Development Environment): Cài đặt Python 3.11, Django REST Framework, Node.js 18, ReactJS, MySQL Server 8.0 cục bộ và cấu hình Git repository cho hai khối mã nguồn Backend và Frontend.
- **Thứ 3 (07/07/2026):** Thiết kế Database Schema trong Django ORM: Định nghĩa các bảng dữ liệu `Users`, `FoodPlaces` (POIs), `Categories`, `AudioCommentaries`, `Reviews`, `Orders`. Thực hiện tạo các file Migrations và migrate thành công vào MySQL local.
- **Thứ 4 (08/07/2026):** Xây dựng các RESTful API cốt lõi trên Backend: API Đăng ký/Đăng nhập (JSON Web Token - JWT Authentication), API Truy vấn vị trí ẩm thực (POI Radius Search dựa trên kinh độ/vĩ độ GPS), API tạo đơn hàng và tích hợp AWS SDK (Boto3) với dịch vụ AWS Polly để tự động chuyển đổi văn bản mô tả địa điểm thành file âm thanh thuyết minh `.mp3`.
- **Thứ 5 (09/07/2026):** Phát triển giao diện UI Frontend bằng ReactJS: Tích hợp thư viện bản đồ tương tác (Leaflet/Mapbox), hiển thị danh sách địa điểm ẩm thực xung quanh vị trí người dùng, xây dựng Trình phát âm thanh (Audio Player) thuyết minh địa điểm tự động và trang quản lý tài khoản.
- **Thứ 6 (10/07/2026):** Thực hiện kiểm thử toàn bộ các API endpoint bằng Postman (xác thực token, response status, data payload); Kiểm thử tích hợp kết nối giữa React Frontend và Django Backend trên môi trường local, đảm bảo giao diện responsive tối ưu trên cả giao diện máy tính và thiết bị di động.

### Kết quả đạt được tuần 3:

- Thiết lập hoàn chỉnh môi trường phát triển (Development Environment) cho cả hai phía Frontend và Backend.
- Phân tích thiết kế và xây dựng thành công Database Schema đáp ứng đầy đủ các yêu cầu nghiệp vụ của hệ thống NeonFoodMap.
- Hoàn thành việc phát triển các API RESTful trên Django REST Framework, tích hợp hệ thống xác thực JWT và dịch vụ AWS Polly Text-to-Speech.
- Xây dựng thành công giao diện người dùng (UI) bằng ReactJS tích hợp bản đồ tương tác, đảm bảo tính responsive và thân thiện với người dùng.
- Tích hợp và kiểm thử luồng gọi API từ Frontend tới Backend bằng Postman, đảm bảo dữ liệu được truy xuất và cập nhật chính xác trước khi sẵn sàng đóng gói container.

