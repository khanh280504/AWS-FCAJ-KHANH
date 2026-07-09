---
title: "Event 4"
date: 2026-06-06
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

# BÀI THU HOẠCH: AWS STUDENT BUILDER GROUP - KIRO SPEC DRIVEN DEVELOPMENT

---

> [!IMPORTANT]
>
> ### 🎯 Tổng quan sự kiện & Mục tiêu
>
> Buổi chia sẻ **AWS Student Builder Group - Kiro Spec Driven Development** giới thiệu cách tiếp cận phát triển phần mềm dựa trên đặc tả, trong đó yêu cầu, thiết kế và kế hoạch triển khai được chuẩn hóa trước khi viết code. Nội dung tập trung vào việc sử dụng **Kiro**, một môi trường phát triển có hỗ trợ AI agent, để chuyển ý tưởng ban đầu thành tài liệu yêu cầu, thiết kế kỹ thuật và danh sách tác vụ rõ ràng.

## 1. Kiro và Spec Driven Development là gì?

### Thông tin tham dự sự kiện

* **Hình thức:** Online.
* **Nền tảng tham dự:** Google Meet.
* **Thời gian tham dự:** 20 giờ.

### Kiro

Kiro là một môi trường phát triển tích hợp AI, hỗ trợ lập trình viên biến yêu cầu tự nhiên thành các tài liệu có cấu trúc. Thay vì chỉ yêu cầu AI viết code ngay lập tức, Kiro khuyến khích quy trình làm rõ bài toán trước, sau đó mới triển khai.

### Spec Driven Development

Spec Driven Development là phương pháp phát triển phần mềm lấy **đặc tả** làm trung tâm. Đặc tả đóng vai trò như nguồn sự thật chính, giúp nhóm phát triển hiểu rõ:

* Hệ thống cần giải quyết vấn đề gì.
* Người dùng mong đợi hành vi nào.
* Điều kiện chấp nhận của từng chức năng là gì.
* Thiết kế kỹ thuật cần đi theo hướng nào.
* Các bước triển khai nên được chia nhỏ ra sao.

Điểm khác biệt lớn của cách tiếp cận này nằm ở việc không xem code là điểm bắt đầu duy nhất. Trong nhiều dự án, lập trình viên thường bắt tay vào viết chức năng ngay sau khi có ý tưởng sơ bộ. Cách làm đó có thể tạo cảm giác nhanh ở giai đoạn đầu, nhưng khi yêu cầu thay đổi hoặc dự án có thêm thành viên, nhóm rất dễ rơi vào tình trạng không ai hiểu đầy đủ lý do đằng sau các quyết định kỹ thuật. Spec Driven Development giải quyết vấn đề này bằng cách biến yêu cầu, thiết kế và kế hoạch triển khai thành các tài liệu có thể đọc, sửa và kiểm chứng.

Với sự hỗ trợ của AI, đặc tả còn đóng vai trò như ngữ cảnh chất lượng cao cho công cụ lập trình. Khi AI hiểu rõ mục tiêu, dữ liệu, luồng xử lý, ràng buộc và tiêu chí hoàn thành, kết quả sinh ra sẽ ít bị lan man hơn. Điều này đặc biệt quan trọng trong các dự án có nhiều logic nghiệp vụ, vì chỉ một yêu cầu mơ hồ cũng có thể dẫn đến thiết kế sai hoặc code khó bảo trì.

---

## 2. Vấn đề của "vibe coding" và lý do cần đặc tả

"Vibe coding" có thể hiểu là cách viết phần mềm dựa nhiều vào cảm hứng và prompt tự do: mô tả ý tưởng ngắn cho AI, nhận code, chạy thử, rồi tiếp tục sửa bằng các prompt tiếp theo. Cách làm này hữu ích khi thử nghiệm nhanh, nhưng có một số hạn chế rõ ràng:

