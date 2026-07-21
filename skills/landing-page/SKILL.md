---
name: landing-page
description: >
  Quy trình chuẩn + best practice để dùng AI làm landing page chuyển đổi cao.
  Kích hoạt bằng /landing-page hoặc khi user muốn tạo trang đích, landing page,
  trang bán hàng, trang thu lead, waitlist, trang giới thiệu sản phẩm/sự kiện/app.
  LUÔN chạy đủ 3 bước bắt buộc: (1) Hỏi & thu thập bối cảnh, (2) Thực hiện,
  (3) Xuất kết quả & báo cáo. Kèm cấu trúc section chuẩn, nguyên tắc tối ưu
  chuyển đổi (CRO), preset theme, lựa chọn tech stack, checklist.
---

# Landing Page — Quy trình chuẩn làm trang đích chuyển đổi cao

> Triết lý cốt lõi: **1 trang = 1 mục tiêu = 1 hành động (CTA).**
> Landing page KHÔNG phải website — mọi thành phần phải phục vụ duy nhất
> một hành động chuyển đổi. Nội dung & thông điệp trước, thiết kế sau.

---

## ⚙️ CÁCH KÍCH HOẠT — Bắt buộc chạy đủ 3 STEP

Khi user gọi `/landing-page` (hoặc nhờ làm trang đích/landing/trang bán hàng),
agent **PHẢI** thực hiện tuần tự 3 bước, **KHÔNG được nhảy cóc sang code luôn**.

### 🟦 STEP 1 — HỎI & THU THẬP BỐI CẢNH (bắt buộc trước tiên)

TUYỆT ĐỐI không code khi chưa đủ thông tin. Dùng `ask_user_question` (nếu kênh
hỗ trợ). **QUY TẮC:** mỗi câu hỏi PHẢI kèm 2–4 gợi ý sẵn để user chọn, luôn có
lựa chọn **"Other"** (UI tự thêm ô text) để user tự nhập. Dữ liệu dài → `textarea`.

**8 câu hỏi + gợi ý sẵn:**

1. **Mục tiêu chính của landing page?**
   → gợi ý: `Thu lead / email` · `Bán sản phẩm/dịch vụ` ·
     `Đăng ký waitlist / dùng thử` · `Quảng bá sự kiện` (+ Other)
2. **Sản phẩm / dịch vụ là gì?** (mô tả ngắn)
   → dùng `text`/`textarea`; yêu cầu user nêu tên + 1 câu giá trị cốt lõi.
3. **Đối tượng khách hàng?**
   → gợi ý: `Doanh nghiệp (B2B)` · `Người tiêu dùng (B2C)` ·
     `Nhà phát triển / kỹ thuật` · `Học viên / cá nhân` (+ Other)
4. **Hành động mong muốn (CTA chính)?**
   → gợi ý: `Mua ngay / thanh toán` · `Để lại email/SĐT` ·
     `Đăng ký dùng thử` · `Đặt lịch / liên hệ tư vấn` (+ Other)
5. **Tông giọng / phong cách?**
   → gợi ý: `Chuyên nghiệp, tin cậy` · `Năng động, trẻ trung` ·
     `Sang trọng, tối giản` · `Thân thiện, gần gũi` (+ Other)
6. **Màu sắc / Theme?**
   → gợi ý: `Xanh tin cậy (SaaS)` · `Tối hiện đại (Dark)` ·
     `Sáng tối giản (Clean)` · `Gradient rực rỡ (Vibrant)` (+ Other / dán HEX/logo)
7. **Nội dung / tài liệu có sẵn?** (text, hình, logo, USP, giá, testimonial)
   → gợi ý: `Tôi sẽ dán vào ngay` · `Chưa có, em gợi ý & viết mẫu` ·
     `Có file/link, gửi sau` (+ Other). KHÔNG bịa số/testimonial; thiếu → `[CẦN BỔ SUNG]`.
8. **Đầu ra kỹ thuật mong muốn?**
   → gợi ý: `HTML tĩnh + Tailwind (1 file, deploy nhanh)` ·
     `React/Next.js component` · `Chỉ cần nội dung (tự dán vào builder)` ·
     `Framer/Webflow-style mô tả` (+ Other)

➡️ Thiếu thì **HỎI LẠI** cho đủ. Xác nhận tóm tắt bối cảnh + đề xuất cấu trúc
   section + theme trước khi sang Step 2.

#### 🎨 Bảng preset Theme

| Theme | Nền | Chữ | Accent | Hợp với |
|---|---|---|---|---|
| **Trust Blue (SaaS)** | trắng | `#0F172A` | xanh `#2563EB` | B2B, SaaS, fintech |
| **Modern Dark** | `#0B0B12` | `#E5E7EB` | tím/mint `#8B5CF6`/`#22D3EE` | Tech, app, dev tool |
| **Clean Minimal** | `#FFFFFF` | `#111` | đen + 1 accent tươi | Cao cấp, tối giản |
| **Vibrant Gradient** | gradient cam-hồng-tím | trắng | vàng `#FACC15` | B2C, sự kiện, trẻ |

