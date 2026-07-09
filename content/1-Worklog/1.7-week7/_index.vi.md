---
title: "Worklog Tuần 7"
date: 2026-06-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

> [!IMPORTANT]
> ### 🎯 Mục tiêu Tuần 7
> **Nắm vững bảo mật AWS – IAM (Identity and Access Management)**: hiểu Users, Groups, Roles, Policies và nguyên tắc Least Privilege; thực hành phân quyền chi tiết cho từng dịch vụ, cấu hình MFA và xây dựng chiến lược bảo mật nhiều lớp cho tài khoản AWS.

### 📅 Kế hoạch triển khai chi tiết:
| Thứ | Công việc chi tiết | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :---: |
| **Thứ 2** | Xem video **Module 04-01** (AWS IAM – Tổng quan) và **Module 04-02** (Users, Groups & Policies). Ghi chép sự khác biệt giữa Identity-based Policy và Resource-based Policy. | 01/06/2026 | 01/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 3** | Xem video **Module 04-03** (IAM Roles & Instance Profiles) và **Module 04-04** (AWS Organizations & SCPs). Tìm hiểu cách EC2 dùng IAM Role để gọi S3 API mà không cần Access Key. | 02/06/2026 | 02/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 4** | **Thực hành Lab IAM – Phần 1:**<br>• Tạo IAM User mới, gán vào Group `Developers`.<br>• Viết Custom Policy JSON chỉ cho phép S3 Read-Only.<br>• Bật MFA cho IAM User bằng Google Authenticator. | 03/06/2026 | 03/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 5** | **Thực hành Lab IAM – Phần 2:**<br>• Tạo IAM Role cho EC2 có quyền ghi vào S3 và đọc từ DynamoDB.<br>• Gắn Role vào EC2 instance và xác minh quyền bằng AWS CLI (`aws sts get-caller-identity`).<br>• Kiểm tra IAM Access Analyzer để phát hiện quyền dư thừa. | 04/06/2026 | 04/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 6** | Tìm hiểu **AWS Security Hub** và **AWS GuardDuty** (giám sát mối đe dọa).<br>• Xem báo cáo IAM Credential Report và xử lý các rủi ro bảo mật phát hiện được.<br>• Viết và đăng tải **Worklog Tuần 7** lên website. | 05/06/2026 | 05/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Kết quả đạt được (Deliverables)
> *   [x] **Hệ thống phân quyền IAM** theo đúng nguyên tắc Least Privilege với User, Group, Role và Custom Policy.
> *   [x] **MFA đã bật** cho tất cả IAM User quan trọng, tăng cường bảo mật tài khoản.
> *   [x] **EC2 sử dụng IAM Role** để gọi S3 và DynamoDB API mà không cần lưu Access Key trên máy.
> *   [x] **IAM Access Analyzer** không phát hiện quyền truy cập bất thường nào từ bên ngoài.
> *   [x] **Báo cáo Worklog Tuần 7** được cập nhật đầy đủ và xuất bản thành công trên trang này.
