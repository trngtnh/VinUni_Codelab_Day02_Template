# 📝 Phase 6 — REFLECTION (Cá nhân)

Tôi nhìn lại bài lab qua ba quyết định: chọn phần việc đủ cụ thể để phân tích, xác định đúng nguyên nhân của một kết quả chưa đạt và giới hạn kết luận theo những gì đã kiểm chứng. Trong các bước đó, tôi sử dụng AI để trao đổi phương án, đặt lại câu hỏi và hỗ trợ đối chiếu thông tin.

## 1. Thu hẹp bài toán trước khi nghĩ đến giải pháp

Danh sách phản ánh ban đầu của tôi gồm nhiều vấn đề thuộc các dịch vụ khác nhau. Khi đưa chúng vào bài, khó khăn là tìm ra tác vụ có thể mô tả bằng một quy trình rõ ràng. Với VinFast, tôi tập trung vào việc cố vấn dịch vụ tổng hợp tình trạng sửa chữa và chuẩn bị nội dung cập nhật cho khách hàng.

Những trao đổi với AI giúp tôi xem xét ai thực hiện tác vụ, thông tin đi qua những bộ phận nào và bước nào có thể cần xử lý văn bản. Từ đó, tôi chọn phạm vi AI tạo bản nháp để cố vấn kiểm tra. Trạng thái kỹ thuật, ngày bàn giao và các quyết định về bảo hành vẫn phải có người phụ trách xác nhận.

Việc đọc nguồn khiến tôi phải điều chỉnh cách diễn giải. Trong trường hợp HASC Hoàng Mai, những lần liên hệ sau khi nhận xe chủ yếu liên quan đến khoản hỗ trợ cam kết sửa chữa. Nếu chỉ đọc phần tóm tắt, tôi có thể gộp chúng thành việc hỏi tiến độ sửa xe. Tôi bổ sung nội dung bài đăng và phản hồi để giữ đúng diễn biến.

Tương tự, một workflow do AI gợi ý có thể hợp lý về mặt trình tự nhưng vẫn cần được xác minh. Tôi giữ các mốc thời gian trong bài dưới dạng giả định mô phỏng. Chưa có số đo thao tác thực tế thì chưa thể xem chúng là baseline của doanh nghiệp.

## 2. Xem lại ý nghĩa của từng lần “Failed”

Trong quá trình chạy thử, tôi từng thấy dòng kiểm tra key báo OK nhưng yêu cầu API vẫn thất bại. Sau khi kiểm tra thêm, có lần chương trình chỉ nhận được một ký tự khi nhập key ẩn. Tôi dùng hướng dẫn kiểm tra từ AI để rà soát từng khả năng và nạp lại key từ clipboard. Trải nghiệm này giúp tôi hiểu rằng mỗi phép kiểm tra chỉ xác nhận một điều kiện cụ thể; biến có giá trị chưa chứng minh API đã chấp nhận key đó.

Khi prototype VinFast trả kết quả 17/20, tôi tiếp tục đối chiếu từng case thay vì chỉ nhìn tổng điểm. AI hỗ trợ phân tích log và so sánh output với yêu cầu đã đặt ra. Hai trường hợp cho thấy nguyên nhân khác nhau.

Ở DEMO-008, trường metadata đã ghi thiếu ETA, nhưng bản nháp dành cho khách chỉ nêu trạng thái sửa chữa. Thông tin quan trọng chưa xuất hiện ở nơi người nhận cần đọc. Yêu cầu trong prompt được làm rõ để khi thiếu ETA, draft_message phải có câu “Ngày bàn giao chưa được xác nhận.”

Ở DEMO-017, nội dung trạng thái phù hợp với hồ sơ nhưng viết thường, trong khi phép so khớp đang phân biệt hoa/thường. Trường hợp này cần sửa cách kiểm tra để chấp nhận khác biệt hình thức, đồng thời giữ yêu cầu về nội dung và căn cứ. Phần đối chiếu được chuẩn hóa Unicode, khoảng trắng và hoa/thường; các kiểm tra về nguồn, ngày/tiền thiếu căn cứ và người duyệt tiếp tục được giữ.

Qua hai case, tôi thấy một kết quả chưa đạt cần được đọc cùng input, output và điều kiện kiểm tra. Việc tham khảo AI hữu ích khi giúp tách các khả năng và đưa ra hướng kiểm chứng. Những nhận định sau đó vẫn cần được đối chiếu với log thực tế.

## 3. Giữ kết luận trong phạm vi đã thử nghiệm

Các lần chạy sử dụng gemini-3.5-flash-lite. Bài mẫu Xanh SM đạt 3/3 boundary tests. Với VinFast, kết quả tăng từ 17/20 ở lần đầu lên 19/20 ở lần hồi quy thứ hai; bản điều chỉnh cũng vượt qua 11 kiểm tra hồi quy offline. Autograder nguyên bản đạt 10/10.

Tôi giữ con số 19/20 trong bài. Ở lần chạy thứ hai, 13 nháp vượt validator, 6 trường hợp được rule chuyển xử lý thủ công trước khi gọi mô hình và một trường hợp gặp lỗi API 503. Vì vậy, kết quả này cần được mô tả là tỷ lệ đạt của pipeline kiểm tra tự động. Nó chưa đủ để kết luận LLM có độ chính xác nghiệp vụ 95%.

Tôi cũng phân biệt kết quả hồi quy với đánh giá độc lập. Sau khi output của bộ 20 case được dùng để điều chỉnh prompt và validator, lần chạy lại cho biết các thay đổi hoạt động thế nào trên bộ dữ liệu đã xem. Muốn mở rộng kết luận, cần dữ liệu mới và sự đánh giá của người hiểu nghiệp vụ.

Điều tôi muốn duy trì trong những lần sử dụng AI tiếp theo là thói quen yêu cầu làm rõ căn cứ: nhận định nào đến từ nguồn, phần nào là giả định và kết quả nào đã được đo. Với bài lab này, phạm vi prototype đã có bằng chứng chạy thực tế, còn mục tiêu giảm thời gian thao tác và khả năng áp dụng tại xưởng vẫn cần kiểm chứng. Đó là cơ sở để tôi giữ quyết định NOT YET đối với triển khai vận hành.
