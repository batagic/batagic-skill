---
name: ai-slides
description: >
  Quy trình chuẩn + bộ prompt tái sử dụng để dùng AI làm slide, báo cáo,
  PowerPoint chất lượng cao. Kích hoạt bằng /ai-slides hoặc khi user muốn tạo
  bài thuyết trình, pitch deck, báo cáo, tài liệu đào tạo, hoặc bất kỳ
  slide/presentation nào. LUÔN chạy đủ 3 bước bắt buộc: (1) Hỏi & thu thập bối cảnh,
  (2) Thực hiện, (3) Xuất kết quả & báo cáo.
---

# AI Slides — Quy trình chuẩn làm slide / báo cáo / PowerPoint

> Triết lý cốt lõi: **AI làm NỘI DUNG & CẤU TRÚC trước, HÌNH THỨC sau.**
> Con người giữ vai trò **kiểm chứng số liệu** và **chốt thẩm mỹ**.
> Đừng bao giờ để AI tự bịa số liệu rồi trình thẳng.

---

## ⚙️ CÁCH KÍCH HOẠT — Bắt buộc chạy đủ 3 STEP

Khi user gọi `/ai-slides` (hoặc nhờ làm slide/báo cáo/PowerPoint), agent **PHẢI**
thực hiện tuần tự 3 bước dưới đây, **KHÔNG được nhảy cóc sang làm luôn**:

### 🟦 STEP 1 — HỎI & THU THẬP BỐI CẢNH (bắt buộc trước tiên)

TUYỆT ĐỐI không bắt tay làm slide khi chưa thu đủ thông tin. Dùng
`ask_user_question` (nếu kênh hỗ trợ) để hỏi 6 mục dưới. **QUY TẮC QUAN TRỌNG:**
mỗi câu hỏi PHẢI kèm sẵn 2–4 gợi ý trả lời để user chỉ việc chọn (phòng khi user
không biết mô tả sao). Luôn có 1 lựa chọn **"Other"** — khi user chọn Other thì
mở ô text để user tự nhập. (Với `ask_user_question`, ô "Other" được UI tự thêm —
KHÔNG cần tự tạo; chỉ cần đưa 2–4 option gợi ý.)

Nếu dữ liệu ở mục 6 dài, dùng `inputType: "textarea"` để user dán vào.

**6 câu hỏi + gợi ý sẵn:**

1. **Chủ đề** slide/báo cáo là gì?
   → gợi ý: `Báo cáo kết quả kinh doanh` · `Kế hoạch / đề xuất dự án` ·
     `Đào tạo nội bộ` · `Giới thiệu sản phẩm` (+ Other để tự nhập)
2. **Đối tượng nghe** là ai?
   → gợi ý: `Sếp / ban lãnh đạo` · `Khách hàng / đối tác` ·
     `Nhà đầu tư` · `Học viên / lớp học` (+ Other)
3. **Mục tiêu** của bài?
   → gợi ý: `Thuyết phục / xin phê duyệt` · `Báo cáo kết quả` ·
     `Đào tạo / hướng dẫn` · `Bán hàng / gọi vốn` (+ Other)
4. **Thời lượng / số slide**?
   → gợi ý: `5 phút (~5 slide)` · `10–15 phút (~10 slide)` ·
     `20–30 phút (~20 slide)` · `Chưa rõ, em tư vấn giúp` (+ Other)
5. **Tông giọng**?
   → gợi ý: `Trang trọng, chuyên nghiệp` · `Thân thiện, gần gũi` ·
     `Truyền cảm hứng` · `Bán hàng, thuyết phục` (+ Other)
6. **Dữ liệu thô** (số liệu / tài liệu nguồn)?
   → gợi ý: `Tôi sẽ dán vào ngay` · `Chưa có, em gợi ý cấu trúc trước` ·
     `Có file, tôi gửi sau` (+ Other / textarea để dán trực tiếp).
   → LƯU Ý: KHÔNG tự bịa số liệu; chỗ nào thiếu đánh dấu `[CẦN BỔ SUNG]`.

