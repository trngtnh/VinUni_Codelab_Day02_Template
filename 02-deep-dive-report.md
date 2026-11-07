# 02 — Deep-Dive Report

- Tên nhóm: AI20K-Group
- Người thực hiện: Trần Đăng Khoa
- Email: 26ai.khoatd2@vinuni.edu.vn
- Nhánh cá nhân: khoa_2k3
- Bài toán đề xuất: VinFast — Hỗ trợ cập nhật tình trạng sửa chữa.

## 1. Phạm vi và căn cứ phân tích

Báo cáo phân tích một tình huống mô phỏng: cố vấn dịch vụ tại xưởng cần cập nhật tình trạng sửa chữa cho khách hàng.

Đầu vào dự kiến gồm mã phiếu, ghi chú sửa chữa và trạng thái đã được người phụ trách xác nhận. Đầu ra là bản nháp để cố vấn kiểm tra trước khi gửi.

Chưa có dữ liệu nội bộ, phỏng vấn nhân viên hoặc đo thời gian thực tế. Quy trình và các mốc thời gian dưới đây là giả định cần xác minh. Các chỉ tiêu chất lượng và thời gian là mục tiêu đề xuất, chưa phải kết quả thử nghiệm.

## 2. Quy trình hiện tại

| Bước | Người thực hiện | Công việc và đầu ra | Thời gian giả định | Điểm chuyển giao / điểm nghẽn |
|---|---|---|---|---|
| 1 | Khách hàng → cố vấn dịch vụ | Tiếp nhận câu hỏi, xác định mã phiếu sửa chữa. | 2 phút | Chuyển giao yêu cầu từ khách hàng sang cố vấn. |
| 2 | Cố vấn dịch vụ | Đọc hồ sơ, tổng hợp trạng thái và thông tin còn thiếu. | 3 phút | Điểm nghẽn: thông tin nằm trong nhiều ghi chú. |
| 3 | Cố vấn ↔ kỹ thuật viên | Làm rõ thông tin còn thiếu và xác nhận trạng thái được phép thông báo. | 4 phút | Chuyển giao giữa hai người; đây là thời gian thao tác, chưa tính chờ phản hồi. |
| 4 | Cố vấn dịch vụ | Soạn nội dung cập nhật từ thông tin đã xác nhận. | 2 phút | Điểm nghẽn: diễn đạt thông tin thành câu trả lời dễ hiểu. |
| 5 | Cố vấn dịch vụ → khách hàng | Đối chiếu, sửa và gửi phản hồi. | 1 phút | Kiểm tra cuối và chuyển thông tin cho khách hàng. |

**Tổng thời gian thao tác giả định: 12 phút/yêu cầu.**

Các bước 2, 4 và 5 chiếm tổng cộng 6 phút. Đây là phạm vi đo để so sánh với quy trình có AI, bao gồm cả việc kiểm tra của con người.

Thời gian chờ kỹ thuật viên, chờ phụ tùng hoặc chờ sửa xe được theo dõi riêng. Chưa có căn cứ để cho rằng AI sẽ rút ngắn các khoảng chờ này.



## 3. Sáu trường mô tả bài toán

