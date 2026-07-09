---
title: "Event 3"
date: 2026-05-30
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

# BÀI THU HOẠCH: GIỚI THIỆU HERA — WORKSHOP VOICE AGENT TRÊN AWS
---
> [!IMPORTANT]
> ### 🎯 Mục tiêu & Tổng quan Workshop
> **Workshop Hera** là tài liệu thực hành chi tiết hướng dẫn triển khai **Bilingual Voice Agent** (Trợ lý giọng nói song ngữ) thời gian thực sử dụng **Amazon Bedrock AgentCore Runtime** và mô hình âm thanh **Amazon Nova 2 Sonic**.


## 1. Voice AI & Dự án Hera là gì?

### Thông tin tham dự sự kiện
* **Hình thức:** Online.
* **Nền tảng tham dự:** Google Meet.
* **Thời gian tham dự:** 20 giờ.

### Voice Agent

Voice Agent là dịch vụ trí tuệ nhân tạo (AI) hoạt động theo cơ chế **truyền phát âm thanh hai chiều theo thời gian thực** (*real-time bidirectional audio streaming*).

Luồng hoạt động:

1. Người dùng nói vào microphone.
2. Âm thanh được truyền tới mô hình speech-to-speech.
3. Mô hình xử lý và tạo phản hồi bằng giọng nói.
4. Âm thanh phản hồi được phát lại trên trình duyệt.

Toàn bộ chu kỳ diễn ra với độ trễ dưới **1 giây**.

### Hera

Hera sử dụng **Amazon Nova 2 Sonic**, mô hình speech-to-speech trên **Amazon Bedrock**, triển khai tại vùng **ap-northeast-1 (Tokyo)**.

Các khả năng nổi bật:

- Giao tiếp bằng giọng nói theo thời gian thực.
- Hỗ trợ gọi công cụ (*Tool Use*).
- Có thể truy vấn **Amazon Bedrock Knowledge Base** ngay trong cùng một luồng streaming.

---

## 2. Lý do lựa chọn Tech Stack

Workshop Hera được xây dựng dựa trên sự kết hợp của các công nghệ sau.

### Amazon Nova 2 Sonic

- Mô hình speech-to-speech thuần AWS.
- Độ trễ thấp từ Việt Nam.
- Tính phí theo phút sử dụng.
- Hỗ trợ Tool Use tự nhiên với Bedrock Knowledge Base.

### Amazon Bedrock AgentCore Runtime

- Managed runtime.
- Không cần cấu hình VPC, ALB hoặc NAT Gateway.
- Hỗ trợ ARM64.
- Bảo mật thông qua IMDSv2.
- Dễ debug và vận hành.

### Pipecat (v1.1.0)

Pipecat đóng vai trò điều phối (*orchestrator*) cho voice pipeline.

Đặc điểm:

- Tích hợp sẵn `AWSNovaSonicLLMService`.
- Tự động xử lý giới hạn stream tối đa **8 phút** của Nova Sonic.
- Quản lý toàn bộ voice loop.

### S3 Vectors + Titan v2

Giải pháp RAG chi phí thấp:

- Khoảng **0.10 USD/tháng** với dữ liệu nhỏ.
- Rẻ hơn đáng kể so với OpenSearch Serverless (**200–400 USD/tháng**).

### Terraform + AWS CDK (Python)

Kết hợp Infrastructure as Code:

| Công cụ | Vai trò |
|---------|----------|
| Terraform | Quản lý Bedrock Knowledge Base |
| AWS CDK (Python) | Triển khai AgentCore Runtime |

---

## 3. Kiến trúc tổng thể

Quy trình xử lý giọng nói diễn ra như sau.

### Bước 1. Yêu cầu kết nối

Trình duyệt yêu cầu một **WebSocket URL (WSS)** đã được ký bằng **AWS SigV4**, có thời hạn khoảng **300 giây** từ **Presigner Lambda**.

### Bước 2. Kết nối

Browser kết nối tới **AgentCore Runtime** (container Pipecat) thông qua WebSocket và truyền âm thanh **16 kHz**.

### Bước 3. Tool Use

AgentCore Runtime chuyển tiếp audio tới Nova 2 Sonic.

Khi Sonic phát hiện câu hỏi cần tra cứu dữ liệu, nó sẽ gọi công cụ:

```text
lookup_product
```

