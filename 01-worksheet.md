# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

## 🏛️ 1. Bối cảnh thực tế: Vin Smart Future (Vingroup)

**Vingroup** — Tập đoàn tư nhân lớn nhất Việt Nam — vừa sáp nhập toàn bộ các phòng ban công nghệ thuộc các công ty thành viên thành một đơn vị công nghệ thống nhất mang tên **Vin Smart Future**. 

Nhiệm vụ của **Vin Smart Future** là xây dựng các giải pháp AI, số hóa, và tự động hóa cốt lõi để nâng cao hiệu suất vận hành và trải nghiệm khách hàng xuyên suốt các công ty thành viên:
* 🚗 **VinFast:** Hệ thống xe điện thông minh (EV), trợ lý AI ảo trong xe, dự đoán bảo trì pin, và quản lý chuỗi cung ứng sản xuất.
* 🚕 **Xanh SM (GSM):** Vận hành đội xe taxi/xe máy điện thông minh, điều vận thông minh (Smart Dispatching), tối ưu hóa lộ trình di chuyển.
* 🏢 **Vinhomes:** Quản lý đô thị thông minh (Smart Cities), trợ lý cư dân thông minh, tối ưu hóa mức tiêu thụ năng lượng.
* 🏥 **Vinmec:** Y tế thông minh, chẩn đoán hình ảnh bằng AI, tối ưu hóa quản lý hồ sơ bệnh án.
* 🎢 **Vinpearl / VinWonders:** Trải nghiệm du lịch số hóa, quản lý phòng và luồng khách thông minh tại các khu vui chơi.

Trong buổi Lab hôm nay, nhóm của bạn sẽ đóng vai trò là **AI Product Engineer** tại **Vin Smart Future**, tiến hành tìm kiếm, scoping, phân tích độ khả thi, thiết lập ranh giới vận hành, và xây dựng một **bản mẫu kỹ thuật (prompt prototype)** cho một bài toán cụ thể thuộc một trong những mảng kinh doanh trên.

---

## 📊 2. Cơ cấu tính điểm bài lab

### 👥 Điểm nhóm (60 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **G1. Workflow Mapping** | 20 | Problem Deep-Dive | Vẽ chi tiết quy trình hiện tại: các bước, handoff, thời gian, bottleneck |
| **G2. Problem Statement** | 20 | Problem Deep-Dive | Problem Statement 6-field bám sát thực tế, metric có số và ranh giới rõ ràng |
| **G3. AI Fit & Future Flow** | 10 | Problem Deep-Dive | So sánh Rule vs LLM vs Agent, future flow có bước AI, ranh giới và Fallback |
| **G4. Decision Quality** | 10 | Problem Deep-Dive | Quyết định Go/Not Yet/No-Go trung thực và có chứng cứ rõ ràng |

### 👤 Điểm cá nhân (40 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **I1. Scan & Cards** | 15 | Quick Cards | Liệt kê 5 problems sử dụng 3 lenses, hoàn thiện 3 quick cards chất lượng |
| **I2. Prototyping** | 10 | 02-lab/ | Chạy thử nghiệm programmatic prompt prototype thành công |
| **I3. AI Log & Reflection** | 15 | 03-ai-log.md | Phản ánh trung thực về việc dùng AI làm thought-partner (giúp gì, sai gì, sửa gì) |

---

# 🚀 Phase 0 — worked Example: Xanh SM Intelligent Dispatcher (15 min)

*Giảng viên walk-through ví dụ thực tế từ Vin Smart Future để bạn hiểu rõ cách scoping một bài toán AI.*
Đọc chi tiết worked example tại file [02-deliverable-example.md](02-deliverable-example.md).

---

# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Tất cả P&L | Lặp lại | Khảo sát nguyện vọng các CBNV, trình Giám đốc phê duyệt, cập nhật các hệ thống kiểm soát nhân sự liên quan **cho các ngày nghỉ lễ** |
| 2 | VinBus | Tốn thời gian | Phản ứng trước sự kiện xuất hiện công trình thi công trên tuyến đường mà xe buýt thuộc tuyến VinBus vận hành đang chạy |
| 3 | VinBus | AI có thể tốt hơn | Xác tình trạng giao thông gây detour nghiêm trọng xảy ra trên tuyến bus mà VinBus vận hành |
| 4 | VinBus | Tốn thời gian | Xử lý yêu cầu tìm đồ thất lạc trên xe |
| 5 | VinCons | Lặp lại | Thẩm định, phân luồng hồ sơ ứng viên thợ hồ |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

## Quick Problem Card #1: Nghỉ lễ

**Bài toán**: Tự động hóa quy trình khảo sát nguyện vọng nghỉ lễ của CBNV, tổng hợp kết quả, trình phê duyệt và cập nhật dữ liệu lên các hệ thống nhân sự liên quan.

**Công ty thành viên**: Tất cả P&L

**Ai đang đau (Actor)?**
- Bộ phận Hành chính & Nhân sự (HR) tại các P&L: các tác vụ này phải làm đi làm lại mỗi khi sát kỳ nghỉ lễ
- CBNV của các P&L: không biết trước được lịch nghỉ để sắp xếp đi chơi & công việc cá nhân
- Đối tác & Khách hàng: Khó sắp xếp các tác vụ dài khi không biết lịch nghỉ lễ, đặc biệt với các đối tác nước ngoài

**Workflow thủ công hiện tại:**
1. HR nhận thông tin sắp xếp ngày nghỉ lễ từ Bộ Nội vụ, hoặc bắt tay thực hiện trước đó khoảng 3-4 tháng.
2. Lên các phương án nghỉ lễ theo khuyến nghị của Bộ Nội vụ hoặc tự lên.
1. HR gửi thông báo và khảo sát nguyện vọng nghỉ lễ.
2. CBNV phản hồi nguyện vọng.
3. HR tổng hợp, kiểm tra và xử lý các trường hợp ngoại lệ.
4. Trình Giám đốc phê duyệt phương án nghỉ (dựa trên 3 thông tin: phương án phù hợp; nguyện vọng CBNV; tác động lên các bộ phận), sau đó Giám đốc thực hiện phê duyệt
5. Cập nhật lịch nghỉ lên các hệ thống kiểm soát nhân sự liên quan: chấm công
6. Thông báo cho các bên hữu quan chịu ảnh hưởng: khách hàng, đối tác,...

**Bước tốn thời gian/lỗi nhất:** Tổng hợp dữ liệu, lập tờ trình, cập nhật dữ liệu trên nhiều hệ thống và thông báo cho đầy đủ các bên hữu quan.

**AI có thể hỗ trợ:**
- Đọc feed tin tức, phát hiện thông báo của Bộ Nội vụ về ngày nghỉ lễ
- Soạn các phương án nghỉ lễ, lập tờ trình.
- Tổng hợp nguyện vọng người lao động, chỉ ra một số xu hướng chính (phòng ban này cần on-site, đối tác đang trong thời gian làm việc chủ chốt (critical))
- Sau phê duyệt, gọi API hoặc hỗ trợ nhập dữ liệu vào hệ thống nhân sự.

**Metric đo thành công:**
- Phương án nghỉ lễ được chốt và thông báo trước tối thiểu 1 tháng đối với kỳ nghỉ < 5 ngày, 3-6 tháng với kỳ nghỉ ≥ 5 ngày (metric có thể thay đổi tùy vào chính sách từng P&L)
- Không xảy ra tình trạng đối tác phản hồi rằng không biết lịch nghỉ lễ (có thể bỏ qua cho khách hàng vì khách hàng không trực tiếp làm việc, khó nắm thời gian nghỉ một cách trực tiếp)
- Không để xảy ra tình trạng thiếu nhân sự trực on-site trong các ngày nghỉ lễ

**Quick Architecture:** LLM + Agent

