---
name: btg-landingpage
description: >
  Builds high-conversion landing pages (copy + code) with a fixed CRO workflow.
  Use when the user runs /landing-page or /btg-landingpage, or asks for a landing
  page, trang đích, trang bán hàng, thu lead, waitlist, or product/event launch page.
---

# BTG Landing Page — Trang đích chuyển đổi cao

> Triết lý: **1 trang = 1 mục tiêu = 1 CTA.** Không phải website.
> Nội dung & thông điệp trước, thiết kế sau. **Không bịa** số liệu / testimonial —
> thiếu → `[CẦN BỔ SUNG]`.

Chi tiết: [references/sections.md](references/sections.md), [references/themes.md](references/themes.md), [references/copy.md](references/copy.md).

---

## Quy tắc phong cách (BẮT BUỘC — ưu tiên cao nhất khi thiết kế)

- **Cấm emoji/icon sáo rỗng kiểu AI hay lạm dụng** (🚀 ✨ 🎯 💡 🔥 ⚡ 🎨 ✅ 💪 🌟 …)
  trong UI, headline, section, bullet, nút. Làm trang trông "AI-generated", rẻ tiền, mất chuyên nghiệp.
- **Cần icon → line-icon đơn sắc** (Lucide / Heroicons *outline*, Phosphor thin),
  đồng nhất độ dày nét & kích thước. Không emoji màu. Ưu tiên hơn: **không icon** — dùng
  typography + khoảng trắng để phân cấp.
- **Phong cách RIÊNG, nổi bật** — không layout template chung chung. Điểm nhấn đến từ
  typography có chủ đích (weight tương phản), whitespace rộng, **1 accent màu**, chi tiết
  tinh (divider mảnh, bo góc nhất quán, shadow tiết chế).
- **Ưu tiên tông CLEAN · SANG TRỌNG · LUXURY · CHUYÊN NGHIỆP** (trừ khi brand/ngành đòi
  khác): nền sạch, palette hạn chế (1 primary + xám + 1 accent), font sang, micro-interaction
  tinh tế, không rối mắt.
- **Không stock cliché**: gradient tím-xanh mặc định, blob tròn nhiều màu, emoji trong
  bullet, nút kiểu "Get Started 🚀". Mọi chi tiết phải có chủ đích.

---

## Workflow (3 STEP — không nhảy cóc)

```
STEP 1  Thu thập bối cảnh (+ escape hatch)
   ↓
STEP 2  Thực hiện (thông điệp → section map → copy → thiết kế/code)
   ↓
STEP 3  Xuất kết quả & báo cáo
```

### STEP 1 — Thu thập bối cảnh

#### Escape hatch (đọc trước khi hỏi)

Đếm các mục đã có trong tin nhắn (8 mục bên dưới).

| Tình huống | Hành động |
|---|---|
| Đủ **≥ 6/8** (hoặc đủ: mục tiêu + sản phẩm + CTA + đầu ra) | **Không hỏi lại cả bộ.** Tóm tắt → hỏi phần thiếu → xin xác nhận → STEP 2 |
| User nói "làm luôn" / "bạn tự quyết" | Điền mặc định hợp lý, ghi rõ giả định, `[CẦN BỔ SUNG]` chỗ thiếu bằng chứng |
| Thiếu nhiều (< 6/8) | Hỏi phần còn thiếu (gộp 1 lần), mỗi câu 2–4 gợi ý |

Dùng AskQuestion nếu có; không thì numbered list trong chat. AskQuestion: UI tự thêm Other — không tự tạo option Other. Dữ liệu dài → textarea nếu hỗ trợ.

#### 8 câu hỏi + gợi ý

1. **Mục tiêu chính** — `Thu lead / email` · `Bán sản phẩm/dịch vụ` · `Waitlist / dùng thử` · `Quảng bá sự kiện`
2. **Sản phẩm / dịch vụ** — tên + 1 câu giá trị cốt lõi (text/textarea)
3. **Đối tượng** — `B2B` · `B2C` · `Dev / kỹ thuật` · `Học viên / cá nhân`
4. **CTA chính** — `Mua ngay` · `Để lại email/SĐT` · `Đăng ký dùng thử` · `Đặt lịch / tư vấn`
5. **Tông giọng** — `Chuyên nghiệp, tin cậy` · `Năng động, trẻ trung` · `Sang trọng, tối giản` · `Thân thiện, gần gũi`
6. **Theme** — `Trust Blue (SaaS)` · `Clean Minimal` · `Warm Editorial` · `Brand HEX của tôi`  
   (Tránh mặc định Dark/purple-glow trừ khi user chọn rõ — xem [themes.md](references/themes.md))
7. **Nội dung sẵn** — `Dán ngay` · `Chưa có, viết mẫu + [CẦN BỔ SUNG]` · `Có file/link, gửi sau`
8. **Đầu ra kỹ thuật** — xem **Default output** bên dưới

**Ngôn ngữ trang:** theo ngôn ngữ user (hỏi nếu lẫn VI/EN).

Trước STEP 2: xác nhận tóm tắt + **section map theo mục tiêu** + theme + đường dẫn file sẽ tạo.

#### Default output (câu 8)

| Ưu tiên | Đầu ra |
|---|---|
| 1 | Repo đã có stack (Next/React/Vite…) → **theo convention repo** |
| 2 | User chọn rõ ở câu 8 → theo lựa chọn |
| 3 | Không rõ / greenfield → **HTML tĩnh + Tailwind CDN, 1 file** `landing/<slug>.html` |