* Yêu cầu ban đầu thường thiếu điều kiện biên và tình huống lỗi.
* AI có thể tự giả định kiến trúc, thư viện hoặc cách tổ chức code.
* Code sinh ra có thể chạy được nhưng không phản ánh đúng mục tiêu sản phẩm.
* Khi dự án lớn hơn, việc truy vết vì sao một chức năng được viết như vậy trở nên khó khăn.
* Tài liệu, test và code dễ bị lệch nhau.

Qua nội dung buổi chia sẻ, em hiểu rằng Kiro không phủ nhận vai trò của AI trong việc tăng tốc lập trình. Ngược lại, Kiro giúp sử dụng AI theo cách có kiểm soát hơn. Thay vì xem AI như công cụ "viết code hộ", người học nên xem AI như một cộng sự kỹ thuật có thể hỗ trợ phân tích yêu cầu, đề xuất thiết kế, chia nhỏ nhiệm vụ và kiểm tra sự nhất quán giữa các phần của dự án.

---

## 3. Quy trình phát triển theo đặc tả

### Bước 1: Xây dựng yêu cầu

Ở giai đoạn đầu, ý tưởng được chuyển thành các yêu cầu rõ ràng. Mỗi yêu cầu cần mô tả vai trò người dùng, mục tiêu sử dụng và điều kiện chấp nhận. Cách làm này giúp tránh tình trạng prompt quá chung chung khiến AI tự suy đoán sai ý định.

Một yêu cầu tốt không chỉ nói "tôi muốn có chức năng đăng nhập", mà cần chỉ rõ người dùng là ai, đăng nhập bằng phương thức nào, khi sai mật khẩu thì hệ thống phản hồi ra sao, khi tài khoản bị khóa thì xử lý như thế nào, và điều kiện nào chứng minh chức năng đã hoàn thành. Khi yêu cầu được viết rõ, cả con người lẫn AI đều có chung một điểm tham chiếu.

### Bước 2: Thiết kế giải pháp

Từ yêu cầu đã được làm rõ, hệ thống tiếp tục tạo hoặc hỗ trợ xây dựng tài liệu thiết kế. Phần thiết kế thường bao gồm kiến trúc tổng quan, luồng xử lý, dữ liệu cần dùng, thành phần giao diện và các điểm tích hợp.

Ở bước này, Kiro giúp chuyển câu hỏi "cần làm gì" thành "sẽ làm như thế nào". Thiết kế có thể mô tả các module chính, quan hệ giữa frontend và backend, API cần tạo, cấu trúc dữ liệu, trạng thái giao diện và các ràng buộc bảo mật. Nhờ có thiết kế trước, quá trình viết code ít bị chắp vá hơn.

### Bước 3: Chia nhỏ công việc

Sau khi có thiết kế, công việc được chia thành các nhiệm vụ nhỏ hơn. Mỗi nhiệm vụ có phạm vi cụ thể, giúp việc triển khai, kiểm thử và theo dõi tiến độ trở nên dễ kiểm soát hơn.

Việc chia nhỏ task cũng giúp người học tránh cảm giác bị ngợp khi làm một dự án lớn. Thay vì triển khai toàn bộ hệ thống cùng lúc, nhóm có thể đi từng phần: tạo cấu trúc dữ liệu, viết API, xây giao diện, thêm validation, viết test, rồi kiểm tra tích hợp. Mỗi bước đều có đầu ra cụ thể.

### Bước 4: Triển khai và kiểm chứng

Code được viết dựa trên yêu cầu và thiết kế đã thống nhất. Khi có thay đổi, lập trình viên cần quay lại cập nhật đặc tả để tránh việc tài liệu và code lệch nhau theo thời gian.

Kiểm chứng không chỉ là chạy thử xem ứng dụng có hoạt động không. Kiểm chứng còn bao gồm so sánh code với yêu cầu ban đầu, kiểm tra các điều kiện chấp nhận, xem xét trường hợp lỗi, và đảm bảo thay đổi mới không phá vỡ chức năng cũ. Đây là thói quen quan trọng để giảm nợ kỹ thuật.

---

## 4. Cấu trúc tài liệu trong quy trình Kiro

### Requirements