## Quick Problem Card #2: Detour tuyến buýt do thi công

**Bài toán**: Tự động hóa việc tiếp nhận, xác minh và đánh giá ảnh hưởng của các công trình thi công đến mạng lưới xe buýt VinBus, từ đó hỗ trợ nhân viên điều hành nhanh chóng xác định tuyến, đoạn đường và điểm dừng bị ảnh hưởng, đồng thời cung cấp cơ sở để lựa chọn phương án ứng phó.

**Công ty thành viên**: VinBus

**Ai đang đau (Actor)?**
- **Nhân viên điều hành vận tải**: Mất thời gian thu thập thông tin từ nhiều nguồn, xác minh vị trí và đối chiếu thủ công với dữ liệu tuyến buýt.
- **Bộ phận quản lý tuyến và lái xe**: Tiếp nhận thông tin ảnh hưởng chậm hoặc thiếu chính xác, dẫn đến khó chủ động điều chỉnh hoạt động.
- **Hành khách**: Có thể không được thông báo kịp thời về thay đổi lộ trình, điểm dừng hoặc thời gian di chuyển.

**Workflow thủ công hiện tại:**
1. Tiếp nhận thông tin công trình từ lái xe, cơ quan chức năng hoặc nguồn tin giao thông.
2. Xác minh vị trí, thời gian và phạm vi thi công.
3. Đối chiếu vị trí công trình với các tuyến xe buýt đang vận hành.
4. Đánh giá ảnh hưởng và trao đổi với các bộ phận liên quan.
5. Đề xuất điều chỉnh lộ trình, điểm dừng hoặc phương án điều hành; thông báo cho các bên.

**Bước tốn thời gian/lỗi nhất:** Xác minh thông tin và xác định tuyến/đoạn đường bị ảnh hưởng; thông báo cho các tài xế và hành khách

**AI có thể hỗ trợ:**
- **LLM – Tiếp nhận và chuẩn hóa thông tin**: Đọc thông báo thi công, tin tức, email và phản ánh hiện trường; trích xuất địa điểm, thời gian, phạm vi thi công, loại hạn chế giao thông và nguồn tin.
- **Geocoding/GIS – Xác định vị trí và ảnh hưởng không gian**: Chuyển địa điểm thành tọa độ hoặc đoạn đường; đối chiếu vùng thi công với hình học tuyến, chiều tuyến và vị trí điểm dừng.
- **Rule engine – Đánh giá ảnh hưởng vận hành**: Đối chiếu thời gian thi công với lịch hoạt động, xác định tuyến và chuyến có khả năng bị ảnh hưởng, phân loại mức độ ảnh hưởng.
- **Routing/Optimization – Hỗ trợ phương án ứng phó**: Tìm các tuyến đường thay thế và kiểm tra các ràng buộc như chiều dài, tải trọng, chiều cao, hạn chế rẽ, khả năng tiếp cận điểm dừng và thời gian hành trình.
- **LLM – Tổng hợp và giao tiếp**: Tạo báo cáo ảnh hưởng, giải thích kết quả đối chiếu và soạn thông báo phù hợp cho nhân viên điều hành, lái xe và hành khách.
- **Workflow/API – Thực thi**: Chuyển kết quả đã được phê duyệt đến hệ thống điều hành và các kênh thông báo liên quan.

**Metric đo thành công:**
- Giảm ít nhất 50% thời gian từ khi tiếp nhận thông tin đến khi xác định danh sách tuyến có khả năng bị ảnh hưởng, so với baseline.
- Ít nhất 90% sự kiện có đủ dữ liệu đầu vào được chuẩn hóa và đưa ra kết quả đối chiếu trong vòng 5 phút.
- Ít nhất 90% sự kiện đủ dữ liệu có báo cáo đánh giá ảnh hưởng trong vòng 15 phút.
- Giảm thời gian từ khi xác minh sự kiện đến khi thông báo phương án đã được phê duyệt cho các bên liên quan.
- Theo dõi tỷ lệ thông báo được lái xe xác nhận và tỷ lệ phương án được triển khai đúng kế hoạch.