7. **Màu sắc / Theme (phong cách thiết kế)?**
   → gợi ý: `Xanh doanh nghiệp (Corporate Blue)` · `Tối sang trọng (Dark Elegant)` ·
     `Tối giản trắng (Minimal Light)` · `Năng động ấm (Vibrant Warm)` (+ Other để
     user mô tả màu/brand riêng, hoặc dán mã màu HEX).
   → Nếu user chọn Other + gửi logo/mã màu thương hiệu → áp đúng màu đó.
   → Nếu user không rõ → mặc định theo tông giọng: trang trọng→Corporate Blue,
     bán hàng/truyền cảm hứng→Vibrant Warm, kỹ thuật→Dark Elegant.

➡️ Nếu user trả lời thiếu, **HỎI LẠI** cho đủ rồi mới sang Step 2.
➡️ Xác nhận lại tóm tắt bối cảnh + đề xuất khung storyline + **theme đã chọn**
   trước khi làm.

#### 🎨 Bảng preset Theme (áp vào khối `style:` của Marp frontmatter)

| Theme | Nền | Chữ | Nhấn (accent) | Hợp với |
|---|---|---|---|---|
| **Corporate Blue** | trắng `#FFFFFF` | `#1A1A1A` | xanh `#0B4F9E` + đỏ `#C0392B` | Báo cáo, lãnh đạo |
| **Dark Elegant** | `#1E1E2E` | `#EDEDED` | tím `#A78BFA` + xanh mint `#34D399` | Pitch, sản phẩm, kỹ thuật |
| **Minimal Light** | `#FAFAFA` | `#222` | đen `#000` + xám `#888` | Tối giản, học thuật |
| **Vibrant Warm** | `#FFF8F0` | `#2B2B2B` | cam `#E67E22` + hồng `#E74C3C` | Bán hàng, truyền cảm hứng |

Ví dụ khối `style:` cho **Corporate Blue**:
```yaml
style: |
  section { font-size: 25px; background:#FFFFFF; color:#1A1A1A; }
  h1, h2 { color:#0B4F9E; }
  strong { color:#C0392B; }
```
Ví dụ **Dark Elegant**:
```yaml
style: |
  section { background:#1E1E2E; color:#EDEDED; font-size:25px; }
  h1, h2 { color:#A78BFA; }
  strong { color:#34D399; }
```
> Khi user chọn theme → thay khối `style:` tương ứng, giữ nguyên cấu trúc slide.
> Với brand riêng: đổi accent = màu logo, giữ nền/chữ tương phản đủ đọc.

### 🟩 STEP 2 — THỰC HIỆN

Chỉ bắt đầu khi Step 1 đã đủ dữ liệu:
1. Dựng **storyline** theo khung phù hợp (mục 3).
2. Viết **nội dung từng slide** (mục 4 + prompt mẫu mục 5).
3. Sinh **file / bản trình bày** nếu user cần (.pptx, .pdf, markdown...).
4. Bám quy tắc thiết kế (mục 4). Đánh dấu `[CẦN BỔ SUNG]` chỗ thiếu dữ liệu.

### 🟨 STEP 3 — XUẤT KẾT QUẢ & BÁO CÁO

1. Giao **kết quả** (nội dung slide hoặc đường dẫn file).
2. **Báo cáo ngắn**: đã làm gì, số slide, khung dùng, điểm cần user kiểm chứng.
3. Chạy **Checklist** (mục 7) và nêu các số liệu cần user đối chiếu nguồn.
4. Hỏi user có cần **tinh chỉnh** (prompt mục 5.4) không.

---

## 1. Quy trình 4 bước (LUÔN theo thứ tự này)

1. **Chốt thông điệp cốt lõi** — 1 câu: người xem cần NHỚ gì?
2. **Dựng storyline / dàn ý** — logic từng slide (dùng khung ở mục 3).
3. **Viết nội dung từng slide** — bullet, số liệu, tiêu đề dạng câu kết luận.
4. **Thiết kế & sinh file** — chỉ làm cuối cùng, khi nội dung đã chốt.

> AI mạnh nhất ở bước 1–3. Bước 4 chỉ là công cụ.

---

## 2. Cung cấp ngữ cảnh (bước quyết định chất lượng)

Trước khi yêu cầu AI, LUÔN khai báo đủ 5 thứ:

- **Đối tượng nghe:** sếp / khách hàng / hội đồng / lớp học?
- **Mục tiêu:** thuyết phục đầu tư / báo cáo kết quả / đào tạo?
- **Thời lượng:** 5 phút hay 30 phút? → quyết định số slide (~1 slide/phút).
- **Tông giọng:** trang trọng / thân thiện / bán hàng.
- **Dữ liệu thô:** dán số liệu, tài liệu nguồn vào (đừng để AI bịa).

