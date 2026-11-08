# 01 — Problem Scan

**Bài lab:** AI Product Scoping (Vin Smart Future)

**Nhánh cá nhân:** TrungTinh

# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Sử dụng đúng **4 Lenses**: Lặp lại (Repetitive); Tốn thời gian (Time-consuming); AI có thể tốt hơn (AI-upgrade); Pain từ người khác (Stakeholder Pain).

### 📝 List bài toán của tôi

| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | VinFast | Tốn thời gian (Time-consuming) | Cố vấn dịch vụ cần tổng hợp hồ sơ để cập nhật tình trạng sửa chữa. Khách hàng phản ánh nhiều lần liên hệ trong thời gian chờ; phần theo dõi sau nhận xe tại Hoàng Mai liên quan hỗ trợ hậu mãi. Nguồn: [S01b — Quang Vũ Đoàn, 09/03/2026](https://vinfast.vn/dien-dan/thao-luan/phu-tung-fadil/), [S01a — Dũng Nguyễn Anh, 17–18/06/2026](https://vinfast.vn/dien-dan/thao-luan/goc-buc-xuc-voi-vf-hasc-hoang-mai/). |
| 2 | Vinhomes — Ocean Park 1 | Lặp lại (Repetitive) | Đề xuất tác vụ ghi nhận, nhóm và theo dõi ý kiến cư dân còn mở. Bài báo ghi nhận phản ánh ý kiến chưa được lắng nghe đầy đủ tại hội nghị ngày 18/01/2026. Nguồn: [S02 — BBĐ, Báo Cựu Chiến Binh Việt Nam, 29/01/2026](https://cuuchienbinh.vn/can-lam-ro-dau-hieu-vi-pham-dan-chu-tai-hoi-nghi-nha-chung-cu-vinhomes-ocean-park-1-d41091.html). |
| 3 | VinWonders Nha Trang | AI có thể tốt hơn (AI-upgrade) | Nhân viên cần tra cứu và trả lời về đường đi, tiện ích và phí. Du khách phản ánh ít biển chỉ dẫn và cho biết ghế nằm bãi biển có phí riêng. Nguồn: [S03 — nika.dm, Trip.com, ngày hiển thị 5/6, chưa xác định năm](https://www.trip.com/moments/detail/nha-trang-670-146195513/); nội dung đang đọc là bản dịch của nền tảng. |
| 4 | Xanh SM (GSM) | Pain từ người khác (Stakeholder Pain) | Nhân viên cần phân loại lý do gián đoạn chuyến từ log/ghi chú. Người đăng phản ánh đơn liên tỉnh biến mất gần giờ đi; cập nhật cho biết hãng đã gọi báo giờ có xe. Nguồn: [S04 — CloneHoiNgu, VOZ, 14/02/2026, bài #1 và #10](https://voz.vn/t/khieu-nai-xanhsm-huy-don-lien-tinh-sat-gio.1208593/). |
| 5 | Vinmec | AI có thể tốt hơn (AI-upgrade) | Nhân viên cần hỗ trợ khách quốc tế tra cứu thông tin hành chính/lịch hẹn bằng ngôn ngữ phù hợp. Jorge Goyanes phản ánh khó giao tiếp tiếng Anh và chatbot tiếng Việt tại thời điểm đánh giá. Nguồn: [S05 — Trustpilot](https://se.trustpilot.com/reviews/69020c46f7c5456cb0768535), [trang tổng hợp](https://ca.trustpilot.com/review/vinmec.com), đầu đánh giá ghi 29/10/2025; phía dưới nội dung có mốc 28/10/2025. |

Các nguồn là phản ánh hoặc bài báo dẫn phản ánh, chưa đủ để suy rộng về toàn hệ thống hay xác định nguyên nhân gốc. Workflow và thời gian dưới đây là **giả định mô phỏng cần xác minh**; các ngưỡng giảm thời gian là **mục tiêu**, chưa phải hiệu quả đã đo.

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn ba bài toán từ SCAN: **#1 VinFast, #3 VinWonders, #4 Xanh SM**.

### Quick Problem Card #1 — VinFast

**Bài toán (1 câu):** Cố vấn dịch vụ cần tổng hợp hồ sơ và soạn cập nhật tình trạng sửa chữa cho khách hàng.

**Công ty thành viên:** VinFast.

**Ai đang đau (Actor)?** Cố vấn dịch vụ; khách hàng đang chờ thông tin.

**Workflow thủ công hiện tại (3–5 bước):**

1. Nhận yêu cầu.
2. Tra cứu hồ sơ.
3. Xác nhận với kỹ thuật viên.
4. Soạn cập nhật.
5. Kiểm tra và gửi.

**Bước nào tốn thời gian/lỗi nhất?** Bước 2 và 4, giả định tổng cộng 6 phút/lượt.

**AI có thể nhảy vào hỗ trợ ở bước nào?** Bước 2 và 4: tóm tắt ghi chú và soạn bản nháp từ trạng thái đã xác nhận.

**Đo thành công bằng gì (Metric có số)?** Mục tiêu giảm phần tổng hợp/soạn từ 6 xuống ≤2 phút/lượt; bản nháp cần cố vấn duyệt.

**Quick Architecture:** No AI / Rule / **LLM (chọn)** / Agent.

---

### Quick Problem Card #2 — VinWonders

**Bài toán (1 câu):** Nhân viên quầy thông tin cần tra cứu và trả lời câu hỏi của du khách về đường đi, tiện ích và phí dịch vụ.

**Công ty thành viên:** Khác — VinWonders Nha Trang.

**Ai đang đau (Actor)?** Nhân viên quầy thông tin; du khách cần hỗ trợ.

**Workflow thủ công hiện tại (3–5 bước):**

1. Nhận câu hỏi.
2. Tra bản đồ/bảng giá.
3. Soạn trả lời.
4. Kiểm tra và trả lời khách.

**Bước nào tốn thời gian/lỗi nhất?** Bước 2 và 3, giả định tổng cộng 6 phút/lượt.

**AI có thể nhảy vào hỗ trợ ở bước nào?** Bước 2 và 3: tìm thông tin trong tài liệu chính thức và soạn nháp Việt/Anh kèm nguồn.

**Đo thành công bằng gì (Metric có số)?** Mục tiêu giảm thời gian tra cứu/soạn từ 6 xuống ≤2 phút/câu hỏi; thông tin giá phải có nguồn.

**Quick Architecture:** No AI / Rule / **LLM (chọn)** / Agent.

---

### Quick Problem Card #3 — Xanh SM

**Bài toán (1 câu):** Nhân viên vận hành cần đọc log và ghi chú để phân loại lý do hủy hoặc thay đổi giờ phục vụ chuyến liên tỉnh.

**Công ty thành viên:** Xanh SM (GSM).

**Ai đang đau (Actor)?** Nhân viên phân tích vận hành/CSKH; hành khách bị gián đoạn kế hoạch di chuyển.

**Workflow thủ công hiện tại (3–5 bước):**

1. Lấy log.
2. Đọc ghi chú và gắn nhãn.
3. Tổng hợp báo cáo.
4. Chuyển người quản lý xem xét.

**Bước nào tốn thời gian/lỗi nhất?** Bước 2, giả định 5 phút/case.

**AI có thể nhảy vào hỗ trợ ở bước nào?** Bước 2: đề xuất nhãn và trích đoạn làm căn cứ; chuyển người khi chưa đủ thông tin.

**Đo thành công bằng gì (Metric có số)?** Mục tiêu giảm thời gian đọc, gắn nhãn và kiểm tra từ 5 xuống ≤2 phút/case.

**Quick Architecture:** No AI / Rule / **LLM (chọn)** / Agent.

---

**Đề xuất để nhóm chọn deep-dive:** Card #1 — VinFast cập nhật tình trạng sửa chữa, vì đầu vào/đầu ra rõ và bản nháp có thể được cố vấn kiểm tra theo hồ sơ.