### Bước 4. RAG Retrieval

AgentCore Runtime gọi:

```text
bedrock-agent-runtime.retrieve
```

để truy vấn **Bedrock Knowledge Base**.

Knowledge Base trả về:

- Top 3 kết quả
- Từ S3 Vectors

Sau đó AgentCore Runtime gửi kết quả trở lại Nova Sonic trong cùng luồng streaming.

### Bước 5. Phản hồi

Nova Sonic:

- Sinh phản hồi bằng giọng nói 24 kHz.
- Gửi audio về AgentCore Runtime.
- AgentCore Runtime truyền lại trình duyệt.
- Browser phát âm thanh cho người dùng.

> Tổng thời gian xử lý cho một vòng hội thoại (End-to-End Turn) khoảng **3 giây**.

---

## 4. Region triển khai

Region mặc định:

```text
ap-northeast-1 (Tokyo)
```

Lý do:

- Độ trễ thấp nhất tới Việt Nam.
- Hỗ trợ đầy đủ:
  - Amazon Nova 2 Sonic
  - AgentCore Runtime
  - Bedrock Knowledge Base
  - S3 Vectors

Các region khác được hỗ trợ:

- `us-east-1`
- `us-west-2`
- `eu-north-1`

---

## 5. Yêu cầu trước khi bắt đầu

### Tài khoản AWS

Cần chuẩn bị:

- AWS Account
- IAM User
- Quyền `AdministratorAccess`

> Chỉ sử dụng cho workshop, không sử dụng tài khoản Root.

### Kiến thức

Người học nên có kiến thức cơ bản về:

- AWS Console
- IAM
- VPC
- Docker
- Terraform

### Công cụ cần cài đặt

- AWS CLI v2
- Terraform >= 1.9
- uv (Python package manager)
- Docker Desktop (hỗ trợ Buildx Multi-Arch)
- jq
- Chrome / Firefox / Safari (hỗ trợ HTTPS và microphone)

> Workshop sử dụng **uv**, không sử dụng `pip`.

### Chi phí

Ước tính:

- **2–5 USD**
- Cho khoảng **2 giờ** thực hành.

> Sau khi hoàn thành workshop, hãy thực hiện phần **Cleanup** để tránh phát sinh chi phí duy trì tài nguyên.

---

## 6. Quy ước của Workshop

### Mã nguồn

Source code được tổ chức theo từng **Phase** để thuận tiện theo dõi.

### Hình ảnh

Các screenshot đều có:

- Khung màu đỏ
- Mũi tên chỉ dẫn
- Chú thích tại các bước quan trọng trên AWS Console

### Ngôn ngữ

Workshop sử dụng:

- Chatbot: **Tiếng Anh** (Nova Sonic hoạt động tốt nhất với tiếng Anh)
- Tài liệu: **Song ngữ Anh – Việt (vi/en)**

> Hệ thống CI sẽ kiểm tra số lượng trang tiếng Việt và tiếng Anh. Build sẽ thất bại nếu hai ngôn ngữ không đồng bộ.

---

## 7. Nội dung thực hành chính của Hera

Theo tài liệu workshop, Hera không chỉ dừng ở mức giới thiệu kiến trúc mà còn hướng dẫn triển khai end-to-end một voice chatbot thật trên AWS account cá nhân. Phần thực hành được chia thành nhiều chặng để người học có thể đi từ nền tảng dữ liệu đến giao diện web hoàn chỉnh.

### 3.1 Knowledge Base

Người học xây dựng **Bedrock Knowledge Base** dùng **S3 Vectors** làm backend lưu vector và **Titan Text Embeddings v2** để tạo embedding. Mục tiêu của bước này là biến dữ liệu sản phẩm thành các đoạn thông tin có thể truy xuất khi người dùng hỏi qua giọng nói.

Điểm đáng chú ý là workshop chọn S3 Vectors để tối ưu chi phí cho catalog nhỏ. Thay vì triển khai OpenSearch Serverless, vốn phù hợp với hệ thống lớn hơn nhưng chi phí duy trì cao, S3 Vectors giúp bài thực hành phù hợp hơn với sinh viên và workshop ngắn.

### 3.2 Pipecat Local

