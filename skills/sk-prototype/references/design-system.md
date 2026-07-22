# Design System theo lĩnh vực + Nguyên tắc UI/UX

## Tư vấn màu / font theo ngành (agent dùng để đề xuất)

| Ngành | Màu chủ đạo | Tâm lý màu | Font gợi ý | Ghi chú UI/UX |
|---|---|---|---|---|
| **Fintech / ngân hàng** | navy `#0B3D91`, xanh tiền `#1E8449` | tin cậy, an toàn | Inter, IBM Plex Sans | Số liệu rõ, bảng gọn, ít màu mè, nhấn bảo mật |
| **Y tế / sức khoẻ** | cyan `#0891B2`, trắng | sạch, dịu | Nunito, Source Sans 3 | Nhiều khoảng trắng, icon mềm, chữ dễ đọc |
| **Giáo dục** | dương `#2563EB`, cam `#F59E0B` | thân thiện, khích lệ | Sora, Inter | Tiến trình học rõ, minh hoạ tiết chế |
| **F&B / bán lẻ** | ấm `#E74C3C`/`#E67E22` | thèm, khẩn | Fraunces + Inter | Ảnh lớn, CTA nổi, cảm xúc |
| **SaaS / công nghệ** | indigo `#4F46E5` | hiện đại, sáng tạo | Geist, Inter | Sạch, gradient nhẹ, micro-interaction |
| **Bất động sản / cao cấp** | ink `#111`, đồng `#B8860B` | sang, đẳng cấp | Cormorant + Inter | Tối giản, ảnh full-bleed, whitespace rộng |
| **Trẻ em / giải trí** | đa sắc tươi | vui nhộn | Baloo 2, Fredoka | Bo góc lớn, màu rực, playful (ngoại lệ luxury) |

> Bảng này chỉ là điểm khởi đầu. **Quy tắc phong cách** (clean/luxury/chuyên nghiệp) ở
> SKILL.md ưu tiên cao hơn khi xung đột — giữ tinh thần sang trọng trừ khi user/ngành đòi khác.

## Nguyên tắc thiết kế chung (áp mọi ngành)

- **Thang khoảng cách nhất quán** — 4 / 8 / 16 / 24 / 32 px. Không canh tuỳ hứng.
- **Tối đa 2 font** — 1 display (heading) + 1 body. Dùng font-weight tạo phân cấp.
- **Bảng màu tối giản** — 1 primary + 1 accent + thang xám + màu semantic (success/warn/error).
- **Tương phản WCAG AA** — chữ trên nền phải đọc được.
- **Phân cấp thị giác** — kích cỡ, đậm nhạt, khoảng trắng dẫn mắt.
- **Nhất quán component** — button/card/input/nav dùng chung style toàn hệ thống.

## Design tokens mẫu (HTML + Tailwind)

```html
<style>
  :root {
    --bg: #ffffff;
    --bg-soft: #f5f5f5;
    --text: #111111;
    --muted: #6b7280;
    --accent: #4f46e5;      /* đổi theo brand/ngành */
    --rule: #e5e5e5;
    --space: 8px;           /* nhân theo 1x/2x/3x/4x */
  }
  body { background: var(--bg); color: var(--text); }
  .btn-primary { background: var(--accent); color: #fff; }
</style>
```

## Anti-AI-look (không làm trừ khi user yêu cầu)

- Gradient tím→indigo mặc định "default AI".
- Dark mode + neon glow làm mặc định.
- Blob tròn nhiều màu, glassmorphism dày, multi-layer shadow.
- Emoji làm bullet / icon trang trí (🚀 ✨ 🎯 💡 🔥 ...).
- Illustration hoạt hình rẻ tiền / clipart.
- Font stack chỉ Inter/Roboto/Arial cho toàn bộ hierarchy.
- Pill cluster "AI · Fast · Secure" trên hero.

## Font gợi ý (greenfield)

- **Display:** Fraunces · Newsreader · Sora · Cormorant · DM Sans
- **Body:** Source Sans 3 · DM Sans · IBM Plex Sans · Inter (body-only)
- Load qua Google Fonts; khai báo trong `<style>` / Tailwind config. Có brand → theo brand.
