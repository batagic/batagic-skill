---
name: prototype
description: >
  Quy trình chuẩn để dùng AI xây một HỆ THỐNG PROTOTYPE (nhiều trang) có thiết kế
  UI/UX nhất quán. Kích hoạt bằng /prototype hoặc khi user muốn dựng prototype,
  mockup, wireframe, demo web app, dashboard, hệ thống nhiều trang. LUÔN chạy đủ
  3 bước bắt buộc: (1) Hỏi & thu thập bối cảnh — BẮT BUỘC hỏi user journey &
  workflow, tư vấn design system theo lĩnh vực; (2) Thực hiện; (3) Xuất & báo cáo.
  Có 3 mức quy mô: Simple / Standard / Professional tương ứng số trang tăng dần.
---

# Prototype — Quy trình xây hệ thống prototype nhiều trang

> Triết lý cốt lõi: **Prototype = luồng người dùng có thể bấm được, không phải 1 trang đẹp.**
> Phải hiểu **user journey + workflow** trước, rồi mới thiết kế. Design system
> (màu, font, khoảng trắng) chọn theo **lĩnh vực**, không theo cảm tính.

---

## ⚙️ CÁCH KÍCH HOẠT — Bắt buộc chạy đủ 3 STEP

Khi user gọi `/prototype`, agent **PHẢI** thực hiện tuần tự 3 bước.
**KHÔNG được code khi chưa hiểu rõ user journey & workflow.**

### 🟦 STEP 1 — HỎI & THU THẬP BỐI CẢNH (bắt buộc trước tiên)

Dùng `ask_user_question` (mỗi câu kèm 2–4 gợi ý + "Other"; dữ liệu dài dùng
`textarea`; ảnh mẫu dùng `file`). Hỏi đủ các nhóm sau:

**A. Sản phẩm & lĩnh vực**
1. **Loại hệ thống?**
   → gợi ý: `Web app / SaaS dashboard` · `Thương mại điện tử` ·
     `Trang dịch vụ / booking` · `Nội bộ / admin panel` (+ Other)
2. **Lĩnh vực / ngành?** (quyết định design system)
   → gợi ý: `Fintech / ngân hàng` · `Y tế / sức khoẻ` · `Giáo dục` ·
     `F&B / bán lẻ` (+ Other — nêu rõ ngành để em chọn màu/font phù hợp)
3. **Đối tượng người dùng chính?**
   → gợi ý: `Doanh nghiệp (B2B)` · `Người tiêu dùng (B2C)` ·
     `Nội bộ nhân viên` · `Kỹ thuật/dev` (+ Other)

**B. User Journey & Workflow (TRỌNG TÂM — bắt buộc hỏi)**
4. **User journey — người dùng đi qua những bước nào?**
   → dùng `textarea`. VD: "Đăng ký → onboarding → tạo dự án → mời thành viên → xem báo cáo".
   → **Nếu user không rõ:** em CHỦ ĐỘNG đề xuất journey mẫu theo loại hệ thống +
     lĩnh vực, rồi xin xác nhận trước khi làm.
5. **Workflow / tác vụ chính người dùng cần hoàn thành?**
   → dùng `textarea`. VD: "Tạo hoá đơn, theo dõi thanh toán, xuất báo cáo".
   → Nếu không rõ → em liệt kê các tác vụ điển hình của ngành để user chọn.

**C. Quy mô prototype (số trang)**
6. **Mức độ prototype?** — nếu user không rõ, GỢI Ý 3 mức:
   → `Simple (đơn giản)` — **~3–5 trang**, luồng cốt lõi vừa đủ để demo ý tưởng.
   → `Standard (tiêu chuẩn)` — **~6–10 trang**, đầy đủ các màn hình chính + phụ.
   → `Professional (chuyên gia)` — **~11–20 trang**, gần production: auth, empty
     states, error, settings, responsive, có thể triển khai luôn.
   → Giải thích rõ khác biệt để user chọn đúng nhu cầu.

**D. Phong cách & tham chiếu**
7. **Có website/app mẫu muốn tham khảo phong cách?**
   → gợi ý: `Có URL, em phân tích` · `Có ảnh chụp, em xem` (dùng `file`) ·
     `Không, em tự đề xuất theo ngành` (+ Other).
   → Nếu có URL → dùng browser/web_fetch xem; nếu có ảnh → dùng `image` phân tích
     màu/layout/typography rồi áp tinh thần đó (KHÔNG sao chép nguyên xi).
8. **Design system — tự chọn hay theo gợi ý của em?**
   → gợi ý: `Em tự đề xuất theo ngành` · `Tôi có brand (màu/font/logo)` ·
     `Sáng / Light` · `Tối / Dark` (+ Other / dán HEX + tên font).
9. **Đầu ra kỹ thuật?**
   → gợi ý: `HTML + Tailwind, nhiều trang liên kết` (khuyến nghị) ·
     `1 file HTML điều hướng bằng tab/JS` · `React/Next.js` (+ Other).

➡️ Thiếu thì HỎI LẠI. Trước khi sang Step 2, **xác nhận lại**: journey + workflow +
   danh sách trang (theo mức đã chọn) + design system đề xuất.

---

#### 🎨 Tư vấn Design System theo lĩnh vực (agent dùng để đề xuất)

