# Prototype — T2 Giáo dục · Nhóm AIS (ca K1 & K6)

## §5. Prototype

- **File:** `prototype/index.html` (một file HTML + JS thuần, mở trực tiếp bằng trình duyệt, không cần backend hay đăng nhập).
- **Công cụ:** HTML/CSS/JS thuần, dựng bằng coding agent.
- **Lời gọi AI thật:** không có. Toàn bộ câu chữ AI lấy nguyên văn từ `spec.md` §3–§4.

### Phần được mô phỏng
- **Đồng hồ & ca trực TA:** mặc định `22:30 · 13/11/2026` (ngoài giờ TA 08:00–22:00); khi chuyển TA báo dự kiến từ `08:00 ngày 14/11`. Khi bấm **TA gửi trả lời (08:05 · 14/11)** ở bảng điều phối TA, đồng hồ chuyển sang `08:05 · 14/11/2026 (Trong ca trực TA)`, phản hồi TA hiện lên khung chat và mục **§3.3** bên cột tài liệu được chính TA/giảng viên cập nhật.
- **Tra cứu tài liệu (`tra_cuu_tai_lieu`):** đoạn trích §3.1–§3.5 và trạng thái Bài tập 3 đang mở (hạn 13/11/2026 23:59) được dựng sẵn từ Dữ liệu A & B của track T2.
- **Hàng chờ phía TA (`chuyen_TA` & `goi_y_bai_tap`):** bấm Xác nhận gửi thêm mục vào tab **Câu hỏi chuyển lên** ngay trên trang để TA trả lời khi đến ca trực. Tab thứ hai mô phỏng một bản nháp `soan_goi_y_bai_tap` cho K5 chờ TA bấm **Duyệt gửi** hoặc **Từ chối**.
- **Tin nhắn người học:** chọn từ 3 ca dựng sẵn (**K1**, **K6**, **Ca bình thường**), tắt ô nhập tự do.

### Luồng bấm thử (khớp §3–§4)
- **Luồng chính (K1 — ca demo):** chọn K1 → AI tự tra §3.3 (không hỏi) → hiện nhãn *"Tài liệu có điểm cần kiểm tra"*, tô vàng câu *"luôn nhỏ hơn"*, hiện phép tính phản ví dụ `0,25 → 0,5` → chọn **Gửi cho TA** / **Sửa nội dung** / **Để sau** → ở thẻ xem trước có thể sửa nội dung, bấm **Hủy** (không gửi gì, giữ bản nháp để mở lại) hoặc **Xác nhận gửi** → vào hàng chờ TA và báo ETA từ 08:00 ngày 14/11 → ở cột TA bên phải, chỉnh/duyệt câu trả lời mẫu và bấm **TA gửi trả lời (08:05 · 14/11)** để thấy phản hồi từ người thật và tài liệu §3.3 được cập nhật.
- **Đổi mức tự chủ của `chuyen_TA`:** thanh chọn trên đầu trang cho chuyển giữa ① Chỉ nhắc tự gửi, ② Cần người học duyệt *(mức nhóm AIS chọn)*, ③ AI tự gửi + hoàn tác 10 phút, kèm phần *"Lời hứa với người học ở mức này"* đổi theo.
- **Ca K6 (xin xác nhận đáp số 11,5):** hiện nhãn *"Bài tập 3 đang mở"*, từ chối xác nhận đúng/sai, dẫn §3.2 và đưa 3 nút **Giải thích cách tìm vị trí giữa**, **Hỏi TA** (qua thẻ duyệt trước khi gửi), **Bỏ qua** (G8).
- **Ca bình thường:** trả lời ngay từ §3.1–§3.2, không bắt chờ TA.
- **Việc bị cấm (`dang_FAQ`):** không có nút nào phía học viên và phía AI; khung TA ghi rõ AI không có quyền tự đăng FAQ.

### Ảnh có đánh số

- `prototype/luong-chinh.png` (`index.html#k1-preview`): bước AI trả lời K1 + thẻ xem trước gửi TA (① ② ③ ④).
- `prototype/hang-cho.png` (`index.html#k1-replied`): sau khi xác nhận gửi (⑤) và giả lập đến ca trực 08:05 ngày 14/11 — TA gửi trả lời trong khung chat và cập nhật sửa §3.3 bên cột tài liệu.

| Số | Thể hiện gì trên màn hình | Nguyên tắc HAX / PAIR | Mức tự chủ |
|---|---|---|---|
| ① | Nhãn *"Bạn đang trò chuyện với AI"* + câu *"Mình chưa sửa tài liệu hay gửi câu hỏi cho TA"* | **G1** (Làm rõ hệ thống làm được gì) · Luật AI 134/2025 Đ.11 | — |
| ② | Trạng thái *"Tài liệu có điểm cần kiểm tra"* + trích dẫn mở được **Mở §3.3**, tô vàng câu *"luôn nhỏ hơn"* | **G2** + **PAIR Explainability & Trust** | `tra_cuu_tai_lieu` · Tự làm (chỉ đọc) |
| ③ | Phép tính phản ví dụ `0,25 → √0,25 = 0,5` ngay dưới đoạn nguồn và trong câu trả lời | **G11** (Giải thích vì sao) | — |
| ④ | Nút **Gửi cho TA / Sửa nội dung / Để sau** + thẻ xem trước (ô sửa nội dung, **Xác nhận gửi**, **Hủy** giữ bản nháp) | **G8** (Gạt bỏ dễ) · **G9** (Sửa dễ) | `chuyen_TA` · Người học duyệt |
| ⑤ | Thông báo đã chuyển mã `TA-0317`, ETA từ 08:00 ngày 14/11 + thẻ tương ứng trong hàng chờ TA | **PAIR Errors + Graceful Failure** | — |
| ⑥ | *(Ở ca K6)* Nhãn *"Bài tập 3 đang mở"*, từ chối xác nhận đúng/sai, chỉ dẫn quy trình §3.2, nút **Bỏ qua** | **G10** (Thu hẹp khi nghi ngờ) · **G8** | `goi_y_bai_tap` · Không gửi khi chưa TA duyệt |

### Quyết định cách hiện
- **Độ chắc & bằng chứng:** hiển thị trạng thái chữ (*"Tài liệu có điểm cần kiểm tra"*) + trích dẫn mở được §3.3 tô vàng câu sai + phản ví dụ `0,25 → 0,5`, thay vì một con số `%` độ tin cậy. Loại `%` vì học viên không biết phần trăm nói lên sai chỗ nào để tự đối chiếu.
- **Điều khiển mức tự chủ:** chọn thẻ **xem trước có sửa/hủy** cho `chuyen_TA` làm mức mặc định, đồng thời thêm thanh chuyển 3 mức ở đầu trang (① tự gửi thủ công · ② người học duyệt · ③ AI tự gửi + hoàn tác) để trình diễn rõ phương án đã loại và sự thay đổi của lời hứa với người học.
- **Tách luồng gợi ý bài mở (`goi_y_bai_tap`):** đặt tab *Duyệt gợi ý* ở phía TA cho thấy bản nháp từ `soan_goi_y_bai_tap` bị giữ ở phía TA cho tới khi TA bấm **Duyệt gửi**, không đẩy thẳng cho học viên.
