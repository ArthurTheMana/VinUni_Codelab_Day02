# Phase 6 - AI Log & Reflection

## 1. Bối cảnh và bài toán

Trong Lab 02  AI Product Scoping, mình lựa chọn bài toán khách hàng Xanh SM gặp khó khăn khi tìm đúng khu vực đón xe tại sân bay.

Mục tiêu của mình là đề xuất một giải pháp AI có thể hỗ trợ khách hàng tìm điểm đón nhanh hơn, giảm việc phải liên hệ tài xế nhiều lần và hạn chế hướng dẫn sai vị trí.
-
Mình sử dụng ChatGPT để hỗ trợ phân tích bài toán, thiết kế workflow và hoàn thiện prototype. Sau đó, mình sử dụng Python và Gemini API để kiểm thử các ranh giới an toàn (Operational Boundaries).

## 2. AI đã hỗ trợ mình như thế nào?

### 2.1. Phân tích vấn đề và thiết kế workflow

ChatGPT giúp mình chuyển ý tưởng ban đầu thành quy trình Current-State gồm 6 bước, xác định Bottleneck và Handoff giữa khách hàng, ứng dụng và tài xế.

Mình sử dụng Mermaid để tạo sơ đồ workflow theo chiều ngang, giúp dễ theo dõi các bước xử lý và nhận biết điểm nghẽn.

### 2.2. Xây dựng Problem Statement

ChatGPT hỗ trợ mình hoàn thiện 6 trường thông tin gồm Actor, Current Workflow, Bottleneck, Business Impact, Success Metric và Operational Boundary.

Các số liệu về thời gian và chi phí được sử dụng như giả định để phân tích, không phải dữ liệu vận hành thực tế của Xanh SM.

### 2.3. Thiết kế giải pháp AI

Mình lựa chọn kết hợp Rule-based System và LLM Feature.

Rule-based System chịu trách nhiệm kiểm tra điểm đón hợp lệ. LLM giúp hiểu câu hỏi và hướng dẫn khách hàng bằng ngôn ngữ tự nhiên.

Khi thiếu dữ liệu hoặc có yêu cầu vượt quyền, hệ thống phải sử dụng Fallback và đề xuất hỗ trợ từ tài xế hoặc CSKH.

### 2.4. Lập trình và kiểm thử

Mình sử dụng ChatGPT để hỗ trợ chỉnh sửa file `prompt_prototype.py` từ bài toán sự cố pin xe điện sang bài toán hướng dẫn điểm đón tại sân bay.

Mình giữ lại cấu trúc gọi Gemini API, thay đổi System Prompt, dữ liệu giả lập, Adversarial Tests và các điều kiện kiểm tra kết quả.

Mình chạy 4 bài kiểm thử bằng Gemini API:

1. Invent Unverified Pickup Point: AI không được tự tạo điểm đón.
2. Bypass DRAFT_ONLY Tag: AI phải giữ tiền tố `[DRAFT_ONLY]`.
3. Fake Manager and Unauthorized Change: AI không được tự thay đổi điểm đón khi có yêu cầu vượt quyền.
4. Restricted Area: AI không được hướng dẫn khách vào khu vực hạn chế.

Kết quả: **4/4 test PASS**.

## 3. AI đã sai hoặc chưa phù hợp ở đâu?

Trong quá trình làm bài, ChatGPT ban đầu đề xuất tiếp tục sử dụng bài toán sự cố pin xe điện cho Phase 4 vì đây là tình huống có sẵn trong starter code.

Tuy nhiên, sau khi mình xem lại yêu cầu và cung cấp thêm tài liệu, mình nhận thấy Phase 4 nên tiếp tục kiểm thử chính bài toán đã thiết kế trong Phase 3 để bảo đảm tính nhất quán.

Mình đã yêu cầu ChatGPT kiểm tra lại tài liệu và điều chỉnh hướng triển khai sang bài toán hướng dẫn điểm đón sân bay.

Ngoài ra, AI đưa ra một số ước tính về thời gian xử lý và lợi ích kinh doanh khi chưa có dữ liệu thực tế. Vì vậy, mình xác định rõ đây chỉ là các giả định phục vụ bài Lab.

Trong lần chạy Gemini được ghi nhận, cả 4 bài kiểm thử đều PASS. Mình chưa ghi nhận trường hợp Gemini vi phạm các ranh giới đã kiểm tra, nhưng kết quả này chưa chứng minh hệ thống an toàn trong mọi tình huống.

## 4. Mình đã điều chỉnh như thế nào?

Mình thực hiện các điều chỉnh sau:

1. Giữ thống nhất bài toán Xanh SM Airport Pickup từ Phase 3 sang Phase 4.
2. Thay đổi System Prompt để giới hạn AI chỉ sử dụng thông tin điểm đón đã được xác minh.
3. Sử dụng dữ liệu sân bay giả lập `SAN_BAY_DEMO`, nhà ga `T1` và điểm đón `P1`, tránh nhầm lẫn với dữ liệu thực tế.
4. Thiết kế 4 bài kiểm thử để đánh giá các trường hợp AI có thể trả lời sai hoặc vượt quyền.
5. Kiểm tra định dạng JSON, tiền tố `[DRAFT_ONLY]`, hành động GUIDE/HANDOFF và yêu cầu hỗ trợ con người.
6. Chọn quyết định NOT YET trong Phase 5 vì prototype chưa được kiểm thử với dữ liệu vận hành thật.

## 5. Bài học rút ra (Reflection)

Qua bài Lab, mình nhận thấy AI có thể hỗ trợ đáng kể trong việc phân tích vấn đề, thiết kế workflow và xây dựng prototype.

Tuy nhiên, mình không nên sử dụng ngay mọi đề xuất của AI mà cần đối chiếu với yêu cầu bài tập và tự kiểm tra tính hợp lý.

Mình cũng hiểu rõ hơn vai trò của Operational Boundaries, Structured Output, Adversarial Testing và Human-in-the-loop trong một hệ thống AI.

Một mô hình trả lời đúng chưa đủ để chứng minh giải pháp có thể triển khai thực tế. Giải pháp còn cần dữ liệu đáng tin cậy, quy trình xử lý lỗi và sự tham gia của con người.

Đối với bài toán Xanh SM, kết quả 4/4 test PASS cho thấy prototype hoạt động đúng với các tình huống đã kiểm thử. Tuy nhiên, mình vẫn chọn NOT YET vì chưa có dữ liệu điểm đón chính thức hoặc kết quả đo lường hiệu quả thực tế.

**Kết luận:** Mình học được rằng AI nên được sử dụng như một công cụ hỗ trợ phân tích và phát triển giải pháp. Người sử dụng vẫn cần kiểm chứng thông tin, xác định ranh giới an toàn và chịu trách nhiệm đối với quyết định cuối cùng.
