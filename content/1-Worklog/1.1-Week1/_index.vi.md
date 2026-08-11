---
title: "Worklog Tuần 1"
date: 2026-06-22
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:

- Tìm hiểu nền tảng AWS Global Infrastructure và nguyên tắc bảo mật IAM Best Practices.
- Khởi tạo phạm vi dự án, phân tích yêu cầu nghiệp vụ và thiết kế kiến trúc hệ thống NeonFoodMap.

### Các công việc triển khai trong tuần:

| Thứ | Công việc thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Tham gia Onboarding chương trình FCAJ tại văn phòng AWS (Bitexco) <br> - Tìm hiểu AWS Global Infrastructure (Region, AZ, Edge) & IAM Best Practices | 22/06/2026 | 22/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Tìm hiểu dịch vụ cốt lõi VPC, EC2, S3, RDS <br> - Khởi tạo AWS Free Tier, cấu hình AWS CLI & kiểm tra IAM Users | 23/06/2026 | 23/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Thảo luận chốt đề tài dự án **NeonFoodMap** <br> - Phân tích yêu cầu nghiệp vụ và tính năng cốt lõi (POI Search, Audio Commentary) | 24/06/2026 | 24/06/2026 | |
| 5 | - Lựa chọn và xác định các thành phần hạ tầng dịch vụ triển khai trên AWS | 25/06/2026 | 25/06/2026 | |
| 6 | - Thiết kế sơ đồ kiến trúc tổng thể (Architecture Diagram) & sơ đồ luồng dữ liệu (DFD) | 26/06/2026 | 26/06/2026 | |

### Chi tiết công việc thực hiện theo ngày:

- **Thứ 2 (22/06/2026):** Tham gia buổi Onboarding định hướng chương trình FCAJ tại văn phòng AWS Việt Nam (Tầng 26, Tòa nhà Bitexco Financial Tower). Nghiên cứu tổng quan hạ tầng toàn cầu của AWS (Global Infrastructure): Region (`ap-southeast-1` Singapore), Availability Zone (Multi-AZ architecture) và các trạm Edge Location. Tìm hiểu AWS IAM Best Practices: vô hiệu hóa Access Key cho Root User, bắt buộc kích hoạt xác thực hai yếu tố (MFA), khởi tạo IAM Admin User và áp dụng nguyên tắc phân quyền tối thiểu (Least Privilege).
- **Thứ 3 (23/06/2026):** Nghiên cứu chi tiết các nhóm dịch vụ đám mây AWS cốt lõi: Compute (EC2, ECS), Storage (S3, EBS), Networking (VPC), Database (RDS). Thực hành đăng ký tài khoản AWS Free Tier, thiết lập bảo mật MFA. Cài đặt và cấu hình AWS CLI trên máy cục bộ (`aws configure`, khai báo Default Region `ap-southeast-1` và output format `json`), kiểm tra kết nối với AWS Cloud bằng lệnh `aws sts get-caller-identity`.
- **Thứ 4 (24/06/2026):** Họp nhóm thảo luận và thống nhất lựa chọn đề tài dự án thực tiễn: **NeonFoodMap** – Ứng dụng bản đồ ẩm thực tương tác tích hợp định vị GPS thời gian thực, tìm kiếm địa điểm POI theo bán kính và thuyết minh tự động bằng giọng nói (Text-to-Speech). Phân tích yêu cầu nghiệp vụ hệ thống và yêu cầu phi chức năng (khả năng chịu tải, tính sẵn sàng cao Multi-AZ và bảo mật OIDC).
- **Thứ 5 (25/06/2026):** Xác định danh mục các dịch vụ AWS cần triển khai cho ứng dụng NeonFoodMap: Mạng VPC Multi-AZ (Public/Private Subnets, IGW, NAT Gateway), Cơ sở dữ liệu RDS MySQL 8.0, Lưu trữ Amazon S3, Điều phối Container Amazon ECS Fargate, Phân phối CDN CloudFront và Giám sát CloudWatch.
- **Thứ 6 (26/06/2026):** Sử dụng công cụ Draw.io thiết kế bản phác thảo Sơ đồ Kiến trúc tổng quan (Architecture Diagram) và Sơ đồ Luồng Dữ liệu (Data Flow Diagram - DFD Level 0 & Level 1) cho hệ thống NeonFoodMap, trình bày báo cáo tiến độ tuần 1 với Mentor hướng dẫn tại AWS.

### Kết quả đạt được tuần 1:

- Nắm vững các khái niệm nền tảng của AWS và cơ sở hạ tầng toàn cầu (Global Infrastructure) bao gồm Region, Availability Zone và Edge Location.
- Phân biệt rõ ràng vai trò của các nhóm dịch vụ chính yếu như Compute (EC2, ECS), Storage (S3, EBS), Networking (VPC), và Database (RDS MySQL).
- Thiết lập và bảo mật tài khoản AWS Free Tier thành công, thực hành áp dụng nguyên tắc đặc quyền tối thiểu (Least Privilege) với IAM.
- Thành thạo việc sử dụng AWS Management Console và cấu hình AWS CLI để tương tác với các tài nguyên AWS từ môi trường dòng lệnh.
- Xác định đề tài dự án NeonFoodMap, hoàn thành việc thu thập yêu cầu và phác thảo sơ đồ luồng dữ liệu (DFD), sơ đồ kiến trúc hệ thống tổng quan.

