---
title: "Worklog Tuần 6"
date: 2026-05-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

> [!IMPORTANT]
> ### 🎯 Mục tiêu Tuần 6
> **Nắm vững dịch vụ cơ sở dữ liệu AWS – Amazon RDS & DynamoDB**: hiểu sự khác biệt giữa cơ sở dữ liệu quan hệ (RDS) và NoSQL (DynamoDB); thực hành tạo và kết nối RDS MySQL, thiết kế bảng DynamoDB và tích hợp với ứng dụng trên EC2.

### 📅 Kế hoạch triển khai chi tiết:
| Thứ | Công việc chi tiết | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :---: |
| **Thứ 2** | Xem video **Module 03-05** (Amazon RDS – Giới thiệu) và **Module 03-06** (RDS Multi-AZ & Read Replicas). Ghi chép bảng so sánh các engine: MySQL, PostgreSQL, Aurora. | 25/05/2026 | 25/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 3** | Xem video **Module 03-07** (Amazon DynamoDB – Giới thiệu) và **Module 03-08** (DynamoDB Partitions & Indexes). Tìm hiểu cách thiết kế Partition Key và Sort Key hiệu quả. | 26/05/2026 | 26/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 4** | **Thực hành Lab RDS:**<br>• Tạo RDS MySQL instance (db.t3.micro – Free Tier) trong Private Subnet.<br>• Cấu hình Security Group cho phép EC2 kết nối port 3306.<br>• Kết nối từ EC2 bằng MySQL CLI, tạo database và bảng mẫu. | 27/05/2026 | 27/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 5** | **Thực hành Lab DynamoDB:**<br>• Tạo DynamoDB table (Partition Key: `userId`, Sort Key: `timestamp`).<br>• Thực hiện thao tác PutItem, GetItem, Query bằng AWS CLI.<br>• Tạo Global Secondary Index (GSI) để tăng hiệu suất truy vấn. | 28/05/2026 | 28/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 6** | Tích hợp RDS và DynamoDB vào ứng dụng web chạy trên EC2.<br>• So sánh use case của từng loại database qua bài tập thực tế.<br>• Viết và đăng tải **Worklog Tuần 6** lên website. | 29/05/2026 | 29/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Kết quả đạt được (Deliverables)
> *   [x] **RDS MySQL instance** triển khai thành công trong Private Subnet, kết nối được từ EC2.
> *   [x] **DynamoDB table** với GSI được tạo và thực hiện thành thạo các thao tác CRUD qua CLI.
> *   [x] **Kiến trúc 3-tier** (Web EC2 → RDS/DynamoDB) được deploy và hoạt động ổn định.
> *   [x] **Báo cáo Worklog Tuần 6** được cập nhật đầy đủ và xuất bản thành công trên trang này.
