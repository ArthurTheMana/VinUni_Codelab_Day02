# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

## 🏛️ 1. Bối cảnh thực tế: Vin Smart Future (Vingroup)

**Vingroup** — Tập đoàn tư nhân lớn nhất Việt Nam — vừa sáp nhập toàn bộ các phòng ban công nghệ thuộc các công ty thành viên thành một đơn vị công nghệ thống nhất mang tên **Vin Smart Future**. 

Nhiệm vụ của **Vin Smart Future** là xây dựng các giải pháp AI, số hóa, và tự động hóa cốt lõi để nâng cao hiệu suất vận hành và trải nghiệm khách hàng xuyên suốt các công ty thành viên:
* 🚗 **VinFast:** Hệ thống xe điện thông minh (EV), trợ lý AI ảo trong xe, dự đoán bảo trì pin, và quản lý chuỗi cung ứng sản xuất.
* 🚕 **Xanh SM (GSM):** Vận hành đội xe taxi/xe máy điện thông minh, điều vận thông minh (Smart Dispatching), tối ưu hóa lộ trình di chuyển.
* 🏢 **Vinhomes:** Quản lý đô thị thông minh (Smart Cities), trợ lý cư dân thông minh, tối ưu hóa mức tiêu thụ năng lượng.
* 🏥 **Vinmec:** Y tế thông minh, chẩn đoán hình ảnh bằng AI, tối ưu hóa quản lý hồ sơ bệnh án.
* 🎢 **Vinpearl / VinWonders:** Trải nghiệm du lịch số hóa, quản lý phòng và luồng khách thông minh tại các khu vui chơi.

Trong buổi Lab hôm nay, nhóm của bạn sẽ đóng vai trò là **AI Product Engineer** tại **Vin Smart Future**, tiến hành tìm kiếm, scoping, phân tích độ khả thi, thiết lập ranh giới vận hành, và xây dựng một **bản mẫu kỹ thuật (prompt prototype)** cho một bài toán cụ thể thuộc một trong những mảng kinh doanh trên.

---

## 📊 2. Cơ cấu tính điểm bài lab

### 👥 Điểm nhóm (60 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **G1. Workflow Mapping** | 20 | Problem Deep-Dive | Vẽ chi tiết quy trình hiện tại: các bước, handoff, thời gian, bottleneck |
| **G2. Problem Statement** | 20 | Problem Deep-Dive | Problem Statement 6-field bám sát thực tế, metric có số và ranh giới rõ ràng |
| **G3. AI Fit & Future Flow** | 10 | Problem Deep-Dive | So sánh Rule vs LLM vs Agent, future flow có bước AI, ranh giới và Fallback |
| **G4. Decision Quality** | 10 | Problem Deep-Dive | Quyết định Go/Not Yet/No-Go trung thực và có chứng cứ rõ ràng |

### 👤 Điểm cá nhân (40 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **I1. Scan & Cards** | 15 | Quick Cards | Liệt kê 5 problems sử dụng 3 lenses, hoàn thiện 3 quick cards chất lượng |
| **I2. Prototyping** | 10 | 02-lab/ | Chạy thử nghiệm programmatic prompt prototype thành công |
| **I3. AI Log & Reflection** | 15 | 03-ai-log.md | Phản ánh trung thực về việc dùng AI làm thought-partner (giúp gì, sai gì, sửa gì) |

---

# 🚀 Phase 0 — worked Example: Xanh SM Intelligent Dispatcher (15 min)

*Giảng viên walk-through ví dụ thực tế từ Vin Smart Future để bạn hiểu rõ cách scoping một bài toán AI.*
Đọc chi tiết worked example tại file [02-deliverable-example.md](02-deliverable-example.md).