| Ngành | Màu chủ đạo | Tâm lý màu | Font gợi ý | Ghi chú UI/UX |
|---|---|---|---|---|
| **Fintech / ngân hàng** | xanh navy `#0B3D91`, xanh lá tiền `#1E8449` | tin cậy, an toàn | Inter, IBM Plex Sans | Số liệu rõ, bảng gọn, ít màu mè, nhấn bảo mật |
| **Y tế / sức khoẻ** | xanh cyan `#0891B2`, trắng | sạch sẽ, dịu | Nunito, Source Sans | Nhiều khoảng trắng, icon mềm, chữ dễ đọc |
| **Giáo dục** | xanh dương `#2563EB`, cam `#F59E0B` | thân thiện, khích lệ | Poppins, Inter | Vui, minh hoạ, tiến trình học rõ |
| **F&B / bán lẻ** | đỏ/cam ấm `#E74C3C`/`#E67E22` | thèm, khẩn | Playfair + Inter | Ảnh lớn, CTA nổi, cảm xúc |
| **SaaS / công nghệ** | tím `#7C3AED`, indigo `#4F46E5` | hiện đại, sáng tạo | Inter, Geist | Sạch, gradient nhẹ, micro-interaction |
| **Bất động sản / cao cấp** | đen `#111`, vàng đồng `#B8860B` | sang, đẳng cấp | Cormorant + Inter | Tối giản, ảnh full-bleed, nhiều khoảng trắng |
| **Trẻ em / giải trí** | đa sắc tươi | vui nhộn | Baloo, Fredoka | Bo góc lớn, màu rực, playful |

**Nguyên tắc chung khi thiết kế (áp mọi ngành):**
- **Thang khoảng cách nhất quán** (4/8/16/24/32px) — đừng canh tuỳ hứng.
- **Tối đa 2 font** (1 heading + 1 body); dùng font-weight tạo phân cấp.
- **Bảng màu**: 1 primary + 1 accent + thang xám (grays) + màu semantic (success/warn/error).
- **Tương phản đủ** (WCAG AA): chữ trên nền phải đọc được.
- **Phân cấp thị giác** rõ: kích cỡ, đậm nhạt, khoảng trắng dẫn mắt.
- **Nhất quán component**: nút, card, input dùng chung style toàn hệ thống.

---

### 🟩 STEP 2 — THỰC HIỆN

Chỉ bắt đầu khi Step 1 đủ dữ liệu & user đã xác nhận danh sách trang.

**Số trang theo mức đã chọn:**

| Mức | Số trang | Bộ trang điển hình |
|---|---|---|
| **Simple** | 3–5 | Landing/Home · Trang chính (list/dashboard) · Trang chi tiết · (Login) |
| **Standard** | 6–10 | + Onboarding · Form tạo/sửa · Settings · Profile · Empty state · 404 |
| **Professional** | 11–20 | + Auth đầy đủ (login/signup/reset) · Error states · Notifications · Billing · Admin · Responsive · Search · Modal flows |

**Cách dựng (khuyến nghị HTML + Tailwind nhiều trang):**
1. **Tạo design system trước** — 1 file `styles`/config Tailwind: bảng màu, font,
   spacing, component cơ bản (button, card, input, nav). Mọi trang import chung.
2. **Dựng shell dùng chung** — header/sidebar/nav nhất quán mọi trang.
3. **Dựng từng trang theo journey** — liên kết `<a href>` để **bấm chuyển trang thật**
   (prototype phải click được, không phải ảnh tĩnh).
4. **Dữ liệu mẫu hợp lý** — điền nội dung thực tế theo ngành; đánh `[CẦN BỔ SUNG]`
   chỗ cần số liệu thật (KHÔNG bịa số/testimonial thật).
5. **Responsive + các state** (loading/empty/error) tuỳ mức Standard/Professional.

Tổ chức file: `outputs/<project>/` gồm `index.html`, các trang `.html`, và
(nếu tách) `assets/`. Mọi trang chia sẻ chung nav + design tokens.

---

### 🟨 STEP 3 — XUẤT KẾT QUẢ & BÁO CÁO

1. Giao **hệ thống prototype** (đường dẫn thư mục + trang khởi đầu `index.html`).
2. **Chụp preview** vài trang chính (browser screenshot) để user nghiệm thu nhanh.
3. **Báo cáo**: sơ đồ journey đã dựng, danh sách trang + liên kết, design system
   (màu/font/spacing) đã áp, các chỗ `[CẦN BỔ SUNG]`.
4. Chạy **Checklist** + gợi ý bước sau (thêm trang, đổi theme, nối data, deploy).

---

## Checklist trước khi bàn giao prototype

- [ ] User journey rõ ràng, các trang **liên kết bấm được** theo đúng luồng?
- [ ] Design system nhất quán (màu/font/spacing/component) trên MỌI trang?
- [ ] Số trang khớp mức đã chọn (Simple/Standard/Professional)?
- [ ] Nội dung mẫu hợp ngành; số liệu thật đánh `[CẦN BỔ SUNG]`, không bịa?
- [ ] Responsive (ít nhất mức Standard trở lên)?
- [ ] Tương phản màu đạt, chữ dễ đọc?
- [ ] Có preview screenshot cho user nghiệm thu?

## Cạm bẫy thường gặp

- ❌ Code ngay khi chưa hiểu user journey → prototype rời rạc, không thành hệ thống.
- ❌ Mỗi trang một phong cách → mất tính hệ thống. Phải có design tokens chung.
- ❌ Chọn màu/font theo cảm tính, không theo lĩnh vực → sai tông ngành.
- ❌ Trang tĩnh không bấm chuyển được → không phải prototype đúng nghĩa.
- ❌ Sao chép nguyên xi site mẫu → chỉ lấy *tinh thần* (màu/layout/nhịp), không clone.
- ❌ Chọn nhầm mức quy mô → làm thừa (tốn thời gian) hoặc thiếu (không đủ demo).
