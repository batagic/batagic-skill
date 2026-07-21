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
