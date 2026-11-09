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
| 1 | **Vinhomes** | Tốn thời gian | Phân loại thủ công và điều phối Ticket báo cáo sự cố (điện, nước) của cư dân cho đội kỹ thuật. |
| 2 | **VinFast** | Lặp lại | Trích xuất và phân tích mã lỗi (error codes) thủ công từ các file log hệ thống trạm sạc/xe điện. |
| 3 | **Vinmec** | Pain từ người khác | Hệ thống phân phối, xếp lịch thông minh để tránh gây quá tải tại bệnh viện. |
| 4 | **Xanh SM** | AI-upgrade | Làm sạch, chuẩn hóa và gán nhãn dữ liệu GPS/chuyến đi bị nhiễu trước khi đưa lên Dashboard. |
| 5 | **VinUni** | AI-upgrade | Xếp lịch, phân bổ phòng học và giảng viên │
 thủ công tốn nhiều tuần làm việc và dễ xảy ra xung đột. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
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
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3(⏱ 20-30        |
| phút/lượt)                                                  │
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

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Hệ thống điều phối và xếp lịch khám bệnh  │
│ thông minh nhằm cân bằng tải và giảm thời gian chờ đợi.     │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Bệnh nhân (mệt mỏi vì chờ đợi lâu) và  │
│ Lễ tân/Điều phối viên y tế (áp lực khi phân bổ thủ công).   │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Bệnh nhân đến viện/đặt lịch ──> 2. Lễ tân xếp người    │
│   vào slot của bác sĩ theo thứ tự ──> 3. Bệnh nhân ngồi chờ │
│   ──> 4. Bác sĩ khám (có ca phức tạp kéo dài gây tắc nghẽn).│
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 (Xếp lịch cứng nhắc,│
│ không dự đoán được ca khó/dễ) (⏱ Gây chờ đợi 30-45 phút).   │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 (AI phân tích  │
│ triệu chứng ban đầu, dự đoán thời gian khám của từng ca và  │
│ điều phối động bệnh nhân sang phòng khám/bác sĩ đang trống).│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ 1. Efficiency: Giảm thời gian chờ đợi trung bình của bệnh   │
│ nhân từ 45 phút ──> dưới 15 phút (Đo bằng: Thời gian từ lúc │
│ check-in lấy số đến lúc bước vào phòng gặp bác sĩ).         │
│ 2. Quality: Tỷ lệ ca khám bắt đầu đúng giờ đạt > 90% (Đo    │
│ bằng: Độ lệch thời gian giữa lịch dự kiến AI xếp và giờ bác │
│ sĩ bắt đầu khám thực tế trên hệ thống HIS của bệnh viện).   │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Xếp lịch, phân bổ phòng học và giảng viên │
│ thủ công tốn nhiều tuần làm việc và dễ xảy ra xung đột.     │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [x] Khác (Ghi rõ) VinUni   │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên Giáo vụ/Phòng đào tạo (quá   │
│ tải) và Giảng viên/Sinh viên (thời khóa biểu bất hợp lý).   │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Thu thập danh sách môn, sĩ số và yêu cầu của giảng viên│
│   ──> 2. Giáo vụ xếp lịch thủ công trên Excel (ghép môn -   │
│   phòng - người) ──> 3. Rà soát chéo tìm xung đột (trùng    │
│   giờ/phòng) ──> 4. Ban hành thời khóa biểu cho toàn trường.│
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 7-14 ngày). │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3 (AI Agent  │
│ tiếp nhận các ràng buộc, tự động tính toán và xuất ra hàng  │
│ loạt phương án xếp lịch tối ưu mà không bị trùng lặp).      │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ 1. Efficiency: Giảm tổng thời gian xếp lịch từ 7-14 ngày    │
│ ──> dưới 2 giờ (Đo bằng: Thời gian từ lúc chốt danh sách    │
│ ràng buộc đầu vào đến khi ra được bản lịch nháp đầu tiên).  │
│ 2. Quality: Tỷ lệ xung đột (trùng phòng, trùng giờ của      │
│ giảng viên) đạt 0%, và đáp ứng >90% nguyện vọng giờ dạy     │
│ (Đo bằng: Số lượng ticket yêu cầu đổi/sửa lịch từ giảng     │
│ viên sau khi ban hành).                                     │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘
```
