---
title: "Workshop"
date: 2026-07-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

<div class="lms">

# WORKSHOP — Triển khai hệ thống LMS trên AWS

Workshop này hướng dẫn từng bước xây dựng **LMS-Management-System** (hệ thống quản lý học tập trực tuyến) trên AWS theo kiến trúc có tính sẵn sàng cao: người dùng truy cập qua **CloudFlare** và **AWS Amplify** (giao diện), backend chạy trên **EC2** phía sau **Application Load Balancer** + **Auto Scaling Group**, dữ liệu lưu ở **Amazon DocumentDB** (Multi-AZ), toàn bộ được giám sát bằng **CloudWatch**, **CloudTrail** và cảnh báo qua **Amazon SNS**.

### 📚 Nội dung workshop

* **5.1** — [Giới thiệu](5.1-gioi-thieu/)
* **5.2** — [Xây dựng hạ tầng mạng](5.2-ha-tang-mang/)
* **5.3** — [Triển khai Backend](5.3-backend/)
* **5.4** — [Cấu hình tên miền & giao diện](5.4-domain-frontend/)
* **5.5** — [Cân bằng tải & Auto Scaling](5.5-loadbalancing-autoscaling/)
* **5.6** — [Giám sát hệ thống](5.6-giam-sat/)
* **5.7** — [Dọn dẹp tài nguyên](5.7-don-dep/)

</div>
