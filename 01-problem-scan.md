# 01 — Problem Scan

- Tên nhóm: AI20K-Group
- Người thực hiện: Trần Đăng Khoa
- Email: 26ai.khoatd2@vinuni.edu.vn
- Nhánh cá nhân: khoa_2k3

## 1. Khảo sát 5 bài toán


| STT | Đơn vị  | Góc nhìn      | Vấn đề cần tìm hiểu |
|---|---|---|---|
| 1   | VinFast | Tốn thời gian | Cố vấn dịch vụ phải đọc hồ sơ và hỏi kỹ thuật viên để cập nhật tình trạng sửa chữa cho khách. |
| 2   | Vinhomes | Lặp lại      | Nhân viên phải đọc và phân loại các phản ánh của cư dân để chuyển đúng bộ phận. |
| 3   | VinWonders | AI có thể hỗ trợ tốt hơn | Nhân viên cần tra cứu thông tin để trả lời câu hỏi về tiện ích, lịch hoạt động và dịch vụ. |
| 4   | Xanh SM | Tốn thời gian | Nhân viên vận hành phải đọc ghi chú để tổng hợp nguyên nhân hủy chuyến. |
| 5   | Vinmec | Khó khăn của người sử dụng | Khách quốc tế cần được hướng dẫn thông tin hành chính và quy trình đặt lịch bằng ngôn ngữ phù hợp. |

## 2. Ba bài toán được chọn để đánh giá tiếp

1. VinFast: Hỗ trợ cập nhật tình trạng sửa chữa.
2. Vinhomes: Hỗ trợ phân loại phản ánh của cư dân.
3. VinWonders: Hỗ trợ tra cứu và soạn câu trả lời cho du khách.

## 3. VinFast

Bài toán: Hỗ trợ cố vấn dịch vụ tổng hợp thông tin và soạn cập nhật tình trạng sửa chữa cho khách hàng.

Đơn vị: VinFast.

Ai đang gặp khó khăn?
- Cố vấn dịch vụ phải tìm và tổng hợp thông tin trước khi trả lời.
- Khách hàng cần biết tình trạng xe và thông tin nào còn chờ xác nhận.

Quy trình hiện tại:
1. Cố vấn nhận câu hỏi và xác định mã phiếu sửa chữa.
2. Đọc hồ sơ, lịch sử sửa chữa và ghi chú.
3. Hỏi kỹ thuật viên để xác nhận trạng thái còn thiếu.
4. Soạn câu trả lời cho khách hàng.
5. Kiểm tra và gửi phản hồi.

Điểm nghẽn: Đọc và tổng hợp hồ sơ, soạn phản hồi, kiểm tra trước khi gửi. Giả định tổng thời gian thao tác của các công việc này là 6 phút/yêu cầu; chưa tính thời gian chờ kỹ thuật viên xác nhận.

AI hỗ trợ ở đâu? Tóm tắt ghi chú được cung cấp và soạn phản hồi nháp dựa trên thông tin đã xác nhận.

Mục tiêu đo lường:
- Giảm thời gian tổng hợp, soạn và duyệt từ mức có thể 6 phút xuống tối đa 3 phút/yêu cầu.
- Ít nhất 18/20 bản nháp trong bộ thử nghiệm được người đánh giá chấp nhận mà không cần sửa thông tin nghiệp vụ.
- Không có trường hợp tự bịa ngày giao xe, chi phí hoặc kết luận kỹ thuật.


Lựa chọn giải pháp: LLM Feature kết hợp quy tắc kiểm tra dữ liệu.

Giới hạn: AI chỉ tạo bản nháp. Cố vấn kiểm tra trước khi gửi; thiếu dữ liệu thì yêu cầu xác nhận thêm. AI không tự chẩn đoán hoặc quyết định bảo hành.

## 4. Vinhomes

Bài toán: Hỗ trợ nhân viên phân loại phản ánh của cư dân để chuyển đúng bộ phận phụ trách.

Đơn vị: Vinhomes.

Ai đang gặp khó khăn? Nhân viên tiếp nhận phản ánh và cư dân đang chờ được hỗ trợ.

