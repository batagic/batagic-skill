# batagic-skill

Bộ skill tái sử dụng cho AI agent. Mỗi skill là một file `SKILL.md` markdown thuần —
mang đi đâu cũng chạy được, không phụ thuộc code.

## Skills

### 📊 ai-slides — Làm slide / báo cáo / PowerPoint

Quy trình chuẩn 3 bước bắt buộc để dùng AI tạo bài thuyết trình chất lượng cao:

1. **Hỏi & thu thập bối cảnh** — hỏi đủ 7 mục (chủ đề, đối tượng, mục tiêu,
   thời lượng, tông giọng, dữ liệu, màu/theme), mỗi câu có gợi ý sẵn + ô "Other".
2. **Thực hiện** — dựng storyline → viết nội dung → sinh file.
3. **Xuất kết quả & báo cáo** — giao file + checklist + điểm cần kiểm chứng.

Kèm: khung storyline (SCQA/Pyramid/...), prompt mẫu theo từng loại, 4 preset theme,
bảng so sánh công cụ, checklist chất lượng.

📄 File: [`skills/ai-slides/SKILL.md`](skills/ai-slides/SKILL.md)

### 🖥️ landing-page — Làm trang đích chuyển đổi cao

Quy trình chuẩn 3 bước để dùng AI tạo landing page tối ưu chuyển đổi:

1. **Hỏi & thu thập bối cảnh** — 8 mục (mục tiêu, sản phẩm, đối tượng, CTA,
   tông giọng, màu/theme, nội dung, tech output), mỗi câu có gợi ý + "Other".
2. **Thực hiện** — dựng cấu trúc section chuẩn (Hero → Social proof → Benefits →
   … → Final CTA) theo nguyên tắc CRO → sinh HTML/React/nội dung.
3. **Xuất kết quả & báo cáo** — giao file + checklist + gợi ý deploy.

Kèm: cấu trúc 10 section, nguyên tắc tối ưu chuyển đổi, 4 preset theme,
lựa chọn tech stack, checklist, prompt mẫu.

📄 File: [`skills/landing-page/SKILL.md`](skills/landing-page/SKILL.md)

### 🧩 prototype — Xây hệ thống prototype nhiều trang (UI/UX)

Quy trình chuẩn 3 bước để dựng prototype nhiều trang có design system nhất quán:

1. **Hỏi & thu thập bối cảnh** — BẮT BUỘC hỏi **user journey + workflow**; tư vấn
   design system (màu/font/spacing) theo **lĩnh vực**; hỏi website mẫu (URL/ảnh);
   3 mức quy mô: **Simple (3–5 trang) · Standard (6–10) · Professional (11–20)**.
2. **Thực hiện** — tạo design tokens chung → shell dùng chung → dựng từng trang
   theo journey, **liên kết bấm được**.
3. **Xuất & báo cáo** — giao hệ thống + preview screenshot + checklist.

Kèm: bảng tư vấn design system theo 7 ngành, nguyên tắc UI/UX, checklist, cạm bẫy.

📄 File: [`skills/prototype/SKILL.md`](skills/prototype/SKILL.md)

## Cách dùng ở agent khác

| Agent | Cách cài |
|---|---|
| **OpenClaw / AICoworker** | Copy thư mục `skills/ai-slides/` vào `skills/` của workspace |
| **Cursor** | Đặt nội dung vào `.cursor/rules/ai-slides.mdc` (giữ frontmatter) |
| **Windsurf** | Dán vào `.windsurfrules` |
| **ChatGPT (Custom GPT)** | Dán toàn bộ nội dung vào ô Instructions |
| **Gemini Gem** | Dán vào phần hướng dẫn của Gem |

> Luôn giữ nguyên khối frontmatter `name` + `description` ở đầu file — đó là thứ
> giúp agent biết khi nào kích hoạt skill.

## License

MIT
