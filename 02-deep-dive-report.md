# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.

Sơ đồ quy trình hiện tại 
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │     │ Bước 5       │
│ Tiếp nhận xe │     │ NV kiểm tra, │     │ Quản lý đối  │     │ Phân công KTV│     │ Cập nhật lịch│
│ & yêu cầu từ │ ──→ │ xác định lỗi │ ──→ │ chiếu lịch,  │ ──→ │ & vị trí cầu │ ──→ │ thủ công khi │
│ Khách hàng   │     │ & ưu tiên    │     │ chuyên môn   │     │ nâng sửa chữa│     │ có thay đổi  │
│              │     │              │     │ & slot rảnh  │     │              │     │              │
│ Ai: Lễ tân   │     │ Ai: Cố vấn DV│     │ Ai: Quản lý  │     │ Ai: Quản lý  │     │ Ai: Quản lý  │
│ 🔄 Handoff   │     │ ⏱ 5-10 phút │    │ 🔴 Bottleneck│    │ 🔴 Bottleneck│      │ 🔄 Handoff  │
│ ⏱ 3 phút     │     │              │    │ ⏱ 10-15 phút │    │ ⏱ 5 phút     │     │              │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
Tổng cộng = 23 - 33 phút/yêu cầu (Chỉ tính riêng phần intake và lên lịch, chưa tính thời gian thực sửa).

🔴 Bottleneck: Bước 3 và 4. Quản lý nhà xưởng phải liên tục nhìn bảng tính/hệ thống cũ để dò tìm: 1) Ai đang rảnh? 2) Người rảnh có đúng chuyên môn (VD: thợ máy gầm vs thợ điện/pin)? 3) Cầu nâng nào đang trống? Việc check chéo 3 điều kiện này bằng mắt người rất chậm và dễ sai sót.

🔄 Handoff: Từ Lễ tân sang Cố vấn dịch vụ (Service Advisor), và từ Cố vấn dịch vụ chuyển yêu cầu sang cho Quản lý xưởng (Workshop Manager).

---

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

| Field | Nội dung chi tiết |
| :--- | :--- |
| **1. Actor / Operator** | Quản lý nhà xưởng (Workshop Manager), Cố vấn dịch vụ, Kỹ thuật viên (Technician). |
| **2. Current Workflow** | Khách đưa xe vào, Cố vấn dịch vụ xác định lỗi. Sau đó, Quản lý xưởng phải tự dò lịch làm việc, đánh giá chuyên môn kỹ thuật viên và kiểm tra tình trạng trống của các khu vực sửa chữa (cầu nâng) để ghép nối và phân công thủ công. Lịch phải vẽ/chỉnh lại bằng tay khi có ca sửa kéo dài hoặc xe cấp cứu (ưu tiên cao) chen ngang. |
| **3. Bottleneck** | Bước kiểm tra nguồn lực đa chiều (chuyên môn KTV + thời gian trống + không gian xưởng) và xếp lịch thủ công (mất 10-20 phút/yêu cầu, dễ xảy ra tình trạng trùng lịch hoặc giao sai thợ). |
| **4. Business Impact** | Giảm công suất (throughput) của xưởng, xe phải nằm chờ lâu gây tốn kém chi phí lưu kho. Khách hàng phàn nàn vì thời gian chờ sửa chữa kéo dài. Quản lý xưởng bị quá tải bởi các công việc sự vụ, không có thời gian kiểm soát chất lượng (QC). |
| **5. Success Metric** | - **Efficiency:** Giảm thời gian lập lịch từ 10–20 phút xuống < 3 phút/lượt. Giảm 20% thời gian xe chờ trước khi sửa.<br>- **Quality:** Giảm 30% lỗi trùng lịch. Đạt ≥ 90% tỷ lệ lịch đề xuất đáp ứng đúng ràng buộc chuyên môn và giờ giấc. |
| **6. Operational Boundary** | - **Được phép:** AI (kết hợp Optimization) được phân tích text mô tả lỗi để ước lượng thời gian, đọc database lịch trực của KTV và công suất xưởng để đề xuất lịch.<br>- **TUYỆT ĐỐI CẤM:** AI không được tự động chốt lịch hoặc tự ý hủy/đẩy lùi lịch hẹn trước của khách hàng VIP mà không báo trước.<br>- **Duyệt (HITL):** Quản lý nhà xưởng bắt buộc phải nhấn "Approve" (Duyệt) phương án xếp lịch do AI đề xuất. |

---

## 3.3. Future-State Flow & AI Fit (25 min)
* **Xác định mức AI Fit (AI-Fit Matrix):** Giải pháp thuộc nhóm nào? [ ] Rule / State-Machine [ ] LLM Feature [ ] Agentic Loop.
* **Vẽ Future-State Flow:** Đánh dấu rõ:
  * 🔵 **AI Step:** Tác vụ LLM xử lý.
  * 🟢 **Human Step (HITL):** Bước con người phê duyệt/review (Human-in-the-loop).
  * ↩️ **Fallback:** Kế hoạch dự phòng khi LLM trả về kết quả lỗi hoặc không tự tin.

