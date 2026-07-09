---
title: "Worklog Tuần 4"
date: 2026-05-11
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

> [!IMPORTANT]
> ### 🎯 Mục tiêu Tuần 4
> **Nắm vững dịch vụ mạng AWS – Amazon VPC**: hiểu kiến trúc mạng ảo Private/Public Subnet, Route Table, Internet Gateway, NAT Gateway; tự thiết kế và triển khai một hệ thống VPC đa tầng (multi-tier) hoàn chỉnh trên AWS Console.

### 📅 Kế hoạch triển khai chi tiết:
| Thứ | Công việc chi tiết | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :---: |
| **Thứ 2** | Xem video **Module 02-05** (Amazon VPC – Giới thiệu) và **Module 02-06** (Subnet, Route Table, Internet Gateway). Vẽ sơ đồ kiến trúc VPC 2 tầng (Public + Private Subnet). | 11/05/2026 | 11/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 3** | Xem video **Module 02-07** (NAT Gateway & Security) và **Module 02-08** (VPC Peering & Endpoints). Tìm hiểu sự khác biệt giữa Security Group và Network ACL. | 12/05/2026 | 12/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 4** | **Thực hành Lab VPC – Phần 1:**<br>• Tạo VPC tùy chỉnh (CIDR: 10.0.0.0/16).<br>• Tạo Public Subnet (10.0.1.0/24) và Private Subnet (10.0.2.0/24).<br>• Gắn Internet Gateway và cấu hình Route Table cho Public Subnet. | 13/05/2026 | 13/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 5** | **Thực hành Lab VPC – Phần 2:**<br>• Tạo NAT Gateway để Private Subnet có thể ra Internet.<br>• Deploy EC2 vào Public Subnet (web server) và Private Subnet (backend).<br>• Kiểm tra kết nối giữa 2 tầng qua Security Group. | 14/05/2026 | 14/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 6** | Tìm hiểu **Elastic Load Balancer (ALB)** cơ bản.<br>• Thực hành tạo ALB phân phối traffic giữa 2 EC2 instance.<br>• Viết và đăng tải **Worklog Tuần 4** lên website. | 15/05/2026 | 15/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Kết quả đạt được (Deliverables)
> *   [x] **Kiến trúc VPC hoàn chỉnh** với Public + Private Subnet, Internet Gateway và NAT Gateway hoạt động đúng.
> *   [x] **Sơ đồ draw.io** thể hiện luồng kết nối mạng từ Internet → ALB → EC2 Public → EC2 Private.
> *   [x] **Application Load Balancer** phân phối traffic thành công giữa 2 EC2 instance.
> *   [x] **Báo cáo Worklog Tuần 4** được cập nhật đầy đủ và xuất bản thành công trên trang này.