Tài liệu yêu cầu là nơi mô tả người dùng, mục tiêu, luồng sử dụng và điều kiện chấp nhận. Đây là phần quan trọng nhất vì nó quyết định hướng đi của toàn bộ dự án. Nếu requirements sai hoặc thiếu, thiết kế và code phía sau cũng dễ sai theo.

### Design

Tài liệu thiết kế giải thích giải pháp kỹ thuật ở mức cao hơn code. Nó giúp trả lời các câu hỏi như hệ thống gồm những thành phần nào, dữ liệu đi qua các bước nào, chức năng nào phụ thuộc vào chức năng nào, và cần lưu ý rủi ro gì khi triển khai.

### Tasks

Tài liệu tasks biến thiết kế thành danh sách công việc có thể thực hiện. Một task tốt nên đủ nhỏ để hoàn thành trong thời gian ngắn, có kết quả rõ ràng, và có thể kiểm tra được. Khi nhìn vào danh sách task, nhóm phát triển sẽ biết nên làm gì trước, làm gì sau.

### Sự liên kết giữa ba tài liệu

Điểm hay của quy trình này là ba tài liệu không tồn tại rời rạc. Requirements giải thích "vì sao" và "cần gì"; Design giải thích "làm bằng cách nào"; Tasks giải thích "thực hiện từng bước ra sao". Khi ba phần này thống nhất, dự án sẽ dễ hiểu hơn và việc dùng AI cũng hiệu quả hơn.

---

## 5. Giá trị thực tiễn của Kiro

### Giảm mơ hồ khi làm việc với AI

Một vấn đề phổ biến khi dùng AI để lập trình là người dùng đưa yêu cầu chưa đủ rõ, dẫn đến kết quả thiếu chính xác. Kiro giúp biến yêu cầu thành cấu trúc cụ thể hơn, từ đó AI có bối cảnh tốt hơn để hỗ trợ.

### Hỗ trợ tư duy sản phẩm

Spec Driven Development buộc người học không chỉ nghĩ đến code, mà còn nghĩ đến người dùng, hành vi hệ thống, lỗi có thể xảy ra và tiêu chí hoàn thành. Đây là tư duy quan trọng khi làm sản phẩm thật.

### Tăng khả năng kiểm thử

Khi yêu cầu có điều kiện chấp nhận rõ ràng, nhóm phát triển dễ viết test case và đánh giá xem chức năng đã đạt hay chưa. Điều này đặc biệt hữu ích trong các dự án có nhiều tính năng hoặc nhiều người cùng tham gia.

### Giảm rủi ro khi mở rộng dự án

Với dự án nhỏ, việc viết code ngay có thể nhanh. Nhưng khi dự án lớn dần, thiếu đặc tả sẽ khiến hệ thống khó bảo trì. Quy trình của Kiro giúp lưu lại quyết định kỹ thuật và chia nhỏ công việc, nhờ đó dễ mở rộng hơn.

### Cải thiện giao tiếp trong nhóm

Trong dự án nhóm, mỗi thành viên thường có cách hiểu khác nhau về cùng một yêu cầu. Khi có đặc tả rõ ràng, nhóm có thể thảo luận dựa trên tài liệu thay vì dựa trên trí nhớ hoặc cảm giác. Điều này giúp giảm tranh luận mơ hồ và tăng tính minh bạch.

### Phù hợp với môi trường học tập

Đối với sinh viên, Kiro giúp rèn luyện quy trình làm dự án gần với thực tế doanh nghiệp hơn. Người học không chỉ nộp code, mà còn có thể trình bày yêu cầu, thiết kế, kế hoạch triển khai và lý do lựa chọn giải pháp. Đây là điểm cộng lớn khi làm đồ án hoặc tham gia hackathon.

---

## 6. Ví dụ áp dụng vào dự án sinh viên

Nếu áp dụng Kiro vào một dự án quản lý sự kiện sinh viên, quy trình có thể diễn ra như sau:

