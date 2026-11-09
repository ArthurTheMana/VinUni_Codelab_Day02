# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

Tụi mình chọn topic 2 của Trần Thành Vinh.

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
---


## 3.2. Problem Statement (6-field) & Metrics (15 min)


| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Quản lý nhà xưởng (Workshop Manager) là người lập và duyệt lịch. Service Advisor cung cấp thông tin lỗi, Technician thực hiện sửa chữa, khách hàng chờ xe. |
| **2. Current Workflow** | Tiếp nhận yêu cầu → Service Advisor xác định loại việc và ưu tiên → Manager đối chiếu lịch KTV, chuyên môn, khu vực trống → phân công KTV, vị trí, thời gian → cập nhật khi có thay đổi. Công cụ: bảng tính/sổ lịch, điện thoại, hệ thống quản lý dịch vụ. |
| **3. Bottleneck** | Bước 3–4: Kiểm tra nguồn lực và lập lịch. Manager phải đối chiếu thủ công lịch làm việc, chuyên môn KTV, thời gian sửa dự kiến và công suất xưởng, dễ dẫn đến trùng lịch hoặc phân công không phù hợp; xếp lại lịch khi có việc khẩn cấp rất tốn công. |
| **4. Business Impact** | Giả sử xưởng nhận 60 yêu cầu/ngày, mỗi yêu cầu tiết kiệm 8–15 phút lập lịch → tiết kiệm 8–15 giờ công/ngày. Với chi phí giả định 100.000 VNĐ/giờ, tương đương 0,8–1,5 triệu VNĐ/ngày/xưởng. Ngoài ra giảm thời gian chờ của xe, giảm trùng lịch/phân công sai và tăng mức sử dụng khu vực sửa chữa, nâng cao trải nghiệm khách hàng. |
| **5. Success Metric** | (1) Giảm thời gian lập lịch từ 10–20 phút xuống < 3 phút/yêu cầu. (2) Giảm ≥ 30% trường hợp trùng lịch hoặc phân công không phù hợp. (3) Giảm 20% thời gian chờ trung bình trước khi sửa. (4) ≥ 90% đề xuất đáp ứng ràng buộc chuyên môn và giờ làm việc. |
| **6. Operational Boundary** | AI được phép phân tích yêu cầu, ước lượng thời gian, đề xuất KTV/khung giờ/khu vực và đề xuất điều chỉnh lịch. AI không được tự ý xác nhận lịch, phân công KTV không đủ chuyên môn/vượt giờ làm việc, bỏ qua ràng buộc an toàn, tự hạ mức ưu tiên hoặc tự thông báo lịch cho khách khi chưa được Manager duyệt. Khi dữ liệu thiếu hoặc không có phương án khả thi, hệ thống phải chuyển Manager xử lý thủ công. |


### Success Metrics theo 4 nhóm


| Nhóm | Metric | Target |
|---|---|---:|
| **Feasibility** | Tỷ lệ yêu cầu có đủ dữ liệu (loại lỗi, ưu tiên, lịch KTV, khu vực) để lập lịch | ≥ 90% |
| | Tỷ lệ đề xuất đáp ứng ràng buộc chuyên môn và giờ làm việc | ≥ 90% |
| **Financial Impact** | Giá trị công lập lịch tiết kiệm với giả định 60 yêu cầu/ngày | 0,8–1,5 triệu VNĐ/ngày/xưởng |
| | Giảm chi phí do trùng lịch/phân công sai (làm lại, xe nằm chờ) | ≥ 30% |
| **Operational Efficiency** | Giảm số trường hợp trùng lịch hoặc phân công không phù hợp | ≥ 30% |
| | Giảm thời gian chờ trung bình của xe trước khi sửa | ≥ 20% |
| **Time Reduction** | Thời gian lập lịch | Từ 10–20 phút xuống < 3 phút |
| | Tỷ lệ cắt giảm thời gian | **≥ 70–85%** |

*Các con số là mục tiêu đề xuất để kiểm chứng, không phải kết quả vận hành thực tế của VinFast. Giá trị thời gian tiết kiệm chưa đồng nghĩa với lợi nhuận thực tế.*

---

## 3.3. Future-State Flow & AI Fit (25 min)


### A. AI-Fit Matrix


**Lựa chọn:**
- [x] Rule / State-Machine
- [x] Optimization (bổ sung cho bài toán lập lịch)
- [x] LLM Feature
- [ ] Agentic Loop


**Giải thích:**


- **Rule / State-Machine:** Kiểm tra ràng buộc cứng: chuyên môn KTV, giờ làm việc, khu vực/thiết bị phù hợp, quy tắc ưu tiên và an toàn, không trùng lịch.
- **Optimization:** Bộ giải lập lịch (constraint solver) chọn KTV, khung giờ, khu vực tối ưu theo ưu tiên, thời gian chờ và công suất xưởng; tính lại nhanh khi có xe khẩn cấp.
- **LLM Feature:** Đọc mô tả lỗi tự do, trích xuất loại công việc và chuyên môn cần thiết, ước lượng thời gian sửa dựa trên các ca tương tự, giải thích lý do đề xuất bằng ngôn ngữ tự nhiên cho Manager.
- **Agentic Loop:** Chưa cần trong MVP vì hệ thống chỉ đề xuất, Manager duyệt; chưa cần tự chủ thực hiện chuỗi hành động.


**Đề xuất:** Kết hợp Rule + Optimization + LLM + Human-in-the-loop. LLM chỉ hiểu và giải thích; Rule và Optimization quyết định tính hợp lệ và tối ưu của lịch; Manager là người duyệt cuối.


### B. Future-State Flow (To-Be)


```text
[1] Tiếp nhận yêu cầu sửa chữa và thông tin phương tiện
              |
              v
[2] 🔵 LLM FEATURE
    Phân tích mô tả lỗi → loại công việc, chuyên môn cần thiết,
    ước lượng thời gian sửa (kèm độ tin cậy)
              |
              v
[3] 🟢 HUMAN STEP (Service Advisor)
    Xác nhận loại việc và mức độ ưu tiên
              |
              v
[4] 🔵 RULE ENGINE
    Lọc KTV đủ chuyên môn, đang trong giờ làm,
    khu vực sửa chữa còn trống
              |
              v
[5] 🔵 OPTIMIZATION
    Tìm phương án KTV + khung giờ + khu vực tối ưu
    (giảm thời gian chờ, tránh trùng lịch)
              |
              v
[6] 🔵 LLM FEATURE
    Giải thích đề xuất và các phương án thay thế
              |
              v
[7] 🟢 HUMAN STEP (HITL – Workshop Manager)
    Xem, chỉnh sửa, duyệt hoặc từ chối lịch
              |
              v
[8] Thông báo Technician và khách hàng
              |
              v
[9] Có việc khẩn cấp / thay đổi → quay lại bước 4–5
    để đề xuất điều chỉnh lịch, Manager duyệt lại
              |
              v
          [HOÀN THÀNH]
```


**Fallback (↩️):**


Nếu LLM không hiểu mô tả lỗi, độ tin cậy thấp hoặc solver không tìm được phương án khả thi:


1. Không tự suy đoán loại công việc hoặc nới lỏng ràng buộc cứng.
2. Chuyển Service Advisor xác nhận hoặc nhập thủ công loại việc và ưu tiên.
3. Hiển thị các xung đột (thiếu KTV chuyên môn, hết khu vực trống) và gợi ý phương án gần nhất (dời khung giờ, mượn KTV ca khác).
4. Manager lập lịch thủ công nếu vẫn không giải quyết được.


### C. Operational Boundaries


| AI được phép làm | AI tuyệt đối không được làm |
|---|---|
| Phân loại công việc và ước lượng thời gian sửa | Tự xác nhận lịch khi chưa có Manager duyệt |
| Đề xuất KTV, khung giờ, khu vực phù hợp | Phân công KTV không đủ chuyên môn hoặc ngoài giờ làm việc |
| Đề xuất điều chỉnh lịch khi có xe khẩn cấp | Tự ý hoãn/hủy lịch xe khác hoặc thay đổi mức ưu tiên |
| Giải thích lý do và phương án thay thế | Bỏ qua ràng buộc an toàn hoặc ước lượng thời gian không có căn cứ |
| Cảnh báo xung đột lịch | Chia sẻ thông tin khách hàng/phương tiện cho người không có quyền |

---


# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)


### AI Readiness Checklist:
1. [ ] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
   *Chưa đầy đủ.* Hiện chỉ có dữ liệu giả lập (roster, ca, bay) trong prototype. Chưa có log lịch sửa chữa thực tế để đo baseline (thời gian lập lịch, tỷ lệ trùng lịch, thời gian chờ) và thời gian sửa theo loại lỗi.
2. [x] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
   *Có.* AI chỉ đề xuất (`[DRAFT_ONLY]`), Manager duyệt cuối; ràng buộc cứng do Rule/Optimization kiểm tra; lỗi an toàn luôn URGENT; có fallback `escalate_to_manager`.
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?
   *Chưa xác nhận.* Cần phỏng vấn Workshop Manager và Service Advisor; Manager vẫn giữ quyền duyệt nên mức thay đổi quy trình thấp.


### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[x] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.


**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> **GO có điều kiện, scope hẹp:** pilot tại 1 xưởng, chỉ với nhóm công việc phổ biến, chế độ đề xuất (Manager duyệt từng lịch).
>
> 1. **Pain point rõ, đo được:** Bước 3–4 tốn 10–20 phút/yêu cầu và dễ trùng lịch. Giả định 60 yêu cầu/ngày, tiết kiệm 8–15 phút/yêu cầu tương đương khoảng 0,8–1,5 triệu VNĐ/ngày/xưởng (ước tính, chưa kiểm chứng).
> 2. **Kiến trúc phù hợp, chi phí thấp:** Ràng buộc chuyên môn, giờ làm và bay trống là bài toán xác định nên dùng Rule + Optimization (không dùng AI để quyết định). LLM chỉ đọc mô tả lỗi, ước lượng thời gian và giải thích, mỗi yêu cầu chỉ cần một lệnh gọi LLM nhỏ. Không cần Agentic Loop.
> 3. **Rủi ro kiểm soát được:** System prompt ở Phase 4 ép tiền tố `[DRAFT_ONLY]`, cấm phân công sai chuyên môn/ngoài ca, khóa ưu tiên URGENT cho lỗi an toàn và có escalate khi không có phương án khả thi. Bộ 4 adversarial test (ép sai chuyên môn, bỏ DRAFT_ONLY, hạ ưu tiên lỗi phanh, fake override) được kiểm tự động. *Cần chạy và ghi kết quả thực tế; chưa được ghi nhận ở đây.*
> 4. **Điểm yếu cần xử lý trước khi mở rộng:** chưa có dữ liệu thật để xác lập baseline; ước lượng thời gian sửa của LLM có thể sai nên phải đối chiếu với lịch sử và hiển thị độ tin cậy; stakeholder chưa được xác nhận.
>
> **Điều kiện để tiếp tục / mở rộng:** (a) thu 2–4 tuần log lịch thật để đo baseline; (b) chạy shadow mode: AI đề xuất song song, Manager vẫn lập lịch như cũ rồi so sánh; (c) đạt ≥ 90% đề xuất thỏa ràng buộc, 0 vi phạm lỗi an toàn và thời gian lập lịch < 3 phút thì mới mở rộng. Nếu không đạt thì chuyển sang **NOT YET** và chỉ giữ lại phần Rule/Optimization.

---
