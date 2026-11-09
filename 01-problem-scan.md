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
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Vinhomes | Repetitive, Time-consuming | Các nhân viên bảo hành các tòa vinhomes thường xuyên nhận được các phản ánh sửa chữa từ cư dân như: đèn hỏng, thang máy, đường nước,.... nhưng thông tin nhận được đôi lúc bị thiếu như tòa nhà, tầng, chi tiết hỏng hóc cần sửa chữa.|
| 2 | Vinpearl/VinWonders | AI-upgrade, Time-consuming | Khách khó tự ghép một lịch trình phù hợp khi có trẻ nhỏ, người lớn tuổi, thời gian hạn chế hoặc sở thích khác nhau. Một lịch trình chung có thể chứa hoạt động không phù hợp hoặc trùng giờ.|
| 3 | VinFast | Repetitive, Time-consuming, Stakeholder Pain | Khi đặt lịch dịch vụ, chủ xe thường mô tả hiện tượng bằng ngôn ngữ đời thường như “xe kêu lạ”, “sạc lâu hơn trước” hoặc “màn hình thỉnh thoảng bị đơ”. Mô tả ban đầu thiếu thông tin về thời điểm xuất hiện, tần suất, điều kiện vận hành và thông báo trên xe. Nhân viên phải hỏi lại nhiều lần; kỹ thuật viên có thể phải liên hệ lại nếu phiếu tiếp nhận chưa đầy đủ.|
| 4 | Vinmec | Repetitive, Time-consuming | Nhân viên tiếp nhận phải trả lời nhiều câu hỏi về giấy tờ, địa điểm và thủ tục khám.|
| 5 | Vinmec | Repetitive, Time-consuming, AI-upgrade | Trước buổi khám, người bệnh thường hỏi về giấy tờ cần mang, địa điểm tiếp nhận, thủ tục bảo hiểm và cách lấy hồ sơ khám cũ. Nhân viên phải trả lời nhiều câu hỏi tương tự nhưng vẫn cần điều chỉnh theo từng lịch hẹn |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #___                                     │
│                                                             │
│ Bài toán (1 câu): ________________________________________  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? ______________________________________ │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. ___ ──> 2. ___ ──> 3. ___ ──> 4. ___                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? ___ (⏱ ___ phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? _____________________ │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? ______________________ │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```
QUICK PROBLEM CARD #1

**Bài toán**: Phản ánh sửa chữa của cư dân thường thiếu thông tin hoặc chứa nhiều vấn đề cùng lúc, khiến nhân viên mất thời gian hỏi lại, phân loại và chuyển đến đúng bộ phận.

**Công ty thành viên**: Vinhomes

**Ai đang đau**: Nhân viên tiếp nhận yêu cầu bảo trì phải đọc, hỏi bổ sung và phân loại thủ công; cư dân phải cung cấp lại thông tin và chờ xử lý.
Workflow thủ công hiện tại (5 bước):
1. Nhận phản ánh từ cư dân.
2. Đọc và xác định thông tin còn thiếu.
3. Liên hệ cư dân để hỏi thêm vị trí, hiện tượng và thời điểm xảy ra.
4. Tách đầu việc, phân loại và chuyển bộ phận phụ trách.
5. Ghi phiếu tiếp nhận và phản hồi cư dân.

**Bước tốn thời gian/lỗi nhất**: 
Bước 2–4: Xác định thông tin thiếu, hỏi lại và phân loại; dễ bỏ sót vấn đề hoặc chuyển sai bộ phận.
Ước tính giả định: 8–12 phút/phản ánh, chưa tính thời gian chờ cư dân trả lời.

**AI có thể nhảy vào hỗ trợ ở bước**: 
Bước 2–4: Trích xuất tòa nhà, tầng, vị trí và hiện tượng; tách nhiều vấn đề; tạo câu hỏi bổ sung; đề xuất mức ưu tiên và bộ phận tiếp nhận theo quy tắc được cung cấp. Nhân viên duyệt trước khi chuyển yêu cầu.

**Đo thành công bằng**: Mục tiêu giảm thời gian thao tác từ 10 xuống ≤ 4 phút/phản ánh, phân loại đúng bộ phận ≥ 90% trên bộ 30 phản ánh giả lập có đáp án chuẩn, nhận diện đủ các trường hợp khẩn trong bộ kiểm thử và chuyển người phụ trách.
**Quick Architecture**:
[ ] No AI  [x] Rule  [x] LLM  [ ] Agent
LLM đọc hiểu phản ánh; Rule kiểm tra trường bắt buộc và áp dụng quy tắc ưu tiên/chuyển bộ phận. 


QUICK PROBLEM CARD #2

**Bài toán**: Khách đi theo gia đình khó xây dựng lịch trình vui chơi phù hợp với thời gian, sở thích và điều kiện tham gia của từng thành viên.

**Công ty thành viên**: Khác — Vinpearl/VinWonders

**Ai đang đau**: Khách gia đình có trẻ nhỏ hoặc người lớn tuổi phải tự đối chiếu nhiều thông tin; nhân viên tư vấn mất thời gian thiết kế lịch trình riêng cho từng nhóm.

**Workflow thủ công hiện tại (5 bước)**:
1. Hỏi số người, độ tuổi, chiều cao trẻ em, sở thích và thời gian tham quan.
2. Tra cứu danh sách hoạt động, giờ mở cửa và điều kiện tham gia.
3. Chọn các hoạt động phù hợp với nhóm khách.
4. Sắp xếp lịch trình, thời gian nghỉ và di chuyển.
5. Kiểm tra trùng giờ, điều chỉnh và gửi khách.

**Bước tốn thời gian/lỗi nhất**:
Bước 3–4: Đối chiếu nhiều điều kiện và sắp xếp lịch trình; dễ chọn hoạt động không phù hợp hoặc trùng giờ.
Ước tính giả định: 15–20 phút/lịch trình.

**AI có thể nhảy vào hỗ trợ ở bước**: 
Bước 2–5: Dựa trên bảng dữ liệu được cung cấp để đề xuất lịch trình, giải thích lựa chọn và đưa ra phương án thay thế. Hỏi bổ sung khi thiếu chiều cao, sở thích hoặc thời gian; không tự bịa giờ hoạt động hay thời gian xếp hàng.

**Đo thành công bằng**: Mục tiêu giảm thời gian lập và kiểm tra lịch trình từ 20 xuống ≤ 5 phút, 100% hoạt động được đề xuất đáp ứng điều kiện tuổi/chiều cao đã cung cấp, không có hoạt động trùng giờ trên bộ 20 tình huống gia đình giả lập, 100% thông tin hoạt động lấy từ dữ liệu đầu vào.

**Quick Architecture**:
[ ] No AI  [x] Rule  [x] LLM  [ ] Agent
Rule lọc điều kiện tham gia và kiểm tra trùng giờ; LLM đề xuất, trình bày lịch trình theo nhu cầu khách.

QUICK PROBLEM CARD #3

**Bài toán**: Chủ xe mô tả hiện tượng bất thường thiếu chi tiết, khiến nhân viên dịch vụ phải hỏi lại nhiều lần để tạo phiếu tiếp nhận đủ thông tin cho kỹ thuật viên.

**Công ty thành viên**: VinFast

**Ai đang đau**: Nhân viên tư vấn dịch vụ phải hỏi và nhập liệu thủ công; kỹ thuật viên nhận phiếu thiếu thông tin; chủ xe phải lặp lại mô tả vấn đề.

**Workflow thủ công hiện tại (5 bước)**:
1. Nhận mô tả hiện tượng từ chủ xe.
2. Xác định từng triệu chứng và thông tin còn thiếu.
3. Hỏi thêm mẫu xe, thời điểm, tần suất, điều kiện xảy ra và thông báo lỗi.
4. Tổng hợp thành phiếu tiếp nhận theo mẫu.
5. Kiểm tra với khách và chuyển kỹ thuật viên.

**Bước tốn thời gian/lỗi nhất**:
Bước 2–4: Hỏi bổ sung và ghi phiếu; dễ bỏ sót triệu chứng hoặc ghi suy đoán thành thông tin đã xác nhận.
Ước tính giả định: 10–15 phút/yêu cầu, chưa tính thời gian chờ khách trả lời.

**AI có thể nhảy vào hỗ trợ ở bước**: 
Bước 2–4: Tách triệu chứng, trích xuất dữ liệu đã có, tạo câu hỏi bổ sung và điền phiếu dự thảo. Phân biệt rõ lời khách cung cấp và thông tin chưa xác nhận; không tự chẩn đoán, báo giá hoặc kết luận bảo hành.

**Đo thành công bằng**: mục tiêu giảm thời gian tạo phiếu từ 15 xuống ≤ 6 phút/yêu cầu, ghi nhận ≥ 95% triệu chứng được nêu trên bộ 30 yêu cầu giả lập, 100% trường còn thiếu được đánh dấu “chưa có thông tin”, không có kết luận nguyên nhân hỏng hóc do AI tự suy diễn trong bộ kiểm thử.

**Quick Architecture**:
[ ] No AI  [x] Rule  [x] LLM  [ ] Agent
LLM đọc hiểu mô tả và soạn câu hỏi/phiếu; Rule kiểm tra các trường bắt buộc trước khi nhân viên duyệt.


