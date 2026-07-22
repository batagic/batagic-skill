# Theme preset & chống look AI generic

## Nguyên tắc chọn theme

1. User chọn / gửi HEX/logo → **ưu tiên brand**.
2. Không rõ → map tông giọng:
   - Chuyên nghiệp, tin cậy → **Trust Blue**
   - Sang trọng, tối giản → **Clean Minimal**
   - Thân thiện / B2C ấm → **Warm Editorial**
   - Năng động trẻ → **Warm Editorial** hoặc Brand HEX (tránh Vibrant tím-hồng mặc định)
3. **Modern Dark / purple glow / indigo gradient** chỉ khi user **chọn rõ**.

## Preset (CSS variables gợi ý)

### Trust Blue (SaaS) — mặc định an toàn B2B

| Token | Giá trị |
|---|---|
| `--bg` | `#FFFFFF` |
| `--bg-soft` | `#F1F5F9` |
| `--text` | `#0F172A` |
| `--muted` | `#64748B` |
| `--accent` | `#2563EB` |
| `--accent-contrast` | `#FFFFFF` |

Không khí: soft gradient `#F8FAFC` → `#EFF6FF` hoặc grid nhẹ; ảnh sản phẩm thật.

### Clean Minimal

| Token | Giá trị |
|---|---|
| `--bg` | `#FFFFFF` |
| `--text` | `#111111` |
| `--muted` | `#6B7280` |
| `--accent` | `#111111` (hoặc 1 accent tươi user chọn, vd. `#0D9488`) |
| `--rule` | `#E5E5E5` |

Typography mạnh, nhiều khoảng trắng; accent tối giản — một màu nhấn cho CTA.

### Warm Editorial (thay cho “Vibrant Gradient” tím-hồng mặc định)

| Token | Giá trị |
|---|---|
| `--bg` | `#F7F4EF` |
| `--text` | `#1A1A1A` |
| `--muted` | `#5C5C5C` |
| `--accent` | `#0F766E` |
| `--accent-2` | `#B45309` (chỉ dùng sparingly) |

Tránh công thức AI hay gặp: cream `#F4F1EA` + serif display + terracotta làm accent chính. Ưu tiên teal/ink + ảnh thật; đổi hết token theo brand khi có HEX.

### Modern Dark (opt-in)

| Token | Giá trị |
|---|---|
| `--bg` | `#0B0B12` |
| `--text` | `#E5E7EB` |
| `--accent` | do user chọn (tránh `#8B5CF6` glow mặc định) |
| `--accent-2` | `#22D3EE` chỉ nếu hợp brand |

Cấm: glow tím lan, gradient purple→indigo toàn trang trừ khi brand yêu cầu.

## Anti-patterns (không làm trừ khi user yêu cầu)

- Purple-on-white / purple→indigo làm “default AI”
- Dark mode + neon glow làm mặc định
- Hero dạng card bo góc nổi giữa nền
- Hàng pill “AI · Fast · Secure” trên hero
- Multi-layer shadow + glassmorphism dày
- Emoji làm bullet chính
- Font stack chỉ Inter/Roboto/Arial cho toàn bộ hierarchy

## Font gợi ý (khi greenfield HTML)

- Display: `"Fraunces"` / `"Newsreader"` / `"Sora"` / `"DM Sans"` (một cặp display + body)
- Body: `"Source Sans 3"` / `"DM Sans"` / `"IBM Plex Sans"`
- Load qua Google Fonts hoặc system fallback có chủ đích; khai báo trong `<style>` / Tailwind config.

## Áp dụng nhanh HTML + Tailwind

```html
<style>
  :root {
    --bg: #ffffff;
    --text: #0f172a;
    --accent: #2563eb;
  }
  body { background: var(--bg); color: var(--text); }
  .btn-primary { background: var(--accent); color: #fff; }
</style>
```

Brand HEX: gán `--accent` (và tương phản chữ nút) theo logo; giữ `--bg`/`--text` đủ contrast (mục tiêu ~WCAG AA).