| Trường | Nội dung |
|---|---|
| **1. Actor / Operator — Người thực hiện** | Cố vấn dịch vụ tổng hợp và gửi cập nhật; kỹ thuật viên xác nhận trạng thái kỹ thuật; khách hàng nhận thông tin. |
| **2. Current Workflow — Quy trình hiện tại** | Nhận yêu cầu → đọc hồ sơ → xác nhận với kỹ thuật viên → soạn nội dung → kiểm tra và gửi. Các công cụ giả định gồm nơi lưu phiếu sửa chữa, ghi chú và kênh trao đổi nội bộ. |
| **3. Bottleneck — Điểm nghẽn** | Đọc ghi chú và soạn phản hồi cần xử lý văn bản. Khi tính cả kiểm tra trước khi gửi, phạm vi này giả định chiếm 6 phút/yêu cầu. |
| **4. Business Impact — Tác động vận hành** | Tác vụ chiếm thời gian của cố vấn và ảnh hưởng tốc độ cập nhật cho khách. Nếu đạt mục tiêu, có thể tiết kiệm 3 phút thao tác/yêu cầu. Chưa có số yêu cầu/ngày hoặc chi phí lao động để quy đổi thành lợi ích tài chính. |
| **5. Success Metric — Mục tiêu thành công** | Giảm thời gian đọc, tổng hợp, soạn và duyệt từ mức giả định 6 xuống tối đa 3 phút/yêu cầu. Ít nhất 18/20 bản nháp được chấp nhận mà không sửa thông tin nghiệp vụ; không có trường hợp bịa ngày giao xe, chi phí hoặc kết luận kỹ thuật. |
| **6. Operational Boundary — Giới hạn vận hành** | AI chỉ sử dụng dữ liệu được cấp và tạo bản nháp. Cố vấn đối chiếu và duyệt trước khi gửi. AI không tự chẩn đoán, quyết định bảo hành/bồi thường hoặc cam kết thông tin chưa được xác nhận. Dữ liệu thiếu, cũ hoặc mâu thuẫn phải chuyển người kiểm tra. |

## 4. AI Fit 

| Phương án | Vai trò phù hợp | Hạn chế trong bài toán |
|---|---|---|
| Rule / mẫu trả lời cố định | Kiểm tra mã phiếu, trường bắt buộc và điền thông tin có cấu trúc vào mẫu. | Khó tổng hợp ghi chú tự do có nhiều cách diễn đạt. Nếu hồ sơ đã chuẩn hóa, phương án này có thể đủ dùng. |
| LLM Feature | Tóm tắt ghi chú, chỉ ra thông tin thiếu và soạn bản nháp dễ hiểu. | Có thể bỏ sót hoặc bổ sung thông tin thiếu căn cứ, cần kiểm tra và người duyệt. |
| Agentic Loop | Có thể thực hiện nhiều bước tra cứu khi được cấp công cụ và quyền phù hợp. | Phạm vi hiện tại chưa cần mức tự chủ này; việc xác nhận và gửi vẫn do con người thực hiện. |

**Lựa chọn đề xuất:** LLM Feature kết hợp rule kiểm tra dữ liệu và người duyệt.



## 5. Future-State Flow 

1. **Human:** Cố vấn nhận câu hỏi và xác định đúng mã phiếu.
2. **Rule:** Kiểm tra mã phiếu, các trường dữ liệu và thời điểm cập nhật.
3. **AI:** Tóm tắt hồ sơ được cung cấp, nêu căn cứ và thông tin còn thiếu.
4. **Human:** Cố vấn xác nhận trạng thái với kỹ thuật viên khi cần.
5. **AI:** Dựa trên thông tin đã xác nhận để soạn bản nháp có nhãn `[DRAFT_ONLY]`.
6. **Rule:** Kiểm tra định dạng, mã phiếu và các trường bắt buộc.
7. **Human:** Cố vấn đối chiếu nội dung với hồ sơ, sửa và duyệt trước khi gửi.
8. **Fallback:** Nếu dữ liệu hoặc kết quả không đạt, giữ yêu cầu mở và chuyển xử lý thủ công.

### Human-in-the-loop 

- Kỹ thuật viên hoặc người có trách nhiệm xác nhận thông tin kỹ thuật.
- Cố vấn kiểm tra mọi bản nháp trước khi gửi.
- Nhãn `[DRAFT_ONLY]` biểu thị bản nháp; quyền gửi phải được kiểm soát bằng quy trình hoặc phần mềm.
- Trong phạm vi bản mẫu, không cung cấp công cụ tự gửi tin cho AI.

### Fallback 

