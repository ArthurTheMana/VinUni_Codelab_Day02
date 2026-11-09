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
| 1 | Phân loại và xử lý lỗi trên phương tiện (VinFast) | Repetitive | Phương tiện cần sửa chữa được đưa về nhà xưởng cần phân loại lỗi. Bình thường người làm, giờ dùng AI để phân loại lỗi. Nếu dễ thì hướng dẫn Customer Support sửa, nếu tệ hơn thì đưa cho engineer. |
| 2 | Lập lịch sửa chữa phương tiện (VinFast) | AI-upgrade, Stakeholder pain | Lập lịch cho người sửa chữa phương tiện. |
| 3 | Giám sát quản lý chất lượng (QC) (VinFast) | Time-consuming/Repetitive | Quản lý chất lượng cho dây chuyền sản xuất xe |
| 4 | Chatbot hỗ trợ cs team (VinMec) | time-consuming/repetitive | Chatbot hỗ trợ xử lý phản hồi/yêu cầu support của nhân viên/khách hàng ở bệnh viện |
| 5 | Chatbot hỗ trợ cư dân (Vinhomes) | time-consuming/AI-upgrade | Chatbot hỗ trợ xử lý phản hồi/yêu cầu của cư dân |

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

**Bài toán:** Sử dụng AI để tự động phân loại lỗi phương tiện khi xe được đưa về nhà xưởng, đánh giá mức độ nghiêm trọng và đề xuất hướng xử lý: Customer Support hướng dẫn xử lý các lỗi đơn giản hoặc chuyển Engineer kiểm tra các lỗi phức tạp.

**Công ty thành viên:** VinFast

**Pain Point:** Nhân viên tiếp nhận phương tiện (Service Advisor), Customer Support, Kỹ sư kỹ thuật (Engineer), Quản lý nhà xưởng (Workshop Manager).

**Workflow:** Tiếp nhận phương tiện được đưa về nhà xưởng. -> Nhân viên kiểm tra tình trạng xe, đọc mô tả lỗi và ghi nhận mã lỗi. -> Nhân viên phân tích nguyên nhân và phân loại mức độ nghiêm trọng. -> Phân công xử lý: Customer Support hướng dẫn các lỗi đơn giản hoặc Engineer kiểm tra lỗi phức tạp. -> Nhân viên cập nhật kết quả xử lý vào hệ thống.

**Bước nào tốn thời gian/lỗi nhất** Bước 3 - Phân tích và phân loại lỗi. Nhân viên phải đọc mô tả, tra cứu mã lỗi và tham khảo các trường hợp tương tự.

**AI có thể nhảy vào hỗ trợ ở bước nào?**
- Phân tích mô tả lỗi và Diagnostic Trouble Codes (DTC).
- Phân loại lỗi theo hệ thống: Battery, Motor, Electrical, Software, Mechanical...
- Đánh giá mức độ ưu tiên.
- Đề xuất Customer Support hoặc Engineer tiếp nhận.
- Trích dẫn tài liệu kỹ thuật làm căn cứ cho đề xuất.

**Đo thành công bằng gì (Metrics)?**
<!-- - Classification Accuracy ≥ 90%. -->
- Giảm thời gian phân loại từ 10–15 phút xuống dưới 2 phút/xe.
- ≥ 90% lỗi được chuyển đúng nhóm phụ trách.
- 100% trường hợp có dấu hiệu ảnh hưởng đến an toàn được chuyển Engineer review.

**Quick architecture:** LLM,Rule, Human-in-the-loop

