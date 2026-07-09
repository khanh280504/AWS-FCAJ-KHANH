---
title: "Worklog Tuần 5"
date: 2026-05-18
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

> [!IMPORTANT]
> ### 🎯 Mục tiêu Tuần 5
> **Nắm vững dịch vụ lưu trữ AWS – Amazon S3**: hiểu các loại Storage Class, Bucket Policy, Versioning, và Static Website Hosting; thực hành upload/download dữ liệu bằng cả Console lẫn AWS CLI, đồng thời tích hợp S3 với CloudFront để tăng tốc phân phối nội dung.

### 📅 Kế hoạch triển khai chi tiết:
| Thứ | Công việc chi tiết | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :---: |
| **Thứ 2** | Xem video **Module 03-01** (Amazon S3 – Giới thiệu) và **Module 03-02** (S3 Storage Classes). Ghi chép bảng so sánh chi phí & độ trễ của Standard, Infrequent Access, Glacier. | 18/05/2026 | 18/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 3** | Xem video **Module 03-03** (S3 Security: Bucket Policy, ACL) và **Module 03-04** (S3 Versioning & Lifecycle). Tìm hiểu cách viết Bucket Policy JSON để phân quyền truy cập. | 19/05/2026 | 19/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 4** | **Thực hành Lab S3 – Phần 1:**<br>• Tạo S3 Bucket với Versioning bật sẵn.<br>• Upload file bằng Console và AWS CLI (`aws s3 cp`, `aws s3 sync`).<br>• Cấu hình Bucket Policy cho phép truy cập public read. | 20/05/2026 | 20/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 5** | **Thực hành Lab S3 – Phần 2:**<br>• Bật **Static Website Hosting** trên S3, deploy trang HTML/CSS mẫu.<br>• Tạo **CloudFront Distribution** trỏ về S3 Origin.<br>• Kiểm tra tốc độ truy cập qua CloudFront URL. | 21/05/2026 | 21/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 6** | Cấu hình **S3 Lifecycle Policy** tự động chuyển object cũ sang Glacier sau 30 ngày.<br>• Kiểm tra và dọn dẹp tài nguyên sau lab.<br>• Viết và đăng tải **Worklog Tuần 5** lên website. | 22/05/2026 | 22/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Kết quả đạt được (Deliverables)
> *   [x] **S3 Bucket** với Versioning, Lifecycle Policy và Bucket Policy được cấu hình đúng.
> *   [x] **Website tĩnh** được deploy lên S3 và phân phối qua CloudFront truy cập thành công từ trình duyệt.
> *   [x] **CLI proficient**: thực hiện thành thạo các lệnh `aws s3 cp`, `aws s3 sync`, `aws s3 ls`.
> *   [x] **Báo cáo Worklog Tuần 5** được cập nhật đầy đủ và xuất bản thành công trên trang này.
