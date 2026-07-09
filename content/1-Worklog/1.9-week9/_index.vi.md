---
title: "Worklog Tuần 9"
date: 2026-06-15
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

> [!IMPORTANT]
> ### 🎯 Mục tiêu Tuần 9
> **Xây dựng ứng dụng Serverless trên AWS – Lambda, API Gateway & SQS**: hiểu kiến trúc hướng sự kiện (event-driven), triển khai hàm Lambda bằng Python/Node.js, tạo REST API không cần quản lý server và kết nối với hàng đợi tin nhắn SQS để xử lý bất đồng bộ.

### 📅 Kế hoạch triển khai chi tiết:
| Thứ | Công việc chi tiết | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :---: |
| **Thứ 2** | Xem video **Module 05-06** (AWS Lambda – Giới thiệu) và **Module 05-07** (Lambda Triggers & Execution Model). Ghi chép vòng đời của một Lambda invocation: Cold Start vs Warm Start. | 15/06/2026 | 15/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 3** | Xem video **Module 05-08** (Amazon API Gateway) và **Module 05-09** (SQS & Event-Driven Architecture). Tìm hiểu cách API Gateway kết nối với Lambda qua Proxy Integration. | 16/06/2026 | 16/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 4** | **Thực hành Lab Lambda:**<br>• Viết hàm Lambda Python trả về JSON response.<br>• Cấu hình trigger từ S3 Event: khi upload file ảnh → Lambda resize tự động.<br>• Xem CloudWatch Logs để debug và kiểm tra thực thi. | 17/06/2026 | 17/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 5** | **Thực hành Lab API Gateway + Lambda:**<br>• Tạo REST API với 3 endpoint: GET /items, POST /items, DELETE /items/{id}.<br>• Tích hợp Lambda xử lý logic và DynamoDB lưu trữ dữ liệu.<br>• Test API bằng Postman và deploy lên Stage `production`. | 18/06/2026 | 18/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 6** | **Thực hành Lab SQS:**<br>• Tạo SQS Standard Queue và Dead Letter Queue (DLQ).<br>• Viết Lambda producer gửi message và Lambda consumer xử lý.<br>• Kiểm tra xử lý lỗi và retry mechanism.<br>• Viết và đăng tải **Worklog Tuần 9** lên website. | 19/06/2026 | 19/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Kết quả đạt được (Deliverables)
> *   [x] **Serverless API** hoàn chỉnh với API Gateway + Lambda + DynamoDB, test pass qua Postman.
> *   [x] **Lambda S3 Trigger** tự động xử lý ảnh upload và lưu kết quả vào bucket đích.
> *   [x] **SQS Pipeline** bất đồng bộ hoạt động với Dead Letter Queue xử lý message lỗi đúng cách.
> *   [x] **Báo cáo Worklog Tuần 9** được cập nhật đầy đủ và xuất bản thành công trên trang này.