---

## 3. Khung storyline chuẩn (chọn theo mục đích)

| Khung | Dùng khi | Cấu trúc |
|---|---|---|
| **SCQA** | Thuyết phục / đề xuất | Bối cảnh → Vấn đề → Câu hỏi → Giải pháp |
| **What–Why–How** | Đào tạo / giới thiệu | Là gì → Tại sao quan trọng → Làm sao |
| **Pyramid (Minto)** | Báo cáo lãnh đạo | Kết luận trước → luận điểm → dẫn chứng |
| **Before–After–Bridge** | Bán hàng / pitch | Hiện trạng → Viễn cảnh → Cầu nối |
| **STAR** | Tổng kết dự án | Situation → Task → Action → Result |

---

## 4. Quy tắc thiết kế slide

- **1 slide = 1 ý.** Đừng nhồi.
- **Quy tắc 6×6:** tối đa ~6 dòng, ~6 chữ/dòng.
- **Số liệu → biểu đồ**, không để bảng chữ dày.
- **Tiêu đề slide = câu kết luận** ("Doanh thu tăng 32% Q2", không phải "Doanh thu").
- **Nhất quán** font / màu / khoảng cách.
- **Ảnh, icon** minh hoạ thay vì chữ.
- **Slide mở đầu** có hook + **slide kết** có call-to-action rõ.

---

## 5. Bộ Prompt mẫu (copy & điền `[...]`)

### 5.0 Prompt khởi tạo storyline (dùng TRƯỚC mọi loại)

```
Bạn là chuyên gia thiết kế bài thuyết trình.
Chủ đề: [chủ đề]
Đối tượng nghe: [ai]
Mục tiêu: [thuyết phục / báo cáo / đào tạo]
Thời lượng: [X] phút (tương ứng ~[X] slide)
Tông giọng: [trang trọng / thân thiện...]
Dữ liệu tôi cung cấp: [dán số liệu / tài liệu]

Hãy dựng STORYLINE theo khung [SCQA / Pyramid / ...]:
- Liệt kê danh sách slide, mỗi slide 1 tiêu đề dạng CÂU KẾT LUẬN
- Nêu ý chính (bullet) của từng slide
- CHƯA thiết kế, CHƯA viết chi tiết — chỉ khung.
Nếu thiếu dữ liệu, hãy HỎI tôi thay vì tự bịa.
```

### 5.1 Báo cáo kết quả (report / tổng kết)

```
Dựa trên storyline đã chốt, viết nội dung chi tiết từng slide cho BÁO CÁO KẾT QUẢ.
Yêu cầu:
- Áp dụng khung Pyramid: kết luận quan trọng nhất lên đầu mỗi phần.
- Mỗi slide: tiêu đề = câu kết luận có số liệu; 3–5 bullet ngắn.
- Đề xuất loại biểu đồ phù hợp cho mỗi số liệu (cột/đường/tròn) và mô tả trục.
- Thêm 1 slide "Điểm nổi bật" và 1 slide "Bước tiếp theo".
- KHÔNG bịa số; chỉ dùng dữ liệu tôi đưa. Đánh dấu [CẦN BỔ SUNG] nếu thiếu.
```

### 5.2 Pitch deck (gọi vốn / bán hàng)

```
Viết PITCH DECK theo khung Before–After–Bridge, [N] slide.
Cấu trúc chuẩn: Vấn đề → Giải pháp → Thị trường → Sản phẩm →
Mô hình kinh doanh → Lợi thế cạnh tranh → Traction/số liệu →
Đội ngũ → Kêu gọi đầu tư.
Yêu cầu:
- Mỗi slide 1 thông điệp mạnh, ngôn ngữ tự tin, hướng lợi ích.
- Slide đầu có HOOK gây chú ý trong 10 giây.
- Slide traction dùng số liệu tôi đưa: [dán].
- Slide cuối: con số kêu gọi + dùng tiền vào việc gì.
```

### 5.3 Tài liệu đào tạo / giảng dạy