<!-- > [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."* -->

QUICK PROBLEM CARD #2

**Bài toán:** Sử dụng AI để hỗ trợ tự động lập lịch sửa chữa phương tiện tại nhà xưởng VinFast, tối ưu việc phân công kỹ thuật viên và thời gian sửa chữa dựa trên loại lỗi, mức độ ưu tiên, chuyên môn kỹ thuật viên và tình trạng sử dụng nhà xưởng.

**Công ty thành viên:** VinFast

**Pain Point:** Quản lý nhà xưởng (Workshop Manager), nhân viên tiếp nhận phương tiện (Service Advisor), kỹ thuật viên (Technician), khách hàng.

**Workflow:** Tiếp nhận yêu cầu sửa chữa và thông tin phương tiện. -> Nhân viên kiểm tra lỗi, xác định loại công việc và mức độ ưu tiên. -> Quản lý nhà xưởng kiểm tra lịch làm việc, chuyên môn của kỹ thuật viên và số lượng khu vực sửa chữa còn trống. -> Phân công kỹ thuật viên, vị trí và thời gian sửa chữa. -> Cập nhật lịch khi có thay đổi hoặc phát sinh công việc mới.

**Bước nào tốn thời gian/lỗi nhất** Bước 3 và 4 - Kiểm tra nguồn lực và lập lịch phân công. Quản lý nhà xưởng phải đối chiếu lịch làm việc, chuyên môn kỹ thuật viên, thời gian dự kiến sửa chữa và công suất nhà xưởng để tránh trùng lịch hoặc phân công không phù hợp.

**AI có thể nhảy vào hỗ trợ ở bước nào?**
- Phân tích thông tin yêu cầu sửa chữa để xác định loại công việc và chuyên môn cần thiết.
- Ước lượng thời gian sửa chữa dựa trên loại lỗi và dữ liệu các trường hợp trước đó.
- Đề xuất kỹ thuật viên phù hợp dựa trên chuyên môn và lịch làm việc.
- Đề xuất khung giờ và khu vực sửa chữa phù hợp với công suất nhà xưởng.
- Đề xuất điều chỉnh lịch khi có công việc khẩn cấp hoặc phát sinh thay đổi.

**Đo thành công bằng gì (Metrics)?**
- Giảm thời gian lập lịch từ 10–20 phút xuống dưới 3 phút/yêu cầu.
- Giảm ít nhất 30% số trường hợp trùng lịch hoặc phân công không phù hợp.
- Giảm 20% thời gian chờ trung bình của phương tiện trước khi được sửa chữa.
- ≥ 90% đề xuất lịch đáp ứng các ràng buộc về chuyên môn kỹ thuật viên và thời gian làm việc.

**Quick architecture:** Rule, Optimization, LLM, Human-in-the-loop.

QUICK PROBLEM CARD #3

**Bài toán:** Sử dụng AI để hỗ trợ nhân viên Vinmec tiếp nhận, phân loại và xử lý các yêu cầu hỗ trợ hoặc phản hồi từ khách hàng, bệnh nhân và nhân viên nội bộ. Chatbot có thể tra cứu thông tin từ tài liệu chính thức, đề xuất câu trả lời cho các yêu cầu phổ biến và chuyển tiếp những trường hợp phức tạp đến bộ phận phụ trách.

**Công ty thành viên:** Vinmec

**Pain Point:** Nhân viên Chăm sóc khách hàng (Customer Service), nhân viên Lễ tân (Receptionist), nhân viên hỗ trợ bệnh nhân và các bộ phận phụ trách như Kế toán, Bảo hiểm, Hành chính.

**Workflow:** Tiếp nhận yêu cầu hoặc phản hồi từ khách hàng, bệnh nhân hoặc nhân viên nội bộ qua hotline, email, website hoặc trực tiếp. -> Nhân viên đọc và xác định nội dung yêu cầu. -> Phân loại yêu cầu và xác định bộ phận phụ trách. -> Tra cứu thông tin từ tài liệu, quy trình hoặc liên hệ bộ phận liên quan để tìm câu trả lời. -> Phản hồi người gửi hoặc chuyển tiếp yêu cầu đến bộ phận chuyên môn. -> Cập nhật trạng thái xử lý.

**Bước nào tốn thời gian/lỗi nhất** Bước 2, 3 và 4 - Phân loại yêu cầu và tra cứu thông tin. Nhân viên phải đọc từng yêu cầu, xác định đúng nhóm vấn đề, tìm kiếm thông tin trong nhiều tài liệu hoặc liên hệ các bộ phận khác nhau. Điều này có thể dẫn đến phản hồi chậm hoặc chuyển nhầm bộ phận.

**AI có thể nhảy vào hỗ trợ ở bước nào?**
- Phân tích nội dung yêu cầu và tự động phân loại theo nhóm: Appointment, Billing, Insurance, Facilities, Administrative...
- Tra cứu thông tin từ cơ sở tri thức chứa tài liệu, quy trình và chính sách chính thức của Vinmec (RAG).
- Đề xuất câu trả lời dựa trên nguồn thông tin đã tra cứu.
- Tự động đề xuất bộ phận tiếp nhận phù hợp.
- Phát hiện các yêu cầu phức tạp hoặc liên quan đến chuyên môn y tế để chuyển nhân viên có chuyên môn xử lý.
- Hỗ trợ nhân viên theo dõi trạng thái và tổng hợp các yêu cầu chưa được giải quyết.

**Đo thành công bằng gì (Metrics)?**
- ≥ 90% yêu cầu được phân loại chính xác.
- Giảm thời gian tra cứu và soạn phản hồi từ 5–10 phút xuống dưới 2 phút/yêu cầu.
- ≥ 85% câu trả lời được tạo có căn cứ từ tài liệu chính thức.
- 100% yêu cầu liên quan đến chẩn đoán, điều trị hoặc quyết định y khoa được chuyển nhân viên y tế có chuyên môn review.

**Quick architecture:** LLM, RAG, Rule, Human-in-the-loop.

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.

## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Ai đang thực hiện tác vụ hằng ngày? |
| **2. Current Workflow** | Mô tả tóm tắt quy trình thủ công hiện tại và công cụ sử dụng. |
| **3. Bottleneck** | Bước nào chậm, lỗi, hoặc cần xử lý ngôn ngữ tự động nhiều nhất? |
| **4. Business Impact** | Tổn thất thực tế đo bằng thời gian, chi phí, hoặc SLA của Vingroup. |
| **5. Success Metric** | AI giải quyết được thì đạt ngưỡng số mấy? (Ví dụ: *"85% vé được phân loại dưới 10s"*). |
| **6. Operational Boundary** | AI được phép làm gì, TUYỆT ĐỐI không được làm gì, điểm nào cần duyệt? |

## 3.3. Future-State Flow & AI Fit (25 min)
* **Xác định mức AI Fit (AI-Fit Matrix):** Giải pháp thuộc nhóm nào? [ ] Rule / State-Machine [ ] LLM Feature [ ] Agentic Loop.
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
