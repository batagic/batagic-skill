# Prompt / instruction mẫu theo loại bài

Agent đọc file này khi cần chi tiết theo loại deck. Áp dụng như **instruction nội bộ**, không cần “prompt lại chính mình” trừ khi user muốn copy sang tool khác.

---

## Storyline trước (mọi loại)

Dựng STORYLINE theo khung đã chọn:

- Danh sách slide; mỗi slide 1 tiêu đề dạng **câu kết luận**
- Ý chính (bullet) từng slide
- CHƯA thiết kế chi tiết — chỉ khung
- Thiếu dữ liệu → hỏi / `[CẦN BỔ SUNG]`, không bịa

Input cần có: chủ đề, đối tượng, mục tiêu, thời lượng/~số slide, tông giọng, dữ liệu thô, theme.

---

## Báo cáo kết quả (Pyramid)

- Kết luận quan trọng nhất lên đầu mỗi phần
- Mỗi slide: tiêu đề = câu kết luận có số liệu; 3–5 bullet ngắn
- Đề xuất loại biểu đồ (cột/đường/tròn) + mô tả trục cho từng số liệu
- Thêm 1 slide **Điểm nổi bật** và 1 slide **Bước tiếp theo**
- Chỉ dùng dữ liệu user đưa; thiếu → `[CẦN BỔ SUNG]`

---

## Pitch deck (Before–After–Bridge)

Cấu trúc gợi ý (~N slide): Vấn đề → Giải pháp → Thị trường → Sản phẩm → Mô hình kinh doanh → Lợi thế cạnh tranh → Traction → Đội ngũ → Kêu gọi đầu tư.

- Mỗi slide 1 thông điệp mạnh; ngôn ngữ tự tin, hướng lợi ích
- Slide đầu: HOOK ~10 giây
- Traction chỉ dùng số liệu user
- Slide cuối: số tiền / yêu cầu + dùng tiền vào việc gì

---

## Đào tạo (What–Why–How)

- Mở bằng câu hỏi / tình huống thực tế
- Mỗi khái niệm: định nghĩa ngắn + ví dụ đời thực + gợi ý hình minh họa
- Slide **Kiểm tra nhanh** sau mỗi 3–4 slide
- Kết: 3 điều cần nhớ + bài tập áp dụng
- Ngôn ngữ đơn giản; thuật ngữ phải giải thích

---

## Tinh chỉnh sau bản nháp

1. Rút gọn slide vi phạm 6×6
2. Đổi tiêu đề chung chung → câu kết luận
3. Chỉ ra slide yếu/thừa; đề xuất cắt hoặc gộp
4. Kiểm tra mạch chuyển slide
5. Liệt kê mọi số liệu để user đối chiếu nguồn

---

## Bản copy-paste (khi user mang sang Gamma / ChatGPT / Copilot)

### Khởi tạo storyline

```
Bạn là chuyên gia thiết kế bài thuyết trình.
Chủ đề: [chủ đề]
Đối tượng nghe: [ai]
Mục tiêu: [thuyết phục / báo cáo / đào tạo]
Thời lượng: [X] phút (~[X] slide)
Tông giọng: [trang trọng / thân thiện...]
Dữ liệu: [dán số liệu / tài liệu]

Dựng STORYLINE theo khung [SCQA / Pyramid / ...]:
- Danh sách slide, tiêu đề = CÂU KẾT LUẬN
- Ý chính từng slide
- CHƯA thiết kế chi tiết
Nếu thiếu dữ liệu, HỎI thay vì bịa.
```

### Báo cáo

```
Dựa trên storyline đã chốt, viết nội dung BÁO CÁO KẾT QUẢ.
- Pyramid: kết luận trước
- Tiêu đề = câu kết luận có số liệu; 3–5 bullet
- Đề xuất biểu đồ + trục
- Thêm "Điểm nổi bật" + "Bước tiếp theo"
- Không bịa số; [CẦN BỔ SUNG] nếu thiếu
```

### Pitch

```
Viết PITCH DECK theo Before–After–Bridge, [N] slide.
Vấn đề → Giải pháp → Thị trường → Sản phẩm → Mô hình → Lợi thế → Traction → Đội ngũ → Kêu gọi.
Hook 10 giây; traction = [số liệu]; cuối = số gọi vốn + use of funds.
```

### Đào tạo

```
SLIDE ĐÀO TẠO chủ đề [X] cho [đối tượng], [N] slide. What–Why–How.
Hook tình huống; định nghĩa + ví dụ; quiz mỗi 3–4 slide; kết 3 điểm nhớ + bài tập.
```
