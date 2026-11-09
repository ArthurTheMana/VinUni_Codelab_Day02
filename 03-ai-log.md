# 03 — AI Interaction Log

## 1. Mục đích sử dụng AI

Trong quá trình thực hiện bài tập AI Product Scoping, tôi sử dụng ChatGPT như một trợ lý để hỗ trợ phân tích bài toán kinh doanh, đánh giá khả năng ứng dụng AI và hoàn thiện các nội dung trong worksheet.

Mục tiêu không phải là để AI tự lựa chọn và quyết định toàn bộ dự án, mà là sử dụng AI để:
- Mở rộng góc nhìn khi tìm kiếm các bài toán thực tế tại những công ty thành viên Vingroup.
- Phân tích quy trình vận hành hiện tại và xác định bottleneck.
- Xây dựng Problem Statement theo mô hình 6-field.
- Đề xuất giải pháp AI phù hợp giữa Rule / State-Machine, LLM Feature và Agentic Loop.
- Xây dựng Future-State Workflow, Human-in-the-loop và Fallback.
- Xác định các chỉ số đo lường hiệu quả và hoàn thiện nội dung báo cáo.

## 2. Quá trình tương tác với AI

### 2.1. Giai đoạn tìm kiếm và đánh giá vấn đề (Phase 1 – SCAN & Phase 2 – QUICK-ASSESS)

**Yêu cầu đặt ra cho AI:**

Tôi cung cấp bối cảnh bài tập và yêu cầu ChatGPT hỗ trợ tìm kiếm, phân tích các vấn đề thực tế trong hoạt động của những công ty thành viên Vingroup. Một số hướng bài toán được xem xét bao gồm:
- VinFast: Phân loại và xử lý lỗi phương tiện.
- VinFast: Tối ưu lịch sửa chữa và bảo dưỡng.
- Vinmec: Chatbot hỗ trợ khách hàng.
- Xanh SM: Hỗ trợ hành khách tìm khu vực đón xe tại sân bay.

**AI đã hỗ trợ:**
- Đề xuất và cấu trúc hóa các bài toán theo Actor, Current Workflow, Bottleneck và AI Solution.
- Phân tích đối tượng sử dụng và tác động vận hành của từng vấn đề.
- Đề xuất các chỉ số để đánh giá tiềm năng ứng dụng AI.
- Giúp chuyển những ý tưởng ban đầu thành các Quick Problem Cards có cấu trúc rõ ràng.

**Kết quả:** Tôi có thể so sánh nhiều bài toán khác nhau thay vì lựa chọn một ý tưởng chỉ dựa trên mức độ hấp dẫn của công nghệ AI.

### 2.2. Giai đoạn phân tích sâu bài toán (Phase 3 – DEEP-DIVE)

Sau khi xem xét các ý tưởng, tôi tập trung vào bài toán **Xanh SM Airport Pick-up Assistant**.

**Yêu cầu đặt ra cho AI:**

Tôi cung cấp Quick Problem Card với thông tin về hành khách, tài xế, quy trình đặt xe, khó khăn khi tìm khu vực đón và thời gian bị lãng phí. Sau đó, tôi yêu cầu ChatGPT hoàn thiện Phase 3 theo đúng cấu trúc worksheet.

**AI đã hỗ trợ:**

1. **Current-State Workflow:** Mô tả quy trình từ lúc hành khách đặt xe đến khi gặp tài xế, xác định bước tìm điểm đón và liên hệ tài xế là bottleneck.
2. **Problem Statement:** Chuyển thông tin ban đầu thành sáu trường Actor, Current Workflow, Bottleneck, Business Impact, Success Metric và Operational Boundary.
3. **Future-State Workflow:** Đề xuất sử dụng Rule Engine để tra cứu điểm đón chính thức và LLM để hiểu câu hỏi, giải thích hướng dẫn cho hành khách.
4. **AI Fit:** Phân tích lý do nên kết hợp Rule / State-Machine và LLM Feature thay vì triển khai Agentic Loop ngay từ MVP.
5. **HITL và Fallback:** Đề xuất cơ chế để hành khách xác nhận điểm đón, đồng thời cung cấp phương án liên hệ tài xế hoặc nhân viên hỗ trợ khi AI không đủ thông tin.

**Kết quả:** Ý tưởng ban đầu được chuyển thành một giải pháp có quy trình triển khai cụ thể, có giới hạn vận hành và có thể xây dựng prototype để kiểm chứng.

### 2.3. Giai đoạn xác định Metrics và Operational Boundaries

Tôi tiếp tục yêu cầu AI làm rõ các chỉ số đánh giá hiệu quả, đặc biệt là bốn nhóm:

