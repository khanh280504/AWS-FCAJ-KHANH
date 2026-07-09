---
title: "Worklog Tuần 10"
date: 2026-06-22
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

> [!IMPORTANT]
> ### 🎯 Mục tiêu Tuần 10
> **Xây dựng CI/CD Pipeline hoàn chỉnh trên AWS**: tự động hóa toàn bộ quy trình từ commit code đến deploy production bằng CodeCommit, CodeBuild và CodePipeline; áp dụng thực tiễn DevOps để rút ngắn chu kỳ phát hành và tăng độ tin cậy của ứng dụng.

### 📅 Kế hoạch triển khai chi tiết:
| Thứ | Công việc chi tiết | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| :---: | :--- | :---: | :---: | :---: |
| **Thứ 2** | Xem video **Module 05-10** (DevOps trên AWS – Tổng quan) và **Module 05-11** (AWS CodeCommit & CodeBuild). Tìm hiểu quy trình GitFlow và cách tích hợp với AWS Developer Tools. | 22/06/2026 | 22/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 3** | Xem video **Module 05-12** (AWS CodeDeploy & CodePipeline). Ghi chép sự khác biệt giữa In-place Deployment và Blue/Green Deployment trong CodeDeploy. | 23/06/2026 | 23/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 4** | **Thực hành Lab CI/CD – Phần 1:**<br>• Tạo CodeCommit repository, clone và push code lên.<br>• Viết `buildspec.yml` cho CodeBuild: install dependencies, run tests, build artifact.<br>• Kết nối CodeBuild với CodeCommit, chạy build lần đầu thành công. | 24/06/2026 | 24/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 5** | **Thực hành Lab CI/CD – Phần 2:**<br>• Tạo CodePipeline với 3 stage: Source → Build → Deploy.<br>• Cấu hình CodeDeploy với Blue/Green deployment lên EC2 Auto Scaling Group.<br>• Trigger pipeline tự động khi push commit mới lên branch `main`. | 25/06/2026 | 25/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thứ 6** | Tích hợp **GitHub Actions** như một lựa chọn thay thế CodePipeline.<br>• So sánh ưu nhược điểm của AWS native CI/CD vs GitHub Actions.<br>• Review toàn bộ kiến trúc CI/CD đã xây dựng.<br>• Viết và đăng tải **Worklog Tuần 10** lên website. | 26/06/2026 | 26/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Kết quả đạt được (Deliverables)
> *   [x] **CI/CD Pipeline hoàn chỉnh** tự động build, test và deploy khi có commit mới lên branch `main`.
> *   [x] **Blue/Green Deployment** hoạt động với zero-downtime, rollback tự động khi deploy thất bại.
> *   [x] **Buildspec.yml** chạy unit test và chặn deploy khi test fail, đảm bảo chất lượng code.
> *   [x] **Báo cáo Worklog Tuần 10** được cập nhật đầy đủ và xuất bản thành công trên trang này.
