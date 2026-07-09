---
title: "Worklog Tuần 3"
date: 2026-05-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

> [!IMPORTANT]
> ### 🎯 Mục tiêu Tuần 3
> **Nắm vững kiến thức Module 02 về dịch vụ EC2**: hiểu các loại instance, AMI, Security Group, và thực hành tạo máy chủ ảo trên cloud; kết nối SSH thành công và triển khai ứng dụng web tĩnh đơn giản.

### 📅 Kế hoạch triển khai chi tiết:
| Thứ | Công việc chi tiết | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :---: |
| **Thứ 2** | Xem video **Module 02-01** (Giới thiệu Amazon EC2) và **Module 02-02** (EC2 Instance Types & Pricing). Ghi chép các dòng máy t2, t3, m5 và trường hợp sử dụng. | 04/05/2026 | 04/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 3** | Xem video **Module 02-03** (AMI & Launch Template) và **Module 02-04** (Security Groups & Key Pairs). Tìm hiểu sự khác biệt Public/Private Key và cách mở port an toàn. | 05/05/2026 | 05/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 4** | **Thực hành Lab EC2 – Phần 1:**<br>• Tạo EC2 instance (Amazon Linux 2, t2.micro - Free Tier).<br>• Tạo và lưu Key Pair (.pem).<br>• Cấu hình Security Group mở port 22 (SSH) và 80 (HTTP). | 06/05/2026 | 06/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 5** | **Thực hành Lab EC2 – Phần 2:**<br>• Kết nối SSH vào EC2 từ máy tính cá nhân.<br>• Cài đặt Apache Web Server (httpd).<br>• Deploy trang HTML đơn giản, truy cập qua Public IP. | 07/05/2026 | 07/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 6** | Tìm hiểu **Elastic IP** (IP tĩnh) và **EBS Volume** (ổ đĩa gắn thêm).<br>• Gắn thêm EBS vào EC2, mount và lưu dữ liệu.<br>• Viết và đăng tải **Worklog Tuần 3** lên website. | 08/05/2026 | 08/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Kết quả đạt được (Deliverables)
> *   [x] **EC2 instance hoạt động** trên môi trường Free Tier với cấu hình Security Group đúng chuẩn.
> *   [x] **Kết nối SSH thành công** từ máy tính cá nhân vào máy chủ EC2 trên cloud.
> *   [x] **Web server Apache** được cài đặt và trang HTML mẫu hiển thị qua trình duyệt bằng Public IP.
> *   [x] **EBS Volume** được gắn, mount và lưu dữ liệu thành công vào EC2.
> *   [x] **Báo cáo Worklog Tuần 3** được cập nhật đầy đủ và xuất bản thành công trên trang này.