Xác định mức AI Fit: Giải pháp thuộc nhóm [x] Agentic Loop (Đây là sự kết hợp giữa LLM đọc hiểu lỗi mô tả bằng chữ và một Engine tối ưu hóa [Optimization Rule-based Solver] để giải quyết bài toán ràng buộc tài nguyên đa biến một cách liên tục/động).

Vẽ Future-State Flow (Luồng tương lai):

Plaintext
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Cố vấn DV    │ ──→ │ 🔵 AI Agent  │ ──→│ 🟢 Quản lý  │ ──→  │ KTV nhận task│
│ nhập mô tả   │     │ đọc lỗi, tính│     │ xưởng kiểm   │     │ qua App và   │
│ lỗi & độ khẩn│     │ toán & tự nháp│    │ tra & nhấn   │     │ bắt đầu sửa  │
│ lên hệ thống │     │ lịch tối ưu  │     │ nút Duyệt    │     │ chữa xe      │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                            │                    │
                            │ (Dự đoán ETA,      │ (Quản lý có thể 
                            │  match KTV,        │  kéo thả sửa lại 
                            │  match cầu nâng)   │  trước khi duyệt)
                            │                    ▼
                            │             ↩️ Fallback:
                            │             Nếu AI báo "Không tìm thấy
                            │             slot phù hợp", hệ thống 
                            │             hiển thị danh sách KTV/Xưởng
                            │             dạng Manual (kẻ ô lưới) để 
                            │             Quản lý tự xử lý thủ công.
                            ▼
                     ┌──────────────┐
                     │ 🔵 Auto-Sync │ 
                     │ AI tự update │
                     │ & dồn lịch   │
                     │ khi có ca gấp│
                     └──────────────┘
Chú thích các điểm đánh dấu:

🔵 AI Step: Agent tự động đọc Text mô tả lỗi, dùng dữ liệu lịch sử để dự đoán cần bao nhiêu thời gian sửa, sau đó dùng thuật toán "nhét" (fit) vào khoảng thời gian trống của đúng KTV có chuyên môn đó và cầu nâng tương ứng. Tự động "dồn" lịch (reschedule) nếu có xe khẩn cấp.

🟢 Human Step (HITL): Quản lý xưởng chỉ đóng vai trò "Người giám sát". AI trình bày ra 1-2 phương án tối ưu, Quản lý nhìn thấy hợp lý thì bấm DUYỆT (Approve) trong vòng vài chục giây thay vì tự xếp từ đầu.

↩️ Fallback: Nếu vào ngày cao điểm (Lễ/Tết), không còn KTV rảnh đáp ứng đủ điều kiện ràng buộc, hệ thống ngắt chế độ Auto và trả lại giao diện bảng lịch truyền thống để Quản lý tự thương lượng nhồi nhét thủ công.

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

### AI Readiness Checklist:
1. [x] **Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?** (VinFast đã có sẵn dữ liệu từ hệ thống quản lý xưởng DMS, bao gồm lịch sử sửa chữa, chuyên môn KTV, và thời gian tiêu chuẩn cho từng loại lỗi).
2. [x] **Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?** (Có. AI chỉ đóng vai trò "Đề xuất nháp", Quản lý xưởng bắt buộc phải duyệt (HITL) trước khi lịch chính thức được áp dụng. Nếu AI lỗi, hệ thống tự động quay về giao diện xếp lịch thủ công).
3. [x] **Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?** (Có. Quản lý xưởng và Cố vấn dịch vụ đang bị quá tải với các công việc hành chính sự vụ, họ rất mong muốn có công cụ tự động hóa để tập trung vào kiểm soát chất lượng).

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[x] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> Dự án đạt mức độ **GO** với chiến lược triển khai Prototype thu hẹp (thử nghiệm trước tại 1-2 xưởng dịch vụ lớn ở Hà Nội hoặc TP.HCM). 
> 
> **1. Bằng chứng kỹ thuật:** Sự kết hợp giữa LLM (để đọc hiểu mô tả lỗi bằng ngôn ngữ tự nhiên từ Cố vấn dịch vụ) và Optimization Solver (để giải bài toán tối ưu ràng buộc về KTV và Cầu nâng) là một giải pháp khả thi và đã được chứng minh trong ngành công nghiệp. Cơ chế Human-in-the-loop (HITL) đảm bảo an toàn tuyệt đối cho vận hành thực tế.
> 
> **2. Chi phí & Lợi ích (ROI):** Chi phí gọi API LLM và chạy Agent tính toán là rất nhỏ (chỉ vài trăm đồng/yêu cầu), nhưng đem lại lợi ích khổng lồ: cắt giảm hơn 80% thời gian lên lịch (từ 20 phút xuống dưới 3 phút). Quan trọng hơn, việc giảm tỷ lệ trùng lịch và tối ưu hóa thời gian trống của cầu nâng sẽ giúp tăng công suất (throughput) tiếp nhận xe của toàn xưởng, trực tiếp mang lại doanh thu và cải thiện mức độ hài lòng của khách hàng (CSAT).