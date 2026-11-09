
# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:
| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **VinFast** | Lặp lại | Phân loại yêu cầu bảo hành và sửa chữa từ mô tả tự do của khách hàng có thể tạo ra khối lượng công việc lặp lại của bộ phận tiếp nhận dịch vụ. |
| 2 | **VinFast** | Lặp lại | Chương trình triệu hồi xe VF 8 tại Việt Nam với các yêu cầu tra cứu, giải đáp và hướng dẫn thủ tục có thể tương tự nhau nhiều. |
| 3 | **Vinpearl** | Tốn thời gian | Nhân viên đặt phòng phải trích xuất nhiều thông tin từ email yêu cầu đặt phòng theo đoàn, bao gồm thời gian lưu trú, số lượng khách, loại phòng và yêu cầu đặc biệt. Email không theo mẫu thống nhất có thể khiến việc nhập và kiểm tra thông tin mất thời gian. |
| 4 | **VinFast** | AI-upgrade | Khách hàng mô tả các triệu chứng bất thường của xe bằng ngôn ngữ tự nhiên, khiến nhân viên cần làm rõ thông tin trước khi chuyển yêu cầu cho kỹ thuật viên. Hệ thống AI có thể hỗ trợ nhận diện triệu chứng và chuẩn hóa thông tin tiếp nhận ban đầu. |
| 5 | **VinFast** | Pain từ người khác | Khiếu nại về sự cố xe, bảo hành hoặc trải nghiệm dịch vụ có mức độ ưu tiên khác nhau, phân loại không chính xác có thể gây trải nghiệm không tốt cho khách hàng và ảnh hưởng nhân viên xử lý. |


---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #_1__                                     │
│                                                             │
│ Bài toán (1 câu): Phân loại yêu cầu bảo hành, sửa chữa từ mô tả tự do của khách hàng có thể tăng khối lượng công việc lặp lại và nguy cơ chuyển giao yêu cầu không đúng bộ phận│
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên chăm sóc khách hàng và nhân viên bảo hành, sửa chữa │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Khách hàng gửi yêu cầu sửa chữa hoặc bảo hành
  ──> 2. Nhân viên tiếp nhận đọc mô tả sự cố và xác minh thông tin xe
  ──> 3. Nhân viên phân loại vấn đề (pin, thân vỏ,...) và xác định bộ phận tiếp nhận
  ──> 4. Yêu cầu được chuyển đến nhân viên tương quan kiểm tra và xử lý.                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2,3 đọc hiểu mô tả sự cố, hỏi lại thông tin còn thiếu và phân loại yêu cầu(⏱ 5-10 phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Sử dụng LLM tại bước 2,3 phân tích mô tả bằng ngôn ngữ tự nhiên, trích xuất triệu chứng, phân loại nhóm vấn đề và đề xuất bộ phận tiếp nhận. Nhân viên kiểm tra trước khi chuyển yêu cầu. │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?  │ 
 - Giảm thời gian phân loại trung bình từ giả định 5-10 phút xuống dưới 2 phút/yêu cầu
 - Đạt độ chính xác cao khi xác định và phân loại
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [x] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #_2__                                     │
│                                                             │
│ Bài toán (1 câu): Việc trích xuất thông tin đặt phòng theo đoàn từ email không theo mẫu thống nhất có thể khiến nhân viên Vinpearl mất nhiều thời gian nhập liệu và kiểm tra thông tin.│
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [x] Khác (Ghi rõ) Vinpearl  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên đặt phòng │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Khách hàng gửi email yêu cầu đặt phòng
  ──> 2. Nhân viên đọc email để xác định thời gian lưu trú, số lượng khách, số phòng, loại phòng, yêu cầu đặc biệt
  ──> 3. Nhân viên nhập dữ liệu vào hệ thống đặt phòng, kiểm tra thông tin còn thiếu
  ──> 4. Nhân viên tìm kiếm phòng phù hợp và gửi phản hồi xác nhận cho khách hàng.                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2,3,4 nhân viên mất thời gian đọc, nhập, tìm kiếm, kiểm tra thông tin và gửi phản hồi xác nhận cho khách hàng(⏱ 10 phút/email)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Sử dụng LLM để phân tích nội dung email, trích xuất các trường thông tin cần thiết, chuyển thành JSON. Hệ thống kiểm tra dữ liệu, đối chiếu, hiển thị thông tin xác nhân. Nhân viên xác nhận đặt phòng, hệ thống gửi emal xác nhận thành công
│                                                             │
│ Đo thành công bằng gì (Metric có số)?  │ 
 - Giảm thời gian xử lý 1 email xuống dưới 3 phút/yêu cầu
 - Trích xuất đầy đủ các trường thông tin có trong email đặt phòng, nếu không có đánh dấu thiếu, không được tự suy đoán
│                                                             │
│ Quick Architecture: [ ] No AI  [x] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```
```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #_3__                                     │
│                                                             │
│ Bài toán (1 câu): Phân loại các khiếu nại liên quan đến sự cố xe, bảo hành và trải nghiệm dịch vụ có mức độ khẩn cấp khác nhau.│
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)  │
│                                                             │
│ Ai đang đau (Actor)? Khách hàng, nhân viên chăm sóc khách hàng, bộ phận xử lý khiếu nại │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Khách hàng gửi khiếu nại qua các kênh thông hỗ trợ
  ──> 2. Nhân viên tiếp nhận và xác định vấn đề
  ──> 3. Nhân viên đánh giá mức độ khẩn cấp, mức độ ảnh hưởng của sự cố
  ──> 4. Nhân viên chuyển đến bộ phận phụ trách để giải quyết theo ưu tiên mức độ.
   ──> 5. Nhân viên theo dõi trạng thái xử lý và phản hồi khách hàng.                 │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 và 3 phân tích nội dung khiếu nại và đánh giá mức độ ưu tiên. Thời gian giả định: (⏱ 5 phút/yêu cầu)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Sử dụng LLM để phân loại nội dung khiếu nại, phát hiện từ ngữ hoặc triệu chứng liên quan đến an toàn và đề xuất mức độ ưu tiên. Các quy tắc an toàn được kiểm tra độc lập, nhân viên xác nhận trước khi chuyển yêu cầu.
│                                                             │
│ Đo thành công bằng gì (Metric có số)?  │ 
 - Giảm thời gian xử lý 1 email xuống dưới 3 phút/yêu cầu
 - Kiểm tra đạt độ chính xác cao trên bộ dữ liệu kiểm thử có nhãn mức độ ưu tiên
 - Đánh giá chính xác cao với các trường hợp nhóm khiếu nại có độ ưu tiên cao như rủi ro an toàn, sự cố nguy hiểm
│                                                             │
│ Quick Architecture: [ ] No AI  [x] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```
> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

---