```
Viết SLIDE ĐÀO TẠO chủ đề [X] cho [đối tượng, trình độ], [N] slide.
Áp dụng khung What–Why–How.
Yêu cầu:
- Mở đầu bằng câu hỏi/tình huống thực tế để tạo tò mò.
- Mỗi khái niệm: định nghĩa ngắn + ví dụ đời thực + 1 hình minh hoạ gợi ý.
- Chèn slide "Kiểm tra nhanh" (câu hỏi tương tác) sau mỗi 3–4 slide.
- Kết bằng slide tóm tắt 3 điều cần nhớ + bài tập áp dụng.
- Ngôn ngữ đơn giản, tránh thuật ngữ nếu không giải thích.
```

### 5.4 Prompt tinh chỉnh (dùng sau khi có bản nháp)

```
Rà lại toàn bộ slide và:
1. Rút gọn slide nào vi phạm quy tắc 6×6.
2. Đổi mọi tiêu đề chung chung thành câu kết luận.
3. Chỉ ra slide nào yếu/thừa và đề xuất cắt hoặc gộp.
4. Đảm bảo mạch chuyển giữa các slide logic.
5. Liệt kê mọi số liệu để tôi đối chiếu nguồn.
```

---

## 6. So sánh công cụ AI làm slide

| Công cụ | Điểm mạnh | Điểm yếu | Hợp nhất khi |
|---|---|---|---|
| **Gamma** | Prompt → slide đẹp tự động, sửa nhanh, template hiện đại | Ít kiểm soát chi tiết, khó theo brand chặt | Cần tốc độ, nháp nhanh, cá nhân/startup |
| **Beautiful.ai** | Tự canh layout thông minh, chuyên nghiệp | Trả phí, linh hoạt thấp | Doanh nghiệp cần đồng bộ |
| **Tome** | Kể chuyện dạng cuộn, tích hợp AI narrative | Rời xa format PPT truyền thống | Pitch sáng tạo, sản phẩm |
| **Canva (Magic Design)** | Kho template khổng lồ, dễ tuỳ biến đẹp | Nội dung AI cơ bản, phải tự viết nhiều | Kiểm soát thẩm mỹ, marketing |
| **PowerPoint Copilot** | Ngay trong PPT, hợp môi trường Office/doanh nghiệp | Cần license M365, phụ thuộc data | Công ty dùng Microsoft |
| **Google Slides + Gemini** | Cộng tác real-time, miễn phí cơ bản | Thiết kế AI còn đơn giản | Nhóm dùng Google Workspace |
| **ChatGPT/Claude + Canva/PPT** | Kiểm soát nội dung tối đa, storyline chắc | 2 bước thủ công (viết → dán thiết kế) | Báo cáo quan trọng, cần chuẩn xác |
| **Marp / Slidev (Markdown)** | Version control, code-friendly, tái lập | Cần biết kỹ thuật | Dân dev, tài liệu kỹ thuật |

**Gợi ý chọn nhanh:**
- Cần **nhanh & đẹp**: Gamma.
- Cần **chính xác & kiểm soát**: ChatGPT/Claude viết nội dung → Canva/PPT thiết kế.
- **Môi trường công ty**: PowerPoint Copilot hoặc Google + Gemini.
- **Kỹ thuật / tái lập**: Marp / Slidev.

---

## 7. Checklist trước khi trình bày

- [ ] Thông điệp chính rõ trong 10 giây đầu?
- [ ] Mỗi slide có tiêu đề = câu kết luận?
- [ ] **Đã đối chiếu lại MỌI số liệu AI đưa với nguồn?** (AI hay bịa)
- [ ] Không lỗi chính tả, sai tên riêng?
- [ ] Slide mở (hook) + slide kết (call-to-action) mạnh?
- [ ] Đã tập nói thử — slide chỉ là chỗ dựa, không phải kịch bản đọc?

---

## 8. Cạm bẫy thường gặp

- ❌ Bảo AI "làm slide đẹp" ngay từ đầu → đẹp mà rỗng. Làm nội dung trước.
- ❌ Tin số liệu AI đưa mà không kiểm → sai lệch nguy hiểm.
- ❌ Nhồi 1 slide quá nhiều chữ → không ai đọc.
- ❌ Tiêu đề chung chung ("Giới thiệu", "Kết quả") → mất cơ hội truyền thông điệp.
- ❌ Quên đối tượng nghe → sai tông, sai độ sâu.
