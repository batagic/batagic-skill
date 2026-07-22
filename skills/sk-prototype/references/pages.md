# Quy mô prototype & Bộ trang theo mức

## 3 mức quy mô (gợi ý khi user không rõ)

| Mức | Số trang | Mô tả | Dùng khi |
|---|---|---|---|
| **Simple** | 3–5 | Luồng cốt lõi vừa đủ để demo ý tưởng | Kiểm chứng ý tưởng nhanh, pitch sớm |
| **Standard** | 6–10 | Đầy đủ màn hình chính + phụ | Demo hoàn chỉnh cho stakeholder |
| **Professional** | 11–20 | Gần production: auth, empty/error, settings, responsive | Bàn giao dev, triển khai luôn |

## Bộ trang điển hình

| Mức | Trang |
|---|---|
| **Simple** | Landing/Home · Trang chính (list/dashboard) · Trang chi tiết · (Login) |
| **Standard** | + Onboarding · Form tạo/sửa · Settings · Profile · Empty state · 404 |
| **Professional** | + Auth đầy đủ (login/signup/reset) · Error states · Notifications · Billing · Admin · Search · Modal flows · Responsive các trang chính |

> Chọn đúng mức: làm thừa = tốn thời gian; làm thiếu = không đủ demo. Xác nhận với user.

## Thứ tự dựng (bắt buộc)

1. **Design tokens trước** — 1 file config: màu, font, spacing, component cơ bản
   (button, card, input, nav). Mọi trang import chung.
2. **Shell dùng chung** — header/sidebar/nav nhất quán mọi trang.
3. **Dựng từng trang theo journey** — liên kết `<a href>` để **bấm chuyển trang thật**
   (prototype phải click được, không phải ảnh tĩnh).
4. **Dữ liệu mẫu hợp lý theo ngành** — đánh `[CẦN BỔ SUNG]` chỗ cần số liệu thật.
   KHÔNG bịa số/testimonial thật.
5. **Responsive + các state** (loading/empty/error) — mức Standard/Professional.

## Tổ chức file

```
outputs/<project>/
├── index.html          # trang khởi đầu
├── <page>.html         # các trang, liên kết bằng <a href>
└── assets/             # (nếu tách) css/img dùng chung
```

Mọi trang chia sẻ chung nav + design tokens. Ưu tiên HTML + Tailwind nhiều trang liên kết;
1 file điều hướng bằng tab/JS hoặc React/Next chỉ khi user chọn.