1. **Yêu cầu:** Sinh viên có thể xem danh sách sự kiện, đăng ký tham gia, nhận thông báo và xem trạng thái đăng ký.
2. **Điều kiện chấp nhận:** Khi sự kiện hết chỗ, hệ thống không cho đăng ký thêm; khi đăng ký thành công, trạng thái chuyển thành "Đã đăng ký"; khi hủy đăng ký, số lượng chỗ trống được cập nhật.
3. **Thiết kế:** Hệ thống gồm giao diện danh sách sự kiện, trang chi tiết, API đăng ký, cơ sở dữ liệu lưu người dùng và sự kiện.
4. **Tasks:** Tạo model dữ liệu, xây API lấy sự kiện, xây API đăng ký, thiết kế giao diện, thêm validation, viết test cho các trường hợp hết chỗ và hủy đăng ký.

Qua ví dụ này có thể thấy đặc tả giúp biến một ý tưởng chung chung thành kế hoạch triển khai rõ ràng. AI có thể hỗ trợ từng bước, nhưng người phát triển vẫn cần kiểm tra tính hợp lý và điều chỉnh theo mục tiêu thực tế.

---

## 7. Rủi ro và lưu ý khi sử dụng Kiro

Kiro và Spec Driven Development mang lại nhiều lợi ích, nhưng không có nghĩa là có thể phụ thuộc hoàn toàn vào công cụ. Một số điểm cần lưu ý gồm:

* Đặc tả do AI tạo ra vẫn cần con người đọc lại và xác nhận.
* Nếu yêu cầu đầu vào sai, tài liệu sinh ra cũng có thể sai theo.
* Không nên tạo quá nhiều tài liệu hình thức nhưng không dùng trong quá trình triển khai.
* Cần cập nhật tài liệu khi code thay đổi để tránh spec-code drift.
* Với bài toán nhỏ, nên giữ quy trình vừa đủ, không làm quá nặng.

Điều quan trọng là dùng Kiro như một công cụ hỗ trợ tư duy kỹ thuật, không phải công cụ thay thế hoàn toàn trách nhiệm của lập trình viên.

---

## 8. Bài học rút ra

1. **AI không thay thế hoàn toàn tư duy phân tích của lập trình viên.** Muốn AI hỗ trợ tốt, người dùng cần cung cấp yêu cầu rõ ràng, có mục tiêu và ràng buộc cụ thể.
2. **Đặc tả tốt giúp code tốt hơn.** Khi yêu cầu, thiết kế và nhiệm vụ được viết rõ, quá trình triển khai sẽ ít sai lệch hơn.
3. **Không nên chỉ "vibe coding".** Việc để AI sinh code ngay từ ý tưởng mơ hồ có thể nhanh lúc đầu, nhưng dễ tạo nợ kỹ thuật về sau.
4. **Tài liệu không phải phần phụ.** Trong quy trình Spec Driven Development, tài liệu chính là công cụ điều phối giữa ý tưởng, thiết kế, code và kiểm thử.
5. **Kiro phù hợp cho sinh viên học cách làm dự án bài bản.** Công cụ này giúp người học rèn luyện cách chia nhỏ vấn đề, viết yêu cầu, suy nghĩ về kiến trúc và kiểm chứng kết quả.
6. **Cần duy trì sự nhất quán giữa tài liệu và code.** Khi một tính năng thay đổi, đặc tả cũng cần được cập nhật để người khác hiểu đúng trạng thái hiện tại của dự án.
7. **Kỹ năng đặt vấn đề vẫn rất quan trọng.** AI chỉ hỗ trợ tốt khi người dùng biết mô tả mục tiêu, ràng buộc và kết quả mong muốn.

---

> [!TIP]
>
> ### 💡 Nhận thức chung
>
> Qua buổi chia sẻ, em nhận thấy xu hướng phát triển phần mềm với AI đang chuyển từ việc "nhờ AI viết code" sang việc "dùng AI để hỗ trợ toàn bộ quy trình kỹ thuật". Kiro và Spec Driven Development cho thấy giá trị lớn nhất của AI không chỉ nằm ở tốc độ sinh code, mà còn ở khả năng hỗ trợ làm rõ yêu cầu, thiết kế giải pháp và kiểm soát quá trình triển khai một cách có hệ thống.