---

### 🟩 STEP 2 — THỰC HIỆN

Chỉ bắt đầu khi Step 1 đủ dữ liệu.

**Cấu trúc section chuẩn của landing page chuyển đổi (điều chỉnh theo mục tiêu):**

1. **Hero** — headline (lợi ích lớn nhất) + subheadline + CTA chính + hình/mockup.
2. **Social proof** — logo khách hàng / số liệu / rating (tạo niềm tin sớm).
3. **Problem–Solution** — nêu nỗi đau → cách sản phẩm giải quyết.
4. **Features / Benefits** — 3–6 khối, nhấn **lợi ích** (không chỉ tính năng).
5. **How it works** — 3 bước đơn giản.
6. **Testimonials** — trích dẫn khách hàng thật (đánh `[CẦN BỔ SUNG]` nếu chưa có).
7. **Pricing** (nếu bán) — bảng giá rõ ràng, nhấn gói khuyến nghị.
8. **FAQ** — xử lý phản đối thường gặp.
9. **Final CTA** — nhắc lại hành động + tạo cảm giác khẩn (ưu đãi/giới hạn).
10. **Footer** — liên hệ, chính sách, mạng xã hội.

**Nguyên tắc tối ưu chuyển đổi (CRO) — bám khi viết & thiết kế:**
- **1 CTA xuyên suốt**, lặp lại 2–3 lần, nút nổi bật màu accent.
- **Headline hướng lợi ích + cụ thể** ("Tăng 30% doanh số", không phải "Giải pháp tốt nhất").
- **Above the fold**: hero phải nói rõ *là gì – cho ai – lợi ích* trong 5 giây.
- **Giảm ma sát**: form ngắn nhất có thể (chỉ hỏi field thật cần).
- **Bằng chứng > lời hứa**: số liệu, logo, review thật.
- **Tốc độ & mobile-first**: tối ưu tải nhanh, responsive.
- **Khoảng trắng & phân cấp thị giác** rõ; CTA tương phản cao.

**Sinh đầu ra** theo lựa chọn ở câu 8 (HTML+Tailwind 1 file / React / chỉ nội dung).
Đánh dấu `[CẦN BỔ SUNG]` mọi chỗ thiếu dữ liệu thật.

#### Prompt mẫu (nếu chạy trên agent chỉ soạn nội dung)

```
Viết nội dung landing page cho [sản phẩm], mục tiêu [X], đối tượng [Y], CTA [Z].
Theo cấu trúc: Hero → Social proof → Problem/Solution → Benefits (3–6) →
How it works → Testimonials → Pricing → FAQ → Final CTA → Footer.
Yêu cầu: headline hướng lợi ích cụ thể; 1 CTA nhất quán; copy ngắn, quét nhanh;
tông [tông giọng]; KHÔNG bịa số liệu/review — chỗ thiếu đánh dấu [CẦN BỔ SUNG].
```

---

### 🟨 STEP 3 — XUẤT KẾT QUẢ & BÁO CÁO

1. Giao **kết quả** (file HTML/React hoặc nội dung + đường dẫn).
2. **Báo cáo ngắn**: đã làm gì, các section, theme/tech dùng, chỗ `[CẦN BỔ SUNG]`.
3. Chạy **Checklist** (dưới) + nêu số liệu/nội dung user cần kiểm chứng/bổ sung.
4. Gợi ý **deploy** (Netlify/Vercel/GitHub Pages) và hỏi có cần **tinh chỉnh** không.

---

## Checklist trước khi publish

- [ ] Hero nói rõ *là gì – cho ai – lợi ích* trong 5 giây?
- [ ] Chỉ 1 mục tiêu / 1 CTA chính, lặp lại nhất quán?
- [ ] Headline hướng lợi ích cụ thể (có số nếu được)?
- [ ] Có social proof / bằng chứng thật (không bịa)?
- [ ] Form thu lead ngắn gọn, ít ma sát?
- [ ] Responsive mobile + tải nhanh?
- [ ] Đã thay hết `[CẦN BỔ SUNG]` bằng nội dung thật?
- [ ] CTA nổi bật, tương phản cao, dễ bấm trên mobile?

## Cạm bẫy thường gặp

- ❌ Biến landing page thành website nhiều mục tiêu → loãng, giảm chuyển đổi.
- ❌ Nhồi nhiều CTA khác nhau → user phân vân, không hành động.
- ❌ Headline chung chung, nói về mình thay vì lợi ích khách hàng.
- ❌ Bịa testimonial/số liệu → mất uy tín, rủi ro pháp lý.
- ❌ Form quá dài → tỉ lệ bỏ cao.
- ❌ Bỏ qua mobile → phần lớn traffic đến từ điện thoại.