Trước khi deploy lên AWS, người học chạy voice agent ở môi trường local. Pipecat đóng vai trò điều phối pipeline, nhận audio, gửi tới Nova Sonic, xử lý tool use và trả phản hồi. Việc chạy local trước giúp kiểm tra logic agent, cấu hình model và luồng RAG trước khi đưa lên managed runtime.

### 3.3 Deploy AgentCore

Sau khi kiểm thử local, container Pipecat được build multi-architecture và deploy lên **Amazon Bedrock AgentCore Runtime**. Đây là bước chuyển từ môi trường phát triển sang môi trường chạy thật, nơi agent có thể nhận kết nối từ browser thông qua WebSocket.

### 3.4 Web Widget

Workshop triển khai một widget web tĩnh gồm HTML, JavaScript và CSS. Widget này được serve qua **S3 + CloudFront**, ghi âm từ trình duyệt và gửi audio tới AgentCore Runtime. Vì trình duyệt không tự ký được WebSocket upgrade bằng SigV4, hệ thống cần **Presigner Lambda** để cấp một WSS URL có thời hạn ngắn.

### 3.5 Observability

Phần observability giúp theo dõi hệ thống sau khi triển khai. Workshop đề cập dashboard CloudWatch, log vận hành và alarm để phát hiện lỗi hoặc chi phí bất thường. Đây là phần quan trọng vì voice agent thời gian thực không chỉ cần chạy được, mà còn cần quan sát được khi có lỗi streaming, lỗi runtime hoặc lỗi truy xuất Knowledge Base.

---

## 8. Phân tích chi tiết voice loop

Một vòng hội thoại trong Hera có thể được hiểu theo luồng sau:

1. Người dùng bấm record trên widget và nói câu hỏi.
2. Browser ghi âm bằng AudioWorklet ở định dạng 16 kHz Int16 mono.
3. Browser gọi Presigner Lambda để xin WebSocket URL đã ký SigV4.
4. Presigner Lambda trả về WSS URL có thời hạn ngắn, khoảng 300 giây.
5. Browser kết nối tới AgentCore Runtime qua WebSocket.
6. AgentCore Runtime chạy container Pipecat và forward audio tới Amazon Nova 2 Sonic.
7. Nova Sonic xử lý audio theo dạng speech-to-speech.
8. Nếu câu hỏi cần tra cứu dữ liệu, Sonic phát sinh tool use.
9. Runtime gọi Bedrock Knowledge Base bằng `bedrock-agent-runtime.retrieve`.
10. Knowledge Base truy xuất top chunks từ S3 Vectors.
11. Runtime gửi kết quả truy xuất trở lại Nova Sonic trong cùng streaming session.
12. Nova Sonic sinh phản hồi audio 24 kHz, Runtime stream về browser và browser phát lại cho người dùng.

Qua luồng này có thể thấy Hera kết hợp nhiều lớp kỹ thuật: xử lý âm thanh ở frontend, xác thực kết nối bằng SigV4, compute managed cho agent, foundation model speech-to-speech, RAG retrieval và phát âm thanh thời gian thực. Đây là một ví dụ rất rõ về cách xây dựng ứng dụng AI hiện đại không chỉ bằng model, mà bằng toàn bộ hệ sinh thái cloud xung quanh model.

---

## 9. Chi phí, cleanup và vận hành

Một điểm em đánh giá cao trong workshop là phần chi phí và cleanup được nhấn mạnh ngay từ đầu. Tài liệu ước tính chi phí khoảng **2-5 USD** nếu thực hành trong thời lượng ngắn và dọn tài nguyên đúng cách. Tuy nhiên, nếu không cleanup, chi phí có thể tiếp tục phát sinh do AgentCore Runtime, Bedrock Knowledge Base, CloudFront request hoặc các tài nguyên liên quan.

### Vì sao cleanup quan trọng?

Trong các workshop cloud, người học thường tập trung vào deploy thành công nhưng dễ quên dọn tài nguyên. Với Hera, cleanup không chỉ là xóa thủ công vài service, mà còn cần xác minh rằng các tài nguyên tính phí đã thật sự được dừng hoặc xóa. Tài liệu có nhắc đến script kiểm tra cleanup để giảm rủi ro còn sót tài nguyên.

### Observability trong thực tế

Hera cũng nhấn mạnh rằng một voice agent production-ready cần khả năng quan sát. Các chỉ số cần quan tâm gồm:

