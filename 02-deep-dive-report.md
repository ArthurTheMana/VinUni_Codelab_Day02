# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

Tụi mình chọn topic 2 của Trần Thành Vinh.

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.


## 3.2. Problem Statement (6-field) & Metrics

**Bài toán:** Khách hàng gặp khó khăn khi tìm đúng khu vực đón xe Xanh SM tại sân bay.

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Khách hàng đặt xe Xanh SM tại sân bay và tài xế hỗ trợ xác nhận vị trí đón khách. |
| **2. Current Workflow** | Khách đặt xe trên ứng dụng Xanh SM, xem thông tin điểm đón và tìm khu vực đón tại sân bay. Nếu không xác định được vị trí, khách phải gọi điện hoặc nhắn tin cho tài xế trước khi lên xe. |
| **3. Bottleneck** | Bước 3–4: Khách khó xác định đúng khu vực đón do các hãng taxi có vị trí riêng. Việc tìm đường và liên hệ tài xế có thể mất khoảng 5–7 phút/lượt (giả định). |
| **4. Business Impact** | Giả sử có 500 chuyến gặp vấn đề này mỗi ngày, việc giảm 3–4 phút/chuyến có thể tiết kiệm khoảng 25–33,3 giờ chờ/ngày. Quy đổi theo mức 60.000 VNĐ/giờ, giá trị thời gian tương đương khoảng 1,5–2 triệu VNĐ/ngày. Đây là số liệu giả định, không phải chi phí thực tế của Xanh SM. |
| **5. Success Metric** | Mục tiêu giảm thời gian tìm điểm đón từ 5–7 phút xuống còn 2–3 phút/lượt, đồng thời giảm số lần khách cần liên hệ tài xế để xác nhận vị trí. |
| **6. Operational Boundary** | AI chỉ được hướng dẫn dựa trên thông tin nhà ga, cửa ra và điểm đón đã được xác minh. AI không được tự tạo vị trí đón, hướng dẫn khách đến khu vực cấm hoặc tự thay đổi điểm đón. Nếu thiếu thông tin, hệ thống phải chuyển sang hỗ trợ của tài xế hoặc nhân viên. |

*Lưu ý: Workflow và số liệu là giả định để phục vụ bài Lab.*

---

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