Gợi ý lựa chọn khi hỏi:  
`HTML + Tailwind (1 file)` · `React/Next theo repo` · `Chỉ copy (markdown)` · `Mô tả cho Framer/Webflow`

---

### STEP 2 — Thực hiện

Thứ tự bắt buộc:

1. **Chốt thông điệp** — 1 câu lợi ích + 1 CTA label.
2. **Section map theo mục tiêu** — chỉ làm section cần (bảng dưới); chi tiết [sections.md](references/sections.md).
3. **Viết copy** — headline lợi ích cụ thể; không bịa proof.
4. **Thiết kế / code** — theme + **visual rules**; rồi mới sinh file.

#### Section theo mục tiêu (core vs tùy chọn)

| Mục tiêu | Core (bắt buộc) | Tùy chọn | Thường bỏ |
|---|---|---|---|
| **Thu lead** | Hero → Proof → Problem/Solution → Benefits → Form/CTA → FAQ ngắn → Footer | How it works | Pricing đầy đủ |
| **Waitlist / trial** | Hero → Proof → Benefits hoặc How it works → Final CTA (+ form) → Footer | FAQ | Pricing |
| **Bán hàng** | Hero → Proof → Problem/Solution → Benefits → Testimonials → Pricing → FAQ → Final CTA → Footer | How it works | — |
| **Sự kiện** | Hero (ngày/địa điểm) → Proof/host → Agenda ngắn → Speakers (nếu có) → CTA đăng ký → FAQ → Footer | Benefits | Features kiểu SaaS |

Không nhồi đủ 10 block nếu mục tiêu không cần. Chi tiết thứ tự & copy hints: [sections.md](references/sections.md).

#### Hero budget (above the fold) — cứng

Trong viewport đầu **chỉ** gồm:

- Brand / tên sản phẩm (hero-level, không chỉ nav)
- **Một** headline
- **Một** câu phụ ngắn
- **Một** nhóm CTA (primary + optional secondary cùng mục tiêu)
- **Một** visual dominant (full-bleed / nền cạnh-to-cạnh)

**Không** đặt trong hero: hàng stats, schedule, address block, promo chips, floating badges, card lưới, collage.

#### Visual & anti-generic-AI-look (cứng khi code)

- **Một composition** — không dashboard giả.
- **Brand first** — bỏ nav vẫn nhận ra brand/sản phẩm.
- Typography có chủ đích; tránh Inter/Roboto/Arial/system làm display chính nếu tự chọn font.
- Nền có không khí (gradient nhẹ / pattern / ảnh thật) — không flat một màu trống trải; visual chính phải là sản phẩm/ngữ cảnh, không chỉ gradient trang trí.
- **Full-bleed hero**; không inset hero card, không card trong hero.
- **Default: không cards.** Card chỉ khi là khung tương tác (form, pricing toggle…).
- Mỗi section: một việc, một headline, một câu phụ.
- Motion: 2–3 chuyển động có chủ đích (không noise).
- **Tránh** look AI hay gặp: purple→indigo mặc định; cream + terracotta serif cliché; dark mode + glow tím nếu user không chọn; pill clusters; multi-shadow; emoji trang trí.
- Theme preset & CSS variables: [themes.md](references/themes.md). Có brand HEX/logo → ưu tiên brand.

#### CRO (tóm tắt — bám khi viết & layout)

- 1 CTA xuyên suốt, lặp 2–3 vị trí, accent tương phản.
- Headline = lợi ích cụ thể (có số nếu user cung cấp).
- Form tối thiểu field; proof thật > lời hứa.
- Mobile-first, tải nhanh, label/a11y cơ bản (contrast, focus, `label` cho input).
- Form: nếu chưa có endpoint → UI + comment/`[CẦN BỔ SUNG: form action]`, đừng giả POST im lặng như đã nối CRM.

---

### STEP 3 — Xuất kết quả & báo cáo

1. Giao file / nội dung + đường dẫn.
2. Báo cáo ngắn: mục tiêu, CTA, section đã dùng, theme, tech, giả định.
3. Checklist dưới + liệt kê mọi `[CẦN BỔ SUNG]` / số liệu cần user xác nhận.
4. Hỏi tinh chỉnh (copy, section cắt/gộp, theme). Deploy (Vercel/Netlify/Pages) **chỉ khi user hỏi**.

---

## Checklist trước khi giao

- [ ] Hero: là gì – cho ai – lợi ích trong ~5 giây; đúng hero budget?
- [ ] 1 mục tiêu / 1 CTA chính, lặp nhất quán?
- [ ] Section map khớp mục tiêu (không thừa block loãng)?
- [ ] Không bịa proof; chỗ thiếu đã đánh dấu?
- [ ] Form ngắn; mobile ổn; CTA nổi bật?
- [ ] Không rơi vào generic AI look (trừ khi user chọn theme đó)?
- [ ] File đúng default output / convention repo?

## Cạm bẫy

- ❌ Nhiều mục tiêu / nhiều CTA khác nhau.
- ❌ Hero nhồi stats, chips, cards.
- ❌ Headline về “chúng tôi” thay vì lợi ích khách.
- ❌ Bịa testimonial/số liệu.
- ❌ Hỏi lại đủ 8 câu khi user đã gần đủ context.
- ❌ Default dark/purple khi user không chọn.