- **Feasibility:** Khả năng có dữ liệu điểm đón chính xác và đầy đủ.
- **Financial Impact:** Giá trị thời gian tiết kiệm và khả năng giảm chi phí hỗ trợ.
- **Operational Efficiency:** Tỷ lệ hành khách tìm đúng điểm đón và số cuộc gọi cần thiết.
- **Time Reduction:** Thời gian tìm điểm đón trước và sau khi có AI.

AI cũng giúp xây dựng ranh giới vận hành: hệ thống chỉ được hướng dẫn dựa trên dữ liệu điểm đón đã xác minh, không được tự tạo tọa độ, tự ý thay đổi điểm đón hoặc hủy chuyến.

## 3. AI trả lời sai hoặc có nguy cơ Hallucination ở đâu?

Trong quá trình sử dụng, tôi nhận thấy một số nội dung do AI đề xuất cần được kiểm tra và điều chỉnh trước khi đưa vào báo cáo.

### 3.1. Tự giả định thời gian của từng bước trong workflow

Khi xây dựng Current-State Workflow, AI đề xuất thời gian riêng cho từng bước, ví dụ:
- Đặt xe: 1–2 phút.
- Tìm khu vực đón: 5–7 phút.
- Liên hệ tài xế: 2–3 phút.
- Gặp tài xế và lên xe: 1–2 phút.

Tuy nhiên, thông tin ban đầu chỉ xác định khoảng 5–7 phút cho việc tìm khu vực đón và liên hệ tài xế, không cung cấp số liệu đo lường riêng cho từng bước.

**Cách xử lý:**
- Giữ 5–7 phút là dữ liệu đầu vào của bài toán.
- Đánh dấu thời gian của các bước còn lại là giả định phục vụ mô hình hóa.
- Ghi rõ cần khảo sát thực tế để xác nhận.
- Không sử dụng các giả định này như số liệu vận hành chính thức của Xanh SM.

### 3.2. Metric ban đầu có sự mâu thuẫn

Trong thông tin đầu vào có câu diễn đạt giảm thời gian từ 2–3 phút xuống còn 3–4 phút. Đây là cách diễn đạt không hợp lý vì thời gian sau cải thiện lại lớn hơn thời gian ban đầu.

**Cách xử lý:**

Tôi yêu cầu AI đối chiếu lại các số liệu và thống nhất cách diễn đạt:

- Thời gian ban đầu: 5–7 phút.
- Thời gian mục tiêu: 2–3 phút.
- Thời gian tiết kiệm: 3–4 phút/lượt.
- Tỷ lệ giảm thời gian: khoảng 57–71%.

Điều này giúp các chỉ số trong Problem Statement và Business Impact nhất quán với nhau.

### 3.3. Giả định về lợi ích tài chính

AI sử dụng giả định 500 chuyến/ngày và giá trị thời gian 60.000 VNĐ/giờ để tính toán lợi ích:

- Thời gian tiết kiệm: 25–33,3 giờ/ngày.
- Giá trị thời gian tương đương: 1,5–2 triệu VNĐ/ngày.

Tuy nhiên, đây là giá trị quy đổi từ thời gian tiết kiệm, không đồng nghĩa với doanh thu tăng thêm hoặc lợi nhuận thực tế.

**Cách xử lý:**
- Ghi rõ các giả định được sử dụng trong phép tính.
- Phân biệt giá trị thời gian tiết kiệm với lợi ích tài chính thực tế.
- Bổ sung rằng cần tính thêm chi phí phát triển, bản đồ, API và vận hành trước khi kết luận ROI.

### 3.4. Nguy cơ AI đưa ra thông tin điểm đón không chính xác

Đối với bài toán sân bay, AI có thể tạo ra hướng dẫn nghe hợp lý nhưng không phản ánh đúng vị trí đón thực tế. Điều này đặc biệt quan trọng vì hành khách có thể dựa vào hướng dẫn để di chuyển trong sân bay.

**Cách xử lý:**
- Không cho phép LLM tự suy đoán tọa độ hoặc điểm đón.
- Sử dụng Rule Engine và database chứa thông tin điểm đón đã xác minh.
- Chỉ cho phép LLM diễn giải và giải thích thông tin từ nguồn dữ liệu đáng tin cậy.
- Nếu thiếu dữ liệu hoặc không đủ độ tin cậy, chuyển sang Fallback thay vì tiếp tục đưa ra câu trả lời phỏng đoán.

## 4. Cách tôi cải thiện Prompt và giới hạn AI

Sau những lần tương tác, tôi nhận thấy việc cung cấp yêu cầu cụ thể và ranh giới rõ ràng giúp kết quả tốt hơn.

Một số nguyên tắc tôi áp dụng:

