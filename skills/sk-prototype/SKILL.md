---
name: sk-prototype
description: >
  Builds a multi-page PROTOTYPE system with a consistent UI/UX design system.
  Use when the user runs /prototype or /sk-prototype, or asks for a prototype,
  mockup, wireframe, demo web app, dashboard, or multi-page system. Always runs
  3 mandatory steps: (1) collect context — MUST ask user journey & workflow, advise
  design system by industry; (2) execute; (3) deliver & report. Three scale tiers:
  Simple / Standard / Professional (increasing page count).
---

# SK Prototype — Xây hệ thống prototype nhiều trang

> Triết lý: **Prototype = luồng người dùng bấm được, không phải 1 trang đẹp.**
> Hiểu **user journey + workflow** trước, rồi mới thiết kế. Design system (màu, font,
> khoảng trắng) chọn theo **lĩnh vực**, không cảm tính.

Chi tiết: [references/journey.md](references/journey.md), [references/pages.md](references/pages.md), [references/design-system.md](references/design-system.md).

---

## Quy tắc phong cách (BẮT BUỘC — ưu tiên cao nhất khi thiết kế)

- **Cấm emoji/icon sáo rỗng kiểu AI hay lạm dụng** (🚀 ✨ 🎯 💡 🔥 ⚡ 🎨 ✅ 💪 🌟 …)
  trong UI, nav, card, nút, tiêu đề. Làm sản phẩm trông "AI-generated", thiếu chuyên nghiệp.
- **Cần icon → line-icon đơn sắc** (Lucide / Heroicons *outline*, Phosphor thin),
  đồng nhất nét & kích thước. Không emoji màu. Ưu tiên hơn: typography + khoảng trắng.
- **Phong cách RIÊNG, nổi bật** — không template chung chung. Điểm nhấn từ typography có
  chủ đích, whitespace rộng, **1 accent màu**, chi tiết tinh (divider mảnh, bo góc nhất quán).
- **Ưu tiên tông CLEAN · SANG TRỌNG · LUXURY · CHUYÊN NGHIỆP** (trừ khi ngành/brand đòi
  khác — vd trẻ em/giải trí): palette hạn chế, font sang, micro-interaction tinh tế.
- **Không stock cliché**: gradient tím-xanh mặc định, blob nhiều màu, emoji trong list.
  Chi tiết anti-AI-look: [references/design-system.md](references/design-system.md).

---

## Workflow (3 STEP — không nhảy cóc)

```
STEP 1  Thu thập bối cảnh (+ escape hatch)
   ↓
STEP 2  Thực hiện (tokens → shell → trang theo journey)
   ↓
STEP 3  Xuất kết quả & báo cáo
```

### STEP 1 — Thu thập bối cảnh

#### Escape hatch (đọc trước khi hỏi)

| Tình huống | Hành động |
|---|---|
| Đủ context (loại + ngành + journey/workflow + mức + đầu ra) | Tóm tắt → hỏi phần thiếu → xác nhận → STEP 2 |
| User "làm luôn" / "tự quyết" | Điền mặc định hợp lý, ghi giả định, `[CẦN BỔ SUNG]` chỗ thiếu |
| Thiếu nhiều | Hỏi phần thiếu (gộp 1 lần), mỗi câu 2–4 gợi ý |

Dùng `ask_user_question` nếu có (UI tự thêm Other — không tự tạo); dữ liệu dài → textarea; ảnh mẫu → file.

#### Câu hỏi + gợi ý (4 nhóm)

**A. Sản phẩm & lĩnh vực**
1. **Loại hệ thống** — `Web app / SaaS dashboard` · `Thương mại điện tử` · `Dịch vụ / booking` · `Admin / nội bộ`
2. **Lĩnh vực / ngành** (quyết định design system) — `Fintech` · `Y tế` · `Giáo dục` · `F&B / bán lẻ` (+ Other, nêu rõ ngành)
3. **Đối tượng** — `B2B` · `B2C` · `Nội bộ nhân viên` · `Dev / kỹ thuật`