| Tình huống | Cách xử lý |
|---|---|
| Thiếu hoặc sai mã phiếu | Dừng tạo bản nháp, yêu cầu xác định đúng hồ sơ. |
| Thiếu thông tin ngày giao xe hoặc chi phí | Nêu rõ thông tin chưa được xác nhận; chuyển người phụ trách bổ sung. |
| Ghi chú mâu thuẫn hoặc chưa rõ còn hiệu lực | Yêu cầu người phụ trách xác minh trước khi dùng để trả lời. |
| AI trả nội dung thiếu căn cứ | Không gửi; cố vấn sửa hoặc soạn thủ công. |
| API lỗi hoặc đầu ra sai định dạng | Thông báo chưa tạo được bản nháp và chuyển xử lý thủ công. |



## 6. Kế hoạch đánh giá 

### 6.1. Chuẩn bị dữ liệu

Dự kiến tạo 20 hồ sơ mô phỏng, gồm:
- Hồ sơ đủ thông tin.
- Hồ sơ thiếu ngày bàn giao hoặc chi phí.
- Hồ sơ có trạng thái mâu thuẫn.
- Hồ sơ có ghi chú cũ.
- Nội dung cố dụ AI bỏ bước duyệt hoặc bịa thông tin.

Mỗi hồ sơ cần có đáp án tham chiếu, thông tin được phép sử dụng và hành vi mong đợi. Dữ liệu mô phỏng phải được ghi nhãn rõ.

### 6.2. Đánh giá thời gian

So sánh hai cách xử lý trên các hồ sơ tương đương:
- Cách A: Cố vấn đọc, soạn và duyệt thủ công hoặc dùng mẫu cố định.
- Cách B: Cố vấn dùng AI hỗ trợ, sau đó đối chiếu, sửa và duyệt.

Đo toàn bộ thời gian từ lúc bắt đầu đọc hồ sơ đến khi bản nháp sẵn sàng gửi, bao gồm thời gian chờ AI và sửa lỗi. Thời gian chờ kỹ thuật viên được ghi riêng.

Mục tiêu cho phạm vi so sánh là từ mức giả định 6 xuống tối đa 3 phút/yêu cầu. Nếu bước 1 và bước 3 giữ nguyên, tổng thời gian thao tác dự kiến giảm từ 12 xuống 9 phút/yêu cầu.

### 6.3. Đánh giá chất lượng

- Ít nhất 18/20 bản nháp được chấp nhận mà không cần sửa thông tin nghiệp vụ.
- Không có trường hợp tự bổ sung ngày bàn giao, chi phí hoặc kết luận kỹ thuật thiếu căn cứ.
- Mọi trường hợp đều cần người duyệt trước khi gửi.
- Tình huống thiếu hoặc mâu thuẫn dữ liệu phải được nhận diện và xử lý phù hợp.


## 7. EVALUATE 

| Câu hỏi | Trạng thái hiện tại | Việc cần bổ sung |
|---|---|---|
| Có sẵn dữ liệu mẫu/logs sạch để kiểm thử? | Chưa; mới có kế hoạch tạo dữ liệu mô phỏng. | Tạo bộ hồ sơ, đáp án tham chiếu và kiểm tra chất lượng dữ liệu. |
| Rủi ro khi AI sai nằm trong tầm kiểm soát? | Đã đề xuất giới hạn, người duyệt và fallback; chưa kiểm chứng. | Thử các tình huống sai, thiếu dữ liệu và vượt giới hạn. |
| Người sử dụng sẵn sàng thay đổi quy trình? | Chưa xác nhận. | Trao đổi với cố vấn dịch vụ và kỹ thuật viên. |

**Quyết định hiện tại: NOT YET.**

Chưa đủ căn cứ để triển khai trong vận hành thực tế. Cần xác minh quy trình, đo baseline, chuẩn bị dữ liệu, thử nghiệm và lấy ý kiến người sử dụng.

Có thể tiếp tục xây dựng bản mẫu học tập với dữ liệu mô phỏng để kiểm tra giả thuyết. Quyết định sẽ được cập nhật theo bằng chứng, bao gồm khả năng chọn rule hoặc mẫu trả lời cố định nếu giải quyết bài toán tốt hơn.