---

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
| 1 | Xanh SM | Pain từ người khác | Khách hàng đặt xe Xanh SM tại sân bay có thể gặp khó khăn khi xác định đúng khu vực đón khách (Pickup Point) do mỗi hãng taxi hoặc dịch vụ gọi xe có vị trí đón riêng. Điều này có thể gây nhầm lẫn, khiến khách phải đi tìm xe, liên hệ tài xế nhiều lần và kéo dài thời gian đón khách. |
| 2 | Xanh SM | Tốn thời gian | Một đội Xanh SM có nhiều xe chuẩn bị hoạt động vào giờ cao điểm buổi sáng. Một số xe còn 20–30% pin, một số xe đang sạc trong khi số lượng trụ sạc khả dụng có giới hạn. Người điều phối phải cân nhắc xe nào nên tiếp tục nhận khách, xe nào cần sạc trước và khi nào xe có thể quay lại hoạt động. |
| 3 | Xanh SM | Lặp lại | Sau mỗi chuyến, khách hàng có thể đánh giá tài xế bằng số sao và nhận xét. Nhân viên phải đọc nhiều phản hồi để phân loại vấn đề về thái độ phục vụ, vệ sinh xe hoặc trải nghiệm chuyến đi. |
| 4 | Vinhomes | AI có thể tốt hơn | Một cư dân mới muốn đăng ký thẻ xe, nhưng không rõ cần chuẩn bị giấy tờ nào hoặc thực hiện ở đâu. Trợ lý AI có thể hỏi tên khu đô thị và loại phương tiện, sau đó hướng dẫn quy trình dựa trên các quy định đang có hiệu lực. |
| 5 | Vinmec | Pain từ người khác | Một bệnh nhân muốn đặt lịch khám nhưng không biết nên chọn chuyên khoa nào. Người bệnh phải liên hệ nhân viên để được hướng dẫn hoặc có thể đặt lịch không phù hợp. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Khách hàng đặt Xanh SM tại sân bay có thể |
| mất thời gian tìm đúng khu vực đón xe do mỗi hãng taxi hoặc |
| dịch vụ gọi xe có điểm đón riêng.                           │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Hành khách đặt xe tại sân bay. Tài xế  |
|xanh SM cũng bị ảnh hưởng khi hai bên không tìm thấy nhau.   │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│     1. Khách đặt xe tại sân bay.                            |
| ──> 2. Khách tìm khu vực đón Xanh SM.                       |
| ──> 3. Liên hệ tài xế nếu không tìm được.                   |
| ──> 4. Gặp tài xế và lên xe.                                │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? 2-3 (⏱ 5-7 phút/lượt)     |
│ AI có thể nhảy vào hỗ trợ ở bước nào? Khách tìm khu vực đón |
| xe và liên hệ tài xế khi không xác định được vị trí.        │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Có thể giảm thời gian mỗi chuyến từ 2-3 phút => Còn 3-4   |
| phút. Có thể giảm thời gian tìm khu vực đón xe từ 5–7 phút  |
| xuống còn 2–3 phút/lượt, tiết kiệm khoảng 3–4 phút.         | 
| Giả sử có 500 chuyến/ngày, tổng thời gian tiết kiệm khoảng  |
| 25–33,3 giờ/ngày. Với chi phí giả định 60.000 VNĐ/giờ, giá  |
| trị thời gian tiết kiệm tương đương 1,5–2 triệu VNĐ/        |
| ngày.                                                       │
│                                                             │
│ Quick Architecture: [ ] No AI  [x] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Sau mỗi chuyến, khách hàng có thể đánh giá| 
| tài xế bằng số sao và nhận xét và nhân viên phải đọc nhiều  |
| phản hồi để phân loại vấn đề về thái độ phục vụ, vệ sinh xe |
| hoặc trải nghiệm chuyến đi.                                 │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên chăm sóc khách hàng và nhân  |
| viên quản lý chất lượng dịch vụ.                            │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│     1. Khách hàng gửi đánh giá sau chuyến đi.               |
| ──> 2. Nhân viên đọc và phân loại phản hồi.                 |
| ──> 3. Chuyển các vấn đề đến bộ phận liên quan.             |
| ──> 4.Tổng hợp kết quả và lập báo cáo.                      │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 (⏱ 5-6 phút/lượt)   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? AI đọc và phân loại   |
| phản hồi thành các nhóm như thái độ tài xế, vệ sinh xe, chất| 
| lượng chuyến đi và đề xuất mức độ ưu tiên. Nhân viên kiểm   |
| tra các trường hợp cần xử lý.                               │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Mục tiêu giảm thời gian phân loại từ 5-6 phút xuống 2     |
| phút/phản hồi (giảm 66,7%). Nếu xử lý 500 phản hồi/ngày, có |
| thể tiết kiệm khoảng 16,7 giờ công/ngày, tương đương 1 triệu |
| VNĐ/ngày theo giả định 60.000 VNĐ/giờ.                      │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Bác sĩ hoặc dược sĩ Vinmec phải kiểm tra  |
| danh sách thuốc, tiền sử dị ứng và các tương tác thuốc có   |
| thể xảy ra trước khi hoàn tất đơn thuốc, khiến quá trình tra| 
| cứu và đối chiếu thông tin có thể tốn nhiều thời gian.      |                                                 │ 
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Cư dân mới cần đăng ký thẻ xe và nhân  |
| viên chăm sóc cư dân thuộc ban quản lý Vinhomes.            │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│     1. Bác sĩ xem hồ sơ và danh sách thuốc của bệnh nhân.   |
| ──> 2. Kiểm tra dị ứng, tương tác và các cảnh báo về thuốc. |
| ──> 3. Tra cứu tài liệu chuyên môn khi cần.                 |
| ──> 4. Bác sĩ hoặc dược sĩ xác nhận đơn thuốc.              │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-3 (⏱ 5-6 phút/lượt) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? AI hỗ trợ đọc ghi chú |
| bệnh án, tổng hợp danh sách thuốc và giải thích các cảnh báo | 
| từ cơ sở dữ liệu thuốc đã được kiểm chứng, giúp bác sĩ hoặc  |
| dược sĩ kiểm tra nhanh hơn.                                 │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Mục tiêu thử nghiệm   |
| giảm ít nhất 30% thời gian rà soát hồ sơ thuốc so với quy   |
| trình hiện tại, đồng thời không bỏ sót cảnh báo quan trọng  |
| trong bộ tình huống kiểm thử được chuyên gia y tế xác nhận. |
| Cần đo thời gian và kiểm tra chất lượng thực tế trước khi   |
| đánh giá hiệu quả.                                          │
│                                                             │
│                                                             │
│ Quick Architecture: [ ] No AI  [x] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