* Trạng thái kết nối WebSocket.
* Lỗi runtime hoặc container.
* Thời gian phản hồi của một lượt hội thoại.
* Lỗi truy xuất Knowledge Base.
* Chi phí sử dụng Bedrock và AgentCore.
* Alarm khi chi phí vượt ngưỡng dự kiến.

Điều này giúp em hiểu rằng triển khai AI không chỉ là tạo demo chạy được. Một hệ thống AI thật cần monitoring, logging, cảnh báo và quy trình vận hành rõ ràng.

---

## 10. Khả năng mở rộng sau workshop

Từ phần tổng kết của tài liệu Hera, có thể thấy dự án còn nhiều hướng mở rộng:

### Kênh thoại qua Twilio

Thay vì chỉ nói chuyện qua browser, hệ thống có thể mở rộng sang cuộc gọi điện thoại bằng Twilio Media Streams. Khi đó cần xử lý thêm bài toán chuyển đổi audio, vì điện thoại thường dùng audio 8 kHz trong khi Sonic cần luồng phù hợp hơn cho voice agent.

### Chatbot đa ngôn ngữ

Workshop hiện ưu tiên tiếng Anh vì Nova Sonic hoạt động tốt nhất với tiếng Anh. Tuy vậy, hướng mở rộng tự nhiên là tự động nhận diện ngôn ngữ người dùng và phản hồi bằng tiếng Việt khi chất lượng model hỗ trợ tốt hơn.

### Multi-agent routing

Hera có thể phát triển thành hệ thống nhiều agent, trong đó một agent điều phối sẽ chuyển câu hỏi tới các agent chuyên biệt như sales, support hoặc billing. Cách tiếp cận này phù hợp với doanh nghiệp vì mỗi agent có thể phụ trách một miền tri thức riêng.

### Lưu lịch sử hội thoại

Phiên bản workshop chủ yếu tập trung vào voice loop hiện tại. Nếu muốn phục vụ người dùng quay lại nhiều lần, hệ thống có thể thêm DynamoDB để lưu session history, TTL để tự động hết hạn dữ liệu, và Cognito để xác định danh tính người dùng.

### Bảo mật và guardrails

Khi triển khai với dữ liệu thật, cần bổ sung guardrails để kiểm soát thông tin nhạy cảm, giới hạn hành vi của agent và tránh trả lời ngoài phạm vi. Đây là bước quan trọng để chuyển từ demo workshop sang sản phẩm có thể dùng trong môi trường thực tế.

---

> [!TIP]
> ### 💡 Bài học & Nhận thức chung (Synthesis)
> 
> Qua việc tìm hiểu và thực hành Workshop Hera, tôi đã rút ra được một số nhận thức công nghệ quan trọng:
> 
> 1. **Cuộc cách mạng của Trí tuệ nhân tạo giọng nói thời gian thực (Voice AI)**:
>    * Nhờ có **Amazon Nova 2 Sonic** với kiến trúc speech-to-speech cải tiến, việc giao tiếp hai chiều với AI không còn bị chia cắt thành các bước trung gian (STT -> LLM -> TTS) giúp tối ưu hóa độ trễ xuống dưới 1 giây, đem lại trải nghiệm đàm thoại tự nhiên gần như người thật.
> 2. **Tối ưu hóa thiết kế hạ tầng và chi phí (Serverless & RAG tối giản)**:
>    * Thay vì sử dụng OpenSearch Serverless tốn kém (200-400 USD/tháng), giải pháp tích hợp **S3 Vectors + Titan v2** chỉ tiêu tốn khoảng 0.10 USD/tháng mà vẫn đáp ứng tốt nghiệp vụ RAG.
>    * Sử dụng **Amazon Bedrock AgentCore Runtime** giúp đơn giản hóa việc quản lý vòng đời container của Pipecat mà không cần cấu hình phức tạp các thành phần VPC, ALB hay NAT Gateway, vừa tiết kiệm chi phí vận hành vừa đảm bảo tính bảo mật.
> 3. **Tầm quan trọng của sự đồng bộ trong Infrastructure as Code (IaC)**:
>    * Việc kết hợp song song giữa **Terraform** (cho Bedrock Knowledge Base) và **AWS CDK Python** (cho AgentCore Runtime) tạo nên một luồng triển khai liền mạch, dễ quản lý và dễ dọn dẹp tài nguyên (cleanup) sau khi kết thúc dự án.