**Quick Architecture:** LLM + Agent + GIS/API (LLM đọc hiểu thông tin, Agent điều phối; GIS và dữ liệu tuyến thực hiện đối chiếu không gian).

# Quick Problem Card #3: Tìm kiếm và đối chiếu đồ thất lạc trên xe buýt

**Bài toán**

Xây dựng hệ thống hỗ trợ tiếp nhận, chuẩn hóa và đối chiếu yêu cầu tìm đồ thất lạc của hành khách với cơ sở dữ liệu đồ vật được nhân viên/lái xe ghi nhận trên các chuyến xe VinBus. Hệ thống tự động tìm kiếm và xếp hạng các đồ vật có khả năng trùng khớp, giúp nhân viên CSKH rút ngắn thời gian xác minh và xử lý yêu cầu.

**Công ty thành viên:** VinBus

**Ai đang đau (Actor)?**

- **Nhân viên chăm sóc khách hàng:** Mất thời gian tiếp nhận, tìm kiếm và đối chiếu thông tin từ nhiều nguồn; khó theo dõi trạng thái xử lý từng yêu cầu.
- **Nhân viên điều hành và lái xe:** Phải tra cứu hoặc xác minh thủ công các trường hợp đồ thất lạc giữa nhiều chuyến xe và ca vận hành.
- **Hành khách:** Không biết đồ vật có được tìm thấy hay không, phải chờ phản hồi và có thể phải liên hệ nhiều lần.

**Workflow thủ công hiện tại:**

1. Tiếp nhận yêu cầu từ hành khách: loại đồ vật, đặc điểm nhận dạng, thời gian, tuyến, chuyến xe và vị trí nghi ngờ làm thất lạc.
2. Tra cứu lịch trình và xác định các xe/chuyến có khả năng liên quan.
3. Tìm kiếm trong dữ liệu đồ vật được nhân viên/lái xe ghi nhận.
4. Liên hệ các bộ phận liên quan để xác minh những trường hợp có khả năng trùng khớp.
5. Xác minh quyền sở hữu và tình trạng lưu giữ đồ vật.
6. Thông báo kết quả, hướng dẫn hành khách nhận lại đồ và ghi nhận trạng thái xử lý.

**Bước tốn thời gian/lỗi nhất:**

- Tìm kiếm và đối chiếu giữa yêu cầu của hành khách và bản ghi đồ thất lạc có mô tả không thống nhất.
- Xác định chuyến xe và bộ phận có khả năng đang lưu giữ đồ vật.
- Theo dõi, phối hợp xác minh và cập nhật trạng thái xử lý giữa CSKH, điều hành và lái xe.

**AI có thể hỗ trợ:**

1. **LLM – Tiếp nhận và chuẩn hóa yêu cầu:** Đọc mô tả tự do của hành khách, trích xuất loại đồ vật, màu sắc, thương hiệu, đặc điểm nhận dạng, thời gian và thông tin chuyến xe.
2. **LLM + AI Vision – Chuẩn hóa bản ghi đồ thất lạc:** Chuyển thông tin ghi nhận từ nhân viên/lái xe thành dữ liệu có cấu trúc; dựa vào hình ảnh hỗ trợ bổ sung các trường thông tin còn thiếu.
3. **Search & Matching – Tìm kiếm ứng viên:** Kết hợp lọc dữ liệu theo tuyến, chuyến, thời gian với tìm kiếm tương đồng theo mô tả và hình ảnh.
4. **Ranking – Xếp hạng kết quả:** Đánh giá mức độ tương đồng giữa yêu cầu và các bản ghi; hiển thị danh sách ứng viên kèm lý do khớp và thông tin còn thiếu.
5. **LLM – Hỗ trợ giao tiếp:** Soạn phản hồi cho hành khách, yêu cầu bổ sung thông tin và hướng dẫn quy trình nhận lại đồ.

