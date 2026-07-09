---
title: "Worklog Tuần 8"
date: 2026-06-08
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

> [!IMPORTANT]
> ### 🎯 Mục tiêu Tuần 8
> **Nắm vững giám sát & tự động hóa AWS – CloudWatch, Auto Scaling và CloudFormation**: thiết lập hệ thống cảnh báo thời gian thực, tự động scale EC2 theo tải, và viết Infrastructure as Code (IaC) bằng CloudFormation template để tái sử dụng kiến trúc.

### 📅 Kế hoạch triển khai chi tiết:
| Thứ | Công việc chi tiết | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :---: |
| **Thứ 2** | Xem video **Module 05-01** (Amazon CloudWatch – Giới thiệu) và **Module 05-02** (CloudWatch Metrics, Alarms & Dashboards). Ghi chép các Namespace metrics quan trọng: EC2, RDS, S3. | 08/06/2026 | 08/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 3** | Xem video **Module 05-03** (EC2 Auto Scaling) và **Module 05-04** (Elastic Load Balancing nâng cao). Tìm hiểu sự khác biệt giữa Target Tracking, Step Scaling và Scheduled Scaling. | 09/06/2026 | 09/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 4** | **Thực hành Lab CloudWatch:**<br>• Tạo CloudWatch Dashboard hiển thị CPU, Network In/Out của EC2.<br>• Cấu hình Alarm gửi email qua SNS khi CPU > 70%.<br>• Bật CloudWatch Logs Agent để thu thập log từ Apache. | 10/06/2026 | 10/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 5** | **Thực hành Lab Auto Scaling:**<br>• Tạo Launch Template cho EC2 web server.<br>• Tạo Auto Scaling Group (min: 1, desired: 2, max: 4).<br>• Gắn ALB vào ASG và kiểm tra scale-out bằng `stress` tool. | 11/06/2026 | 11/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 6** | Xem video **Module 05-05** (AWS CloudFormation – IaC).<br>• Viết CloudFormation template YAML tạo VPC + Subnet + EC2 tự động.<br>• Deploy stack và verify tài nguyên được tạo đúng cấu hình.<br>• Viết và đăng tải **Worklog Tuần 8** lên website. | 12/06/2026 | 12/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Kết quả đạt được (Deliverables)
> *   [x] **CloudWatch Dashboard** giám sát EC2 real-time với ít nhất 4 metrics và 1 Alarm SNS email.
> *   [x] **Auto Scaling Group** tự động scale-out khi CPU vượt ngưỡng, xác nhận qua CloudWatch Graph.
> *   [x] **CloudFormation Stack** tạo thành công toàn bộ hạ tầng VPC + EC2 chỉ bằng 1 lệnh deploy.
> *   [x] **Báo cáo Worklog Tuần 8** được cập nhật đầy đủ và xuất bản thành công trên trang này.
