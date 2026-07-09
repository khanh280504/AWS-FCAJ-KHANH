---
title: "Worklog Tuần 11"
date: 2026-06-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

> [!IMPORTANT]
> ### 🎯 Mục tiêu Tuần 11
> **Xây dựng dự án cuối khoá (Capstone Project)**: thiết kế và triển khai một hệ thống web hoàn chỉnh trên AWS tích hợp tất cả kiến thức đã học (VPC, EC2, RDS, S3, IAM, CloudWatch, CI/CD); chuẩn bị tài liệu kiến trúc và slide thuyết trình cho buổi demo cuối khoá.

### 📅 Kế hoạch triển khai chi tiết:
| Thứ | Công việc chi tiết | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :---: |
| **Thứ 2** | Lên ý tưởng và phác thảo kiến trúc Capstone Project.<br>• Xác định yêu cầu: tối thiểu dùng 5 dịch vụ AWS.<br>• Vẽ sơ đồ kiến trúc chi tiết trên **draw.io** bao gồm luồng dữ liệu và phân quyền IAM. | 29/06/2026 | 29/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 3** | Xây dựng hạ tầng nền tảng bằng **CloudFormation**:<br>• Deploy VPC multi-AZ, Public/Private Subnets, ALB, Auto Scaling Group.<br>• Tạo RDS Multi-AZ trong Private Subnet với automated backup. | 30/06/2026 | 30/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 4** | Phát triển backend ứng dụng:<br>• Deploy API bằng Lambda + API Gateway kết nối DynamoDB.<br>• Cấu hình S3 + CloudFront cho static frontend.<br>• Tích hợp **AWS Cognito** để xác thực người dùng (login/register). | 01/07/2026 | 01/07/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 5** | Hoàn thiện vận hành & bảo mật:<br>• Cài đặt CloudWatch Dashboard tổng hợp toàn bộ hệ thống.<br>• Cấu hình WAF (Web Application Firewall) bảo vệ API Gateway.<br>• Thiết lập CI/CD Pipeline tự động deploy khi push code mới. | 02/07/2026 | 02/07/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 6** | Kiểm thử tổng hợp toàn bộ hệ thống:<br>• Load test bằng `Apache JMeter` kiểm tra Auto Scaling hoạt động đúng.<br>• Thực hiện disaster recovery drill: xoá RDS → restore từ snapshot.<br>• Viết và đăng tải **Worklog Tuần 11** lên website. | 03/07/2026 | 03/07/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Kết quả đạt được (Deliverables)
> *   [x] **Sơ đồ kiến trúc Capstone** hoàn chỉnh trên draw.io, thể hiện đầy đủ tất cả dịch vụ và luồng kết nối.
> *   [x] **Hệ thống web** chạy ổn định trên AWS với đầy đủ: frontend (S3+CF), backend (Lambda+APIGW), DB (RDS+DynamoDB).
> *   [x] **CI/CD Pipeline** tự động deploy, CloudWatch giám sát và WAF bảo vệ toàn bộ hệ thống.
> *   [x] **Load test** xác nhận Auto Scaling hoạt động đúng và hệ thống xử lý được ≥ 100 req/s.
> *   [x] **Báo cáo Worklog Tuần 11** được cập nhật đầy đủ và xuất bản thành công trên trang này.