**B. User Journey & Workflow (BẮT BUỘC — xem [journey.md](references/journey.md))**
4. **User journey** — người dùng đi qua các bước nào? (textarea). Không rõ → em đề xuất journey mẫu theo loại hệ thống → xin xác nhận.
5. **Workflow / tác vụ chính** — việc cần hoàn thành? (textarea). Không rõ → liệt kê tác vụ điển hình của ngành để chọn.

**C. Quy mô (xem [pages.md](references/pages.md))**
6. **Mức prototype** — `Simple (3–5 trang)` · `Standard (6–10)` · `Professional (11–20)` · `Chưa rõ, tư vấn giúp`. Giải thích khác biệt để user chọn đúng.

**D. Phong cách & tham chiếu**
7. **Website/app mẫu?** — `Có URL, em phân tích` · `Có ảnh (file)` · `Không, em đề xuất theo ngành`.
   Có URL → browser/web_fetch xem; có ảnh → `image` phân tích màu/layout/font. Lấy **tinh thần**, không clone.
8. **Design system** — `Em đề xuất theo ngành` · `Brand của tôi (HEX/font/logo)` · `Sáng / Light` · `Tối / Dark`
9. **Đầu ra** — `HTML + Tailwind nhiều trang` (khuyến nghị) · `1 file điều hướng JS` · `React/Next`

**Ngôn ngữ:** theo user. Trước STEP 2: xác nhận journey + workflow + **danh sách trang theo mức** + design system.

---

### STEP 2 — Thực hiện

Chỉ chạy khi STEP 1 đủ & user đã xác nhận danh sách trang. Thứ tự dựng bắt buộc + tổ chức file: xem [pages.md](references/pages.md).

1. **Design tokens trước** — màu/font/spacing/component chung, mọi trang import.
2. **Shell dùng chung** — header/sidebar/nav nhất quán.
3. **Dựng từng trang theo journey** — liên kết `<a href>` **bấm chuyển được** (không ảnh tĩnh).
4. **Dữ liệu mẫu hợp ngành** — `[CẦN BỔ SUNG]` chỗ cần số thật; không bịa.
5. **Responsive + state** (loading/empty/error) ở mức Standard/Professional.

Design system theo ngành + nguyên tắc UI/UX + anti-AI-look: [design-system.md](references/design-system.md).

---

### STEP 3 — Xuất kết quả & báo cáo

1. Giao hệ thống (đường dẫn thư mục + `index.html` khởi đầu).
2. **Chụp preview** vài trang chính (browser screenshot) cho user nghiệm thu.
3. Báo cáo: journey đã dựng, danh sách trang + liên kết, design system (màu/font/spacing), các `[CẦN BỔ SUNG]`.
4. Chạy checklist + gợi ý bước sau (thêm trang, đổi theme, nối data, deploy — deploy **chỉ khi user hỏi**).

---

## Checklist trước khi bàn giao

- [ ] User journey rõ, các trang **liên kết bấm được** đúng luồng?
- [ ] Design system nhất quán (màu/font/spacing/component) mọi trang?
- [ ] Số trang khớp mức đã chọn?
- [ ] Nội dung mẫu hợp ngành; số thật đánh `[CẦN BỔ SUNG]`, không bịa?
- [ ] Responsive (Standard+); tương phản đạt?
- [ ] Không rơi vào generic AI look / emoji cliché?
- [ ] Có preview screenshot cho user?

## Cạm bẫy

- ❌ Code ngay khi chưa hiểu journey → prototype rời rạc.
- ❌ Mỗi trang một phong cách → mất tính hệ thống (thiếu design tokens chung).
- ❌ Chọn màu/font cảm tính, sai tông ngành.
- ❌ Trang tĩnh không bấm chuyển được.
- ❌ Clone nguyên xi site mẫu (chỉ lấy tinh thần).
- ❌ Chọn nhầm mức quy mô (thừa/thiếu).
