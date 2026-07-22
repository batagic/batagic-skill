---
name: sk-slides
description: >
  Builds high-quality presentation content and Marp slide decks from user context.
  Use when the user runs /ai-slides or /sk-slides, or asks for slides, PowerPoint,
  pitch deck, báo cáo, bài thuyết trình, tài liệu đào tạo, or any presentation.
---

# SK Slides — Quy trình làm slide / báo cáo / PowerPoint

> Triết lý: **AI làm NỘI DUNG & CẤU TRÚC trước, HÌNH THỨC sau.**
> Con người kiểm chứng số liệu và chốt thẩm mỹ.
> **Không bao giờ bịa số liệu.** Thiếu → đánh dấu `[CẦN BỔ SUNG]`.

**Output mặc định:** file Marp Markdown `.md` (ví dụ `slides/<ten-de-tai>.md`).
Chỉ xuất `.pptx` / PDF / tool khác khi user yêu cầu rõ.

Chi tiết thêm: [references/prompts.md](references/prompts.md), [references/tools.md](references/tools.md).

---

## Quy tắc phong cách (BẮT BUỘC — ưu tiên cao nhất khi thiết kế)

- **Cấm emoji/icon sáo rỗng kiểu AI hay lạm dụng** (🚀 ✨ 🎯 💡 🔥 ⚡ 🎨 ✅ 💪 🌟 …)
  trên slide, tiêu đề, bullet. Làm deck trông "AI-generated", thiếu chuyên nghiệp.
- **Cần icon → line-icon đơn sắc** (Lucide / Heroicons *outline*, Phosphor thin),
  đồng nhất nét & kích thước. Không emoji màu. Ưu tiên hơn: dùng typography + khoảng trắng.
- **Phong cách RIÊNG, nổi bật** — không template chung chung. Điểm nhấn từ typography có
  chủ đích, whitespace rộng, **1 accent màu**, chi tiết tinh (divider mảnh, canh lề chuẩn).
- **Ưu tiên tông CLEAN · SANG TRỌNG · LUXURY · CHUYÊN NGHIỆP** (trừ khi brand/ngành đòi
  khác): palette hạn chế, font sang, không rối mắt, không thừa màu.
- **Không stock cliché**: gradient tím-xanh mặc định, clipart, emoji trang trí trong bullet.

---

## Workflow duy nhất (3 STEP — không nhảy cóc)

```
STEP 1  Thu thập bối cảnh (+ escape hatch)
   ↓
STEP 2  Thực hiện (4 sub-step nội bộ)
   ↓
STEP 3  Xuất kết quả & báo cáo
```

### STEP 1 — Thu thập bối cảnh

#### Escape hatch (đọc trước khi hỏi)

Đếm các mục đã có trong tin nhắn user (7 mục bên dưới).

| Tình huống | Hành động |
|---|---|
| Đủ **≥ 5/7** mục (hoặc đủ để dựng storyline + có dữ liệu/ chủ đề rõ) | **Không hỏi lại cả bộ.** Tóm tắt bối cảnh → hỏi phần còn thiếu (nếu có) → xin xác nhận → sang STEP 2 |
| User nói "làm luôn" / "bạn tự quyết" | Điền mặc định hợp lý, ghi rõ giả định, đánh dấu `[CẦN BỔ SUNG]` chỗ thiếu số liệu |
| Thiếu nhiều (< 5/7) | Hỏi các mục còn thiếu (có thể gộp 1 lần), kèm 2–4 gợi ý + Other |

Dùng AskQuestion / `ask_user_question` nếu kênh hỗ trợ; không thì hỏi numbered list trong chat. Mỗi câu kèm **2–4 gợi ý**. Với AskQuestion, UI tự thêm Other — không tự tạo option Other.

#### 7 câu hỏi + gợi ý

1. **Chủ đề** — `Báo cáo kết quả kinh doanh` · `Kế hoạch / đề xuất dự án` · `Đào tạo nội bộ` · `Giới thiệu sản phẩm`
2. **Đối tượng nghe** — `Sếp / ban lãnh đạo` · `Khách hàng / đối tác` · `Nhà đầu tư` · `Học viên / lớp học`
3. **Mục tiêu** — `Thuyết phục / xin phê duyệt` · `Báo cáo kết quả` · `Đào tạo / hướng dẫn` · `Bán hàng / gọi vốn`
4. **Thời lượng / số slide** — `5 phút (~5 slide)` · `10–15 phút (~10 slide)` · `20–30 phút (~20 slide)` · `Chưa rõ, tư vấn giúp`
5. **Tông giọng** — `Trang trọng, chuyên nghiệp` · `Thân thiện, gần gũi` · `Truyền cảm hứng` · `Bán hàng, thuyết phục`
6. **Dữ liệu thô** — `Tôi sẽ dán vào ngay` · `Chưa có, gợi ý cấu trúc trước` · `Có file, gửi sau`  
   (dữ liệu dài → textarea nếu có). **Không bịa số.**
7. **Theme thiết kế** — `Corporate Blue` · `Dark Elegant` · `Minimal Light` · `Vibrant Warm`  
   Other → user mô tả / HEX / logo. Không rõ → map: trang trọng→Corporate Blue; bán hàng/cảm hứng→Vibrant Warm; kỹ thuật→Dark Elegant.