Personally, mình sẽ chọn topic 1 của problem card bản thân. 

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.

## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Khách hàng đặt xe Xanh SM tại sân bay và tài xế hỗ trợ xác nhận vị trí đón khách. |
| **2. Current Workflow** | Khách đặt xe trên ứng dụng Xanh SM, xem thông tin điểm đón và tìm khu vực đón tại sân bay. Nếu không xác định được vị trí, khách phải gọi điện hoặc nhắn tin cho tài xế trước khi lên xe. |
| **3. Bottleneck** | Bước 3–4: Khách khó xác định đúng khu vực đón do các hãng taxi có vị trí riêng. Việc tìm đường và liên hệ tài xế có thể mất khoảng 5–7 phút/lượt (giả định). |
| **4. Business Impact** | Giả sử có 500 chuyến gặp vấn đề này mỗi ngày, việc giảm 3–4 phút/chuyến có thể tiết kiệm khoảng 25–33,3 giờ chờ/ngày. Quy đổi theo mức 60.000 VNĐ/giờ, giá trị thời gian tương đương khoảng 1,5–2 triệu VNĐ/ngày. Đây là số liệu giả định, không phải chi phí thực tế của Xanh SM. |
| **5. Success Metric** | Mục tiêu giảm thời gian tìm điểm đón từ 5–7 phút xuống còn 2–3 phút/lượt, đồng thời giảm số lần khách cần liên hệ tài xế để xác nhận vị trí. |
| **6. Operational Boundary** | AI chỉ được hướng dẫn dựa trên thông tin nhà ga, cửa ra và điểm đón đã được xác minh. AI không được tự tạo vị trí đón, hướng dẫn khách đến khu vực cấm hoặc tự thay đổi điểm đón. Nếu thiếu thông tin, hệ thống phải chuyển sang hỗ trợ của tài xế hoặc nhân viên. |


## 3.3. Future-State Flow & AI Fit (25 min)
- [x] Rule / State-Machine
- [x] LLM Feature
- [ ] Agentic Loop

**Giải thích:** Rule-based xác định điểm đón hợp lệ dựa trên dữ liệu chính thức của sân bay và Xanh SM. LLM hỗ trợ hiểu câu hỏi của khách hàng, hỏi thêm thông tin còn thiếu và hướng dẫn đường đi bằng ngôn ngữ dễ hiểu. Không cần Agentic Loop vì hệ thống không tự thực hiện hoặc thay đổi thao tác đặt xe.

* **Vẽ Future-State Flow:** Đánh dấu rõ:
  * 🔵 **AI Step:** Tác vụ LLM xử lý.
  * 🟢 **Human Step (HITL):** Bước con người phê duyệt/review (Human-in-the-loop).
  * ↩️ **Fallback:** Kế hoạch dự phòng khi LLM trả về kết quả lỗi hoặc không tự tin.

---

# 💻 Phase 4 — TECHNICAL PROMPT PROTOTYPE (Nhóm, 30 min)

Để đảm bảo kỹ sư của Vin Smart Future luôn giữ vững năng lực lập trình, nhóm của bạn sẽ tiến hành **lập trình bản mẫu prompt** trực tiếp trên **Gemini 2.5 Flash** bằng Python để stress-test hệ thống.

### Hướng dẫn thực hiện:
1. Mở file [starter-code/prompt_prototype.py](starter-code/prompt_prototype.py) bằng VS Code/Cursor.
2. Hoàn thiện các nội dung sau:
   * **System Prompt:** Viết chỉ thị cực kỳ nghiêm ngặt quy định vai trò, nhiệm vụ, định dạng output và **Operational Boundary (Ranh giới cấm)** của mô hình.
   * **Structured Output:** Định nghĩa định dạng JSON output rõ ràng.
   * **Adversarial Test Cases:** Viết ít nhất 3 prompts "tấn công" (Adversarial inputs) cố tình dụ AI vượt ranh giới hoặc đưa ra câu trả lời không được phép để kiểm tra xem ranh giới của bạn có thực sự vững chắc.
3. Chạy file python:
   ```bash
   python3 prompt_prototype.py
   ```
4. Kiểm tra xem các ranh giới an toàn có bị LLM phá vỡ hay không và ghi lại kết quả vào worksheet.

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [ ] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
2. [ ] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[ ] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> *Viết lý giải chi tiết tại đây*

---

# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân bạn về việc phối hợp với AI trong buổi học hôm nay vào file `03-ai-log.md`.*
