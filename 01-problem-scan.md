# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Xanh SM | Pain từ người khác | Khách hàng đặt xe Xanh SM tại sân bay có thể gặp khó khăn khi xác định đúng khu vực đón khách (Pickup Point) do mỗi hãng taxi hoặc dịch vụ gọi xe có vị trí đón riêng. Điều này có thể gây nhầm lẫn, khiến khách phải đi tìm xe, liên hệ tài xế nhiều lần và kéo dài thời gian đón khách. (Nguyễn Tài Minh Huy) |
| 2 | VinFast | AI-upgrade, Stakeholder pain | Lập lịch cho người sửa chữa phương tiện. (Trần Thành Vinh)|
| 3 | Vinhomes | Tốn thời gian | Phân loại thủ công và điều phối Ticket báo cáo sự cố (điện, nước) của cư dân cho đội kỹ thuật. |
| 4 | Vinhomes | Repetitive, Time-consuming | Các nhân viên bảo hành các tòa vinhomes thường xuyên nhận được các phản ánh sửa chữa từ cư dân như: đèn hỏng, thang máy, đường nước,.... nhưng thông tin nhận được đôi lúc bị thiếu như tòa nhà, tầng, chi tiết hỏng hóc cần sửa chữa. (Hoàng Dương Anh Quân)|
| 5 | VinPearl | Tốn thời gian | Việc trích xuất thông tin đặt phòng theo đoàn từ email không theo mẫu thống nhất có thể khiến nhân viên Vinpearl mất nhiều thời gian nhập liệu và kiểm tra thông tin. (Nguyễn Văn Hùng)|

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1 (Minh Huy)                            │
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
│ QUICK PROBLEM CARD #2 (Trần Thành Vinh)                     │
│                                                             │
│ Bài toán (1 câu):                                           │
│ Ứng dụng AI hỗ trợ tự động lập lịch sửa chữa phương tiện,   │
│ tối ưu phân công kỹ thuật viên, thời gian và vị trí sửa     │
│ chữa dựa trên loại lỗi, mức độ ưu tiên và nguồn lực xưởng.  │
│                                                             │
│ Công ty thành viên:                                         │
│ [x] VinFast [ ] Xanh SM [ ] Vinhomes                        │
│ [ ] Vinmec [ ] Khác                                         │
│                                                             │
│ Ai đang đau (Actor)?                                        │
│ Workshop Manager, Service Advisor, Technician và khách      │
│ hàng. Đặc biệt là Workshop Manager chịu áp lực trong việc   │
│ kiểm tra nguồn lực và phân công lịch sửa chữa.              │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│ 1. Tiếp nhận yêu cầu sửa chữa và thông tin phương tiện.     │
│ ──> 2. Kiểm tra lỗi, xác định loại công việc và mức độ      │
│ ưu tiên.                                                    │
│ ──> 3. Kiểm tra lịch làm việc, chuyên môn kỹ thuật viên     │
│ và công suất khu vực sửa chữa.                              │
│ ──> 4. Phân công kỹ thuật viên, vị trí và thời gian         │
│ sửa chữa.                                                   │
│ ──> 5. Cập nhật, điều chỉnh lịch khi có phát sinh.          │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Bước 3 và 4 – Kiểm tra nguồn lực và lập lịch phân công.     │
│ ⏱ Ước tính 10–20 phút/yêu cầu sửa chữa.                    │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ - Phân tích yêu cầu, xác định loại lỗi và chuyên môn cần có.│
│ - Dự đoán thời gian sửa chữa từ dữ liệu lịch sử.            │
│ - Đề xuất kỹ thuật viên phù hợp với chuyên môn và lịch làm. │
│ - Tối ưu khung giờ, vị trí sửa chữa theo công suất xưởng.   │
│ - Đề xuất điều chỉnh lịch khi có công việc khẩn cấp.        │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ - Giảm thời gian lập lịch từ 10–20 phút xuống dưới 3 phút/  │
│ yêu cầu.                                                    │
│ - Giảm ít nhất 30% trường hợp trùng lịch hoặc phân công     │
│ không phù hợp.                                              │
│ - Giảm 20% thời gian chờ trung bình của phương tiện.        │ 
│ - ≥ 90% đề xuất lịch đáp ứng ràng buộc chuyên môn và        │
│ thời gian làm việc.                                         │
│                                                             │
│ Quick Architecture:                                         │
│ [ ] No AI [x] Rule [ ] LLM [x] Agent                        │
│ Bổ sung: Optimization + Human-in-the-loop.                  │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3 (Lê Chuẩn)                            │
│                                                             │
│ Bài toán (1 câu): Phân loại và điều phối thủ công các ticket│
│ báo cáo sự cố của cư dân trên App Vinhomes gây chậm trễ.    │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Admin/Ban quản lý (quá tải giờ cao     │
│ điểm) và Cư dân (bức xúc vì phải chờ đợi lâu).              │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Cư dân tạo ticket (text/ảnh) ──> 2. Admin đọc hiểu &   │
│   xem ảnh để xác định loại lỗi ──> 3. Đánh giá mức độ khẩn  │
│   cấp ──> 4. Assign cho đội kỹ thuật phù hợp & báo cư dân.  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 5-7 phút/lượt)│
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3 (AI tự     │
│ động phân tích text/ảnh của cư dân, gắn tag loại sự cố, mức │
│ độ ưu tiên và đề xuất luôn đội kỹ thuật xử lý).             │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ 1. Efficiency: Giảm thời gian xử lý & điều phối từ 5-7 phút │
│ ──> dưới 30 giây/lượt (Đo bằng: Thời gian chênh lệch từ lúc │
│ user tạo ticket đến lúc trạng thái đổi thành "Assigned").   │
│ 2. Quality: Tỷ lệ phân loại đúng đội kỹ thuật đạt > 95% (Đo │
│ bằng: Tỷ lệ ticket KHÔNG bị thợ kỹ thuật reject/chuyển trả  │
│ lại trên phần mềm quản lý).                                 │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```