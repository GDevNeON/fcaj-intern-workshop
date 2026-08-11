---
title : "Dọn dẹp tài nguyên AWS"
date : 2026-08-10
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

### Mục tiêu

Sau khi hoàn thành thực hành bài Workshop **NeonFoodMap** và kiểm thử các tính năng hệ thống, bạn nên tiến hành dọn dẹp (Cleanup) toàn bộ các tài nguyên đã khởi tạo trên AWS. Việc này giúp đảm bảo tài khoản AWS của bạn không phát sinh các chi phí ngoài ý muốn từ các tài nguyên đang chạy như NAT Gateway, ECS Tasks, RDS Instance hay Load Balancer.

### Nguyên tắc dọn dẹp tài nguyên

Các tài nguyên trên AWS có mối quan hệ phụ thuộc lẫn nhau (Dependency). Do đó, bạn cần thực hiện dọn dẹp theo **trình tự ngược lại** với quá trình khởi tạo (từ tầng ứng dụng, CDN, Load Balancer xuống cơ sở dữ liệu, lưu trữ S3 và cuối cùng là hạ tầng mạng VPC).

---

### Quy trình dọn dẹp chi tiết từng bước

#### 1. Hủy dịch vụ và dừng ECS Tasks (Amazon ECS Fargate)
1. Truy cập **AWS Management Console** -> tìm kiếm dịch vụ **Elastic Container Service (ECS)**.
2. Chọn Cluster `cls-neonfoodmap` (hoặc `NeonFoodmap-cluster`).
3. Trong tab **Services**, chọn các Service đang chạy: `svc-neonfoodmap-be` và `svc-neonfoodmap-fe`.
4. Nhấn **Update service** -> thay đổi **Desired tasks** về `0` -> nhấn **Update**.
5. Sau khi số lượng Task đang chạy chuyển về `0`, chọn lại các Service -> nhấn **Delete**.
6. Xác nhận xóa bằng cách nhập `delete` -> nhấn **Delete**.
7. Chuyển sang menu **Task Definitions**, chọn các Task Definition `task-neonfoodmap-be` và `task-neonfoodmap-fe` -> chọn tất cả Revisions -> nhấn **Actions** -> **Deregister**.

---

#### 2. Vô hiệu hóa và xóa CDN (Amazon CloudFront Distribution)
1. Truy cập dịch vụ **CloudFront Console**.
2. Chọn Distribution `neonfoodmap-frontend-cdn` đang ở trạng thái `Enabled`.
3. Nhấn **Disable** -> xác nhận vô hiệu hóa.
4. Chờ khoảng 3-5 phút cho đến khi trạng thái chuyển thành `Disabled`.
5. Chọn Distribution đó một lần nữa -> nhấn nút **Delete** để xóa hẳn.

---

#### 3. Xóa Application Load Balancer và Target Groups
1. Truy cập dịch vụ **EC2 Console** -> chọn **Load Balancers** ở menu bên trái.
2. Chọn Application Load Balancer `alb-neonfoodmap`.
3. Nhấn **Actions** -> **Delete load balancer** -> xác nhận xóa.
4. Chuyển sang mục **Target Groups**.
5. Chọn hai Target Groups `tg-neonfoodmap-be` và `tg-neonfoodmap-fe`.
6. Nhấn **Actions** -> **Delete** -> chọn **Yes, delete**.

---

#### 4. Xóa Cơ sở dữ liệu Amazon RDS MySQL
1. Truy cập dịch vụ **Amazon RDS Console** -> chọn **Databases**.
2. Chọn DB Instance `rds-neonfoodmap-db`.
3. Nhấn **Actions** -> **Delete**.
4. Trong màn hình xác nhận:
   - Bỏ chọn **Create final snapshot?** (nếu không cần lưu bản sao).
   - Tích chọn **I acknowledge that upon database deletion, Automated backups...**.
   - Nhập `delete me` vào ô xác nhận -> nhấn **Delete**.
5. Chuyển sang mục **Subnet groups** -> chọn DB Subnet Group `dbsg-neonfoodmap` -> nhấn **Delete**.

---

#### 5. Làm rỗng và xóa các S3 Buckets
1. Truy cập dịch vụ **Amazon S3 Console**.
2. Với từng bucket (`neon-food-map-frontend`, `neon-food-map-media`, `neon-food-map-audio`, `neon-food-map-logs`):
   - Chọn tên bucket -> nhấn nút **Empty** (Làm rỗng).
   - Nhập `permanently delete` -> nhấn **Empty** để xóa sạch toàn bộ objects và log files chứa bên trong.
   - Sau khi bucket đã rỗng, quay lại danh sách Buckets -> chọn bucket -> nhấn nút **Delete**.
   - Nhập lại tên đầy đủ của bucket -> nhấn **Delete bucket**.

---

#### 6. Xóa Amazon ECR Repositories
1. Truy cập dịch vụ **Amazon ECR Console** -> chọn **Repositories**.
2. Chọn các kho lưu trữ `neon-food-map-backend` và `neon-food-map-frontend`.
3. Nhấn nút **Delete**.
4. Nhập `delete` vào ô xác nhận để xóa toàn bộ Docker Container Images chứa trong ECR.

---

#### 7. Xóa giám sát CloudWatch & AWS Budgets
1. Truy cập dịch vụ **Amazon CloudWatch Console**.
2. **Dashboards**: chọn `NeonFoodMap-Operational-Dashboard` -> chọn **Delete dashboard**.
3. **Alarms**: chọn các cảnh báo `ALB-5XX-Error-Alarm`, `ECS-CPU-Alarm` -> nhấn **Actions** -> **Delete**.
4. **Log groups**: chọn các nhóm log `/ecs/neon-food-map`, `/aws/alb/neonfoodmap` -> chọn **Actions** -> **Delete log group**.
5. Truy cập **AWS Budgets Console** -> chọn Budget alert đã tạo -> nhấn **Delete**.

---

#### 8. Xóa CloudFormation Stacks & IAM Roles
1. Truy cập dịch vụ **AWS CloudFormation Console**.
2. Chọn Stack `NeonFoodMap-IAM-Stack` -> chọn **Delete** -> xác nhận **Delete stack**.
3. Nếu tạo thủ công trong **IAM Console**:
   - Vào **Roles**: xóa các role `ECS-TaskExecutionRole`, `ECS-TaskRole`, và `GitHubActions-ECR-ECS-DeployRole`.
   - Vào **Identity Providers**: chọn OIDC provider `token.actions.githubusercontent.com` -> nhấn **Delete**.

---

#### 9. Xóa NAT Gateway, Elastic IP và Amazon VPC
1. Truy cập **Amazon VPC Console**.
2. **NAT Gateways**: chọn NAT Gateway đặt tại Public Subnet -> nhấn **Actions** -> **Delete NAT gateway**.
3. **Elastic IPs**: chọn địa chỉ IP động đã gán cho NAT Gateway -> nhấn **Actions** -> **Release Elastic IP addresses**.
4. **Security Groups**: xóa các Security Group tùy chỉnh `sg-rds-mysql`, `sg-ecs-backend`, `sg-alb` (Lưu ý: ngắt liên kết Security Group trước khi xóa).
5. **Your VPCs**: chọn VPC `vpc-neonfoodmap` -> nhấn **Actions** -> **Delete VPC**.
   - AWS sẽ tự động xóa tất cả các Subnets, Route Tables, Internet Gateway và Network ACLs liên kết trực thuộc VPC này.

---

### Xác nhận dọn dẹp hoàn tất

Sau khi thực hiện xong 9 bước trên, bạn có thể vào lại **AWS Billing & Cost Management Dashboard** hoặc kiểm tra **Resource Groups & Tag Editor** để xác nhận không còn tài nguyên nào tính phí đang tiếp tục chạy ngầm trong tài khoản của bạn.