Quy trình hiện tại:
1. Nhân viên nhận phản ánh.
2. Đọc nội dung và xác định loại vấn đề.
3. Kiểm tra thông tin còn thiếu.
4. Chọn bộ phận phụ trách và chuyển yêu cầu.
5. Ghi nhận trạng thái để theo dõi.

Điểm nghẽn: Đọc phản ánh, kiểm tra thông tin, phân loại và duyệt bộ phận tiếp nhận. Giả định tổng thời gian thao tác là 4 phút/yêu cầu.

AI hỗ trợ ở đâu? Đề xuất nhóm vấn đề, bộ phận nhận và thông tin cần hỏi thêm, kèm trích đoạn làm căn cứ.

Mục tiêu đo lường:
- Giảm thời gian phân loại và duyệt từ mức có thể 4 phút xuống tối đa 2 phút/yêu cầu.
- Đạt ít nhất 18/20 trường hợp phân loại đúng trên bộ dữ liệu thử có đáp án được người đánh giá xác nhận.


Lựa chọn giải pháp: Rule kết hợp LLM Feature. Biểu mẫu có loại vấn đề rõ ràng có thể dùng rule; LLM hỗ trợ nội dung tự do hoặc nhiều ý.

Giới hạn: AI chỉ đề xuất phân loại, nhân viên duyệt trước khi chuyển. Nội dung thiếu hoặc mâu thuẫn phải chuyển người kiểm tra. Không tự quyết định phí, bồi thường hoặc kết luận tranh chấp.

## 5. VinWonders

Bài toán: Hỗ trợ nhân viên tra cứu và soạn câu trả lời cho du khách về tiện ích, lịch hoạt động và dịch vụ.

Đơn vị: VinWonders.

Ai đang gặp khó khăn? Nhân viên quầy thông tin và du khách cần câu trả lời rõ ràng, kịp thời.

Quy trình hiện tại:
1. Nhân viên nhận câu hỏi.
2. Xác định khu vui chơi và ngày khách dự định sử dụng dịch vụ.
3. Tra cứu tài liệu, bản đồ hoặc thông báo đang có hiệu lực.
4. Soạn câu trả lời.
5. Kiểm tra và trả lời khách.

Điểm nghẽn: Tra cứu tài liệu, soạn câu trả lời và kiểm tra trước khi trả lời khách. Giả định tổng thời gian thao tác là 6 phút/câu hỏi.

AI hỗ trợ ở đâu? Tổng hợp thông tin từ tài liệu chính thức được cung cấp và soạn câu trả lời nháp có dẫn nguồn.

Mục tiêu đo lường:
- Giảm thời gian tra cứu, soạn và duyệt từ mức 6 phút xuống tối đa 3 phút/câu hỏi.
- Ít nhất 18/20 câu trả lời thử nghiệm đúng và đủ theo tài liệu.
- Mọi thông tin về giá hoặc lịch hoạt động trong bản nháp đều có nguồn còn hiệu lực.


Lựa chọn giải pháp: LLM Feature có tra cứu tài liệu. Với câu hỏi cố định và dữ liệu có cấu trúc, ưu tiên tra cứu hoặc mẫu trả lời bằng rule.

Giới hạn: Không tự bịa giá, lịch hoặc ưu đãi. Nếu tài liệu thiếu, hết hiệu lực hoặc mâu thuẫn, yêu cầu nhân viên xác minh trước khi trả lời.

## 6. Đề xuất bài toán để phân tích sâu

Em đề xuất chọn "VinFast — Hỗ trợ cập nhật tình trạng sửa chữa" vì:
- Tác vụ có đầu vào và đầu ra cụ thể: hồ sơ, ghi chú đã xác nhận → bản nháp cập nhật.
- Người duyệt có thể đối chiếu bản nháp với hồ sơ.
- Có thể thử nghiệm bằng dữ liệu mô phỏng, không cần kết nối hệ thống doanh nghiệp.
- Có thể so sánh AI với phương án mẫu trả lời cố định để đánh giá giá trị bổ sung.
