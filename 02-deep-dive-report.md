# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.

---

## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

## 3.2. Problem Statement (6-field) & Metrics

| Field | Nội dung chi tiết |
| :--- | :--- |
| **1. Actor / Operator** | Nhân viên Giáo vụ/Phòng đào tạo VinUni và Giảng viên. |
| **2. Current Workflow** | Giáo vụ gửi form Excel thu thập nguyện vọng giờ dạy của Giảng viên. Sau đó, gom tất cả dữ liệu (sĩ số, số lượng phòng trống, danh sách môn) để xếp lịch thủ công trên các file bảng tính. Khi có 1 người xin đổi lịch, giáo vụ phải dò lại toàn bộ file để điều chỉnh, tránh hiệu ứng domino gây trùng lặp. |
| **3. Bottleneck** | Bước 2 và 3 (xếp lịch và rà soát xung đột) tốn nhiều tuần lễ vì con người không thể xử lý tối ưu hàng ngàn ràng buộc cùng lúc (thời gian rảnh của GV, sức chứa phòng học, môn học tiên quyết). |
| **4. Business Impact** | Lãng phí hàng trăm giờ làm việc của bộ phận Giáo vụ. Sinh viên và Giảng viên phàn nàn vì lịch học thường xuyên bị thay đổi phút chót do phát hiện lỗi trùng lặp, làm chậm tiến độ đăng ký tín chỉ và khai giảng. |
| **5. Success Metric** | - **Efficiency:** Giảm tổng thời gian xếp lịch từ 14 ngày xuống dưới 2 giờ.<br>- **Quality:** Đạt 0% tỷ lệ xung đột (trùng phòng/trùng giờ). Tỷ lệ đáp ứng nguyện vọng giờ dạy của Giảng viên đạt >90%. |
| **6. Operational Boundary** | - **Được phép:** Đọc database phòng học, môn học, và text nguyện vọng của GV để tính toán tạo lịch nháp.<br>- **TUYỆT ĐỐI CẤM:** Không được tự ý thay đổi hoặc hủy khung giờ môn học cốt lõi (Core Subjects) của các Trưởng khoa/Giáo sư (VIP) mà không có sự đồng ý.<br>- **Duyệt (HITL):** Trưởng phòng đào tạo bắt buộc phải ấn duyệt (Approve) bản nháp cuối cùng trước khi publish. |
---

## 3.3. Future-State Flow & AI Fit (25 min)

Xác định mức AI Fit (AI-Fit Matrix): Giải pháp thuộc nhóm [x] Agentic Loop (Sử dụng LLM để đọc hiểu nguyện vọng ngôn ngữ tự nhiên của giảng viên, kết hợp với một hệ thống Optimization Solver để giải quyết bài toán ràng buộc xếp lịch).

Vẽ Future-State Flow (Luồng tương lai):

┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ GV nhập text │ ──→ │ 🔵 AI Agent  │ ──→ │ 🟢 Giáo vụ   │ ──→ │ Hệ thống tự  │
│ nguyện vọng &│     │ phân tích &  │     │ rà soát 3 bản│     │ update Data &│
│ giờ lên Cổng │     │ tự nháp lịch │     │ nháp & Duyệt │     │ gửi email GV │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                            │                    │                             
                            │ (Trích xuất        │ (Giáo vụ có thể             
                            │  ràng buộc,        │  kéo thả sửa lại            
                            │  chạy Solver)      │  trước khi duyệt)           
                            │                    ▼                             
                            │             ↩️ Fallback:                        
                            │             Nếu AI báo "Thiếu phòng              
                            │             trầm trọng", hệ thống                
                            │             highlight các môn bị                 
                            ▼             tắc nghẽn để Giáo vụ                 
                     ┌──────────────┐     can thiệp xếp bằng tay.              
                     │ 🔵 Auto-Sync │                                          
                     │ AI tự update │                                          
                     │ & dồn lịch   │                                          
                     │ khi GV xin   │                                          
                     │ đổi đột xuất │
                     └──────────────┘

Chú thích các điểm đánh dấu:
🔵 AI Step (Tác vụ AI): AI Agent tự động đọc hiểu text nguyện vọng của giảng viên, chuyển đổi thành các tham số ràng buộc và chạy thuật toán (Solver) để sinh ra lịch nháp tối ưu, không xung đột. Khối Auto-Sync bên dưới giúp hệ thống tự động tính toán và dồn lại lịch khi có giảng viên xin đổi giờ đột xuất.
🟢 Human Step / HITL (Con người phê duyệt): Nhân viên Giáo vụ đóng vai trò chốt chặn cuối cùng. Họ sẽ xem xét các phương án lịch do AI đề xuất, có thể kéo-thả để chỉnh sửa thủ công trực tiếp trên giao diện, sau đó bắt buộc phải nhấn nút "Duyệt" thì lịch mới có hiệu lực.
↩️ Fallback (Kế hoạch dự phòng): Nếu lượng lớp học vượt quá công suất phòng trống khiến AI không thể tìm ra phương án (tắc nghẽn), hệ thống sẽ ngắt chế độ tự động, bôi đỏ (highlight) các môn bị lỗi và trả lại giao diện bảng tính để Giáo vụ trực tiếp xử lý bằng tay.
---


# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

AI Readiness Checklist:
[x] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test? (Có sẵn dữ liệu Excel lịch học các kỳ trước, danh sách phòng và database giảng viên của VinUni).

[x] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)? (Có. AI chỉ xuất bản nháp (Draft), nhân viên Giáo vụ luôn là chốt chặn rà soát cuối cùng trước khi ban hành).

[x] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ? (Có. Khối lượng công việc xếp lịch thủ công đang làm quá tải bộ phận Đào tạo, họ rất cần công cụ tự động hóa).

Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[x] GO (Bắt đầu xây dựng Prototype): Bắt đầu phát triển với scope hẹp.
[ ] NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline): Trì hoãn để chuẩn bị thêm.
[ ] NO-GO (Không khả thi / Rule-based tốt hơn): Hủy bỏ dự án AI này.

Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):

GO. Bài toán xếp lịch học thuật sở hữu lượng biến số khổng lồ (thời gian, không gian, con người) mà thuật toán rule-based cứng ngắc hoặc sức người khó có thể xử lý tối ưu. Việc ứng dụng Agentic Loop (LLM trích xuất ràng buộc ngôn ngữ tự nhiên từ text nguyện vọng kết hợp với Solver giải bài toán tối ưu) là hoàn toàn khả thi về mặt kỹ thuật. Chi phí xây dựng Prototype thấp, nhưng mang lại ROI vận hành cực kỳ lớn: rút ngắn SLA từ hàng tuần xuống vài giờ và triệt tiêu rủi ro xung đột phòng học, nâng cao trải nghiệm cho cả giảng viên và sinh viên VinUni.