**Metric đo thành công:**
*Độ chính xác tìm kiếm*
- Trong 5 kết quả gợi ý đầu tiên, tỷ lệ kết quả thực sự liên quan đạt ít nhất 80%.
- Theo dõi riêng tỷ lệ ghép nhầm đồ vật và tỷ lệ bỏ sót đồ vật có trong cơ sở dữ liệu.

*Hiệu quả xử lý yêu cầu*
- Tăng tỷ lệ yêu cầu được tìm thấy đồ vật và xác nhận bàn giao thành công.
- Tăng tỷ lệ đồ vật được ghi nhận đầy đủ vào hệ thống.
- Giảm tỷ lệ yêu cầu phải đóng mà không xác định được kết quả do thiếu thông tin hoặc thất lạc dữ liệu.

**Quick Architecture:**

**LLM + Search/Matching Engine + Database + Workflow/API + Human-in-the-loop**

- **LLM:** Tiếp nhận, trích xuất và chuẩn hóa mô tả đồ vật từ ngôn ngữ tự nhiên.
- **Database/Search:** Lọc theo tuyến, chuyến, thời gian và tìm kiếm tương đồng theo mô tả.
- **Image matching (tùy chọn):** Sử dụng mô hình xử lý ảnh/embedding để hỗ trợ so khớp hình ảnh.
- **Ranking engine:** Xếp hạng các ứng viên và giải thích các đặc điểm trùng khớp.
- **Human-in-the-loop:** Nhân viên xác minh đồ vật và quyền sở hữu trước khi bàn giao.
- **Workflow/API:** Theo dõi trạng thái, phân công xử lý, thông báo và ghi nhận bàn giao.

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.

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

## 3.3. Future-State Flow & AI Fit (25 min)
* **Xác định mức AI Fit (AI-Fit Matrix):** Giải pháp thuộc nhóm nào? [ ] Rule / State-Machine [ ] LLM Feature [ ] Agentic Loop.
* **Vẽ Future-State Flow:** Đánh dấu rõ:
  * 🔵 **AI Step:** Tác vụ LLM xử lý.
  * 🟢 **Human Step (HITL):** Bước con người phê duyệt/review (Human-in-the-loop).
  * ↩️ **Fallback:** Kế hoạch dự phòng khi LLM trả về kết quả lỗi hoặc không tự tin.

---

# 💻 Phase 4 — TECHNICAL PROMPT PROTOTYPE (Nhóm, 30 min)

Để đảm bảo kỹ sư của Vin Smart Future luôn giữ vững năng lực lập trình, nhóm của bạn sẽ tiến hành **lập trình bản mẫu prompt** trực tiếp trên **Gemini 2.5 Flash** bằng Python để stress-test hệ thống.

### Hướng dẫn thực hiện:
1. Mở file [starter-code/prompt_prototype.py](starter-code/prompt_prototype.py) bằng VS Code/Cursor.
2. Hoàn thiện các nội dung sau:
   * **System Prompt:** Viết chỉ thị cực kỳ nghiêm ngặt quy định vai trò, nhiệm vụ, định dạng output và **Operational Boundary (Ranh giới cấm)** của mô hình.
   * **Structured Output:** Định nghĩa định dạng JSON output rõ ràng.
   * **Adversarial Test Cases:** Viết ít nhất 3 prompts "tấn công" (Adversarial inputs) cố tình dụ AI vượt ranh giới hoặc đưa ra câu trả lời không được phép để kiểm tra xem ranh giới của bạn có thực sự vững chắc.
3. Chạy file python:
   ```bash
   python3 prompt_prototype.py
   ```
4. Kiểm tra xem các ranh giới an toàn có bị LLM phá vỡ hay không và ghi lại kết quả vào worksheet.

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

# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân bạn về việc phối hợp với AI trong buổi học hôm nay vào file `03-ai-log.md`.*