**Ngôn ngữ slide:** theo ngôn ngữ user đang dùng (hoặc hỏi nếu lẫn VI/EN).

Trước STEP 2: xác nhận tóm tắt bối cảnh + khung storyline đề xuất + theme.

---

### STEP 2 — Thực hiện (4 sub-step, đúng thứ tự)

Chỉ chạy khi STEP 1 đã đủ (hoặc đã áp escape hatch).

1. **Chốt thông điệp cốt lõi** — 1 câu: người xem cần NHỚ gì?
2. **Dựng storyline** — chọn khung theo mục tiêu (bảng dưới); liệt kê slide với tiêu đề = câu kết luận.
3. **Viết nội dung từng slide** — bullet ngắn, số liệu thật hoặc `[CẦN BỔ SUNG]`; đề xuất loại biểu đồ nếu có số.
4. **Thiết kế & sinh file** — áp theme vào Marp frontmatter `style:`; ghi file `.md`. Chỉ làm sau khi nội dung đã chốt.

#### Khung storyline

| Khung | Dùng khi | Cấu trúc |
|---|---|---|
| **SCQA** | Thuyết phục / đề xuất | Bối cảnh → Vấn đề → Câu hỏi → Giải pháp |
| **What–Why–How** | Đào tạo / giới thiệu | Là gì → Tại sao → Làm sao |
| **Pyramid (Minto)** | Báo cáo lãnh đạo | Kết luận trước → luận điểm → dẫn chứng |
| **Before–After–Bridge** | Bán hàng / pitch | Hiện trạng → Viễn cảnh → Cầu nối |
| **STAR** | Tổng kết dự án | Situation → Task → Action → Result |

#### Quy tắc thiết kế

- 1 slide = 1 ý; quy tắc **6×6** (~6 dòng, ~6 chữ/dòng).
- Tiêu đề = **câu kết luận** (có số liệu nếu có), không phải nhãn chung ("Doanh thu").
- Số liệu → biểu đồ; ảnh/icon minh họa thay chữ dày.
- Slide mở = hook; slide kết = CTA rõ.
- Nhất quán font / màu / khoảng cách theo theme.

#### Theme preset (Marp `style:`)

| Theme | Nền | Chữ | Accent |
|---|---|---|---|
| **Corporate Blue** | `#FFFFFF` | `#1A1A1A` | `#0B4F9E` + `#C0392B` |
| **Dark Elegant** | `#1E1E2E` | `#EDEDED` | `#A78BFA` + `#34D399` |
| **Minimal Light** | `#FAFAFA` | `#222` | `#000` + `#888` |
| **Vibrant Warm** | `#FFF8F0` | `#2B2B2B` | `#E67E22` + `#E74C3C` |

Corporate Blue:
```yaml
---
marp: true
theme: default
paginate: true
style: |
  section { font-size: 25px; background:#FFFFFF; color:#1A1A1A; }
  h1, h2 { color:#0B4F9E; }
  strong { color:#C0392B; }
---
```

Dark Elegant:
```yaml
style: |
  section { background:#1E1E2E; color:#EDEDED; font-size:25px; }
  h1, h2 { color:#A78BFA; }
  strong { color:#34D399; }
```

Brand riêng: accent = màu logo; giữ nền/chữ tương phản đủ đọc.

#### Mẫu file Marp tối thiểu

```markdown
---
marp: true
theme: default
paginate: true
style: |
  section { font-size: 25px; background:#FFFFFF; color:#1A1A1A; }
  h1, h2 { color:#0B4F9E; }
  strong { color:#C0392B; }
---

# Tiêu đề bài
## Phụ đề / đối tượng

---

# Câu kết luận slide 2
- Bullet ngắn
- Bullet ngắn
```

Lưu mặc định: `slides/<slug-chu-de>.md` trong workspace (tạo thư mục nếu chưa có).

---

### STEP 3 — Xuất kết quả & báo cáo

1. Giao đường dẫn file Marp (và nội dung/preview nếu hữu ích).
2. Báo cáo ngắn: số slide, khung dùng, theme, giả định đã lấy.
3. Chạy checklist dưới; liệt kê mọi số liệu cần user đối chiếu nguồn.
4. Hỏi có cần tinh chỉnh không (rút 6×6, đổi tiêu đề kết luận, cắt/gộp, mạch logic).

Nếu user muốn tool khác (Gamma, PPT…): đọc [references/tools.md](references/tools.md) rồi tư vấn — **không đổi default Marp** trừ khi user chốt.

---

## Checklist trước khi giao

- [ ] Thông điệp chính rõ trong 10 giây đầu?
- [ ] Mỗi slide: tiêu đề = câu kết luận?
- [ ] Mọi số liệu đã gắn nguồn hoặc `[CẦN BỔ SUNG]`?
- [ ] Không lỗi chính tả / sai tên riêng?
- [ ] Hook mở + CTA kết?
- [ ] File Marp mở được (frontmatter `marp: true` + `---` giữa các slide)?

## Cạm bẫy

- ❌ Thiết kế đẹp trước, nội dung sau → rỗng.
- ❌ Bịa / tin số liệu AI không kiểm.
- ❌ Nhồi chữ; tiêu đề chung chung; quên đối tượng nghe.
- ❌ Hỏi lại đủ 7 câu khi user đã cung cấp gần hết (bỏ qua escape hatch).