| Vấn đề | Cách điều chỉnh yêu cầu |
|---|---|
| AI đưa ra câu trả lời quá chung chung | Cung cấp bối cảnh doanh nghiệp, Actor và quy trình thực tế. |
| AI tự thêm số liệu | Yêu cầu phân biệt dữ liệu đầu vào, giả định và mục tiêu đề xuất. |
| Nội dung không đúng cấu trúc worksheet | Cung cấp chính xác các mục Phase 3 cần hoàn thiện. |
| Metric thiếu nhất quán | Yêu cầu kiểm tra lại công thức và đối chiếu giữa các chỉ số. |
| AI đề xuất giải pháp quá phức tạp | Yêu cầu so sánh Rule, LLM và Agentic Loop, ưu tiên giải pháp tối thiểu phù hợp MVP. |
| AI có thể tạo thông tin điểm đón không chính xác | Giới hạn LLM sử dụng dữ liệu điểm đón đã xác minh và bổ sung Fallback. |

**Ví dụ về cách đặt yêu cầu hiệu quả hơn:**

Thay vì chỉ yêu cầu:

> Hãy đề xuất giải pháp AI cho Xanh SM tại sân bay.

Tôi cung cấp yêu cầu cụ thể hơn:

> Dựa trên Quick Problem Card của Xanh SM Airport Pick-up Assistant, hãy hoàn thiện Phase 3 theo cấu trúc worksheet. Phân biệt rõ dữ liệu đầu vào và giả định. Đề xuất AI Fit giữa Rule / State-Machine, LLM Feature và Agentic Loop. Ưu tiên MVP đơn giản, sử dụng dữ liệu điểm đón đã xác minh. Không cho phép AI tự tạo tọa độ hoặc thay đổi điểm đón. Bổ sung Human-in-the-loop và Fallback khi thiếu dữ liệu hoặc kết quả không đủ tin cậy.

## 5. Đánh giá vai trò của AI trong quá trình thực hiện

| Tiêu chí | Đánh giá |
|---|---|
| Tìm kiếm và mở rộng ý tưởng | Tốt – giúp mở rộng góc nhìn và cấu trúc hóa các vấn đề. |
| Phân tích quy trình | Tốt – hỗ trợ xác định Actor, Handoff và Bottleneck. |
| Đề xuất giải pháp AI | Tốt – giúp so sánh Rule, LLM và Agentic Loop. |
| Tính chính xác của số liệu | Cần kiểm chứng – AI có thể tự đưa ra giả định hoặc diễn giải chưa nhất quán. |
| Đánh giá tác động kinh doanh | Cần dữ liệu thực tế – các phép tính chỉ có ý nghĩa khi giả định được xác nhận. |
| Operational Boundaries | Tốt – hỗ trợ xác định giới hạn và phương án dự phòng cho AI. |

## 6. Bài học rút ra

Qua quá trình sử dụng AI, tôi rút ra một số bài học:

1. **AI là công cụ hỗ trợ tư duy, không phải nguồn dữ liệu thực tế:** Các số liệu và thông tin do AI đề xuất cần được đối chiếu với dữ liệu đầu vào hoặc nguồn đáng tin cậy.
2. **Chất lượng đầu ra phụ thuộc nhiều vào chất lượng prompt:** Một yêu cầu có bối cảnh, cấu trúc và ràng buộc rõ ràng sẽ tạo ra kết quả hữu ích hơn.
3. **Không phải bài toán nào cũng cần Agentic AI:** Với bài toán Xanh SM Airport Pick-up Assistant, Rule Engine kết hợp LLM Feature đã đủ phù hợp cho MVP.
4. **Operational Boundary quan trọng không kém khả năng của AI:** Hệ thống cần biết khi nào không nên trả lời và khi nào phải chuyển cho con người.
5. **Hiệu quả AI phải được đo lường bằng KPI:** Một giải pháp chỉ thực sự có giá trị khi giúp giảm thời gian, chi phí hoặc cải thiện hiệu quả vận hành.

**Kết luận:**

ChatGPT đã giúp tôi rút ngắn thời gian cấu trúc hóa ý tưởng, phân tích quy trình và xây dựng giải pháp AI cho bài toán Xanh SM Airport Pick-up Assistant. Tuy nhiên, tôi vẫn cần chủ động kiểm tra số liệu, xác nhận các giả định và quyết định ranh giới vận hành. Qua đó, tôi hiểu rằng việc xây dựng một sản phẩm AI thực tế không chỉ là lựa chọn mô hình phù hợp, mà còn phải bắt đầu từ một vấn đề kinh doanh rõ ràng, dữ liệu đáng tin cậy và cơ chế kiểm soát rủi ro phù hợp.