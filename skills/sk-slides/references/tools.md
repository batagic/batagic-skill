# So sánh công cụ AI làm slide

Chỉ đọc khi user hỏi chọn tool, hoặc muốn xuất ngoài Marp mặc định.

| Công cụ | Điểm mạnh | Điểm yếu | Hợp nhất khi |
|---|---|---|---|
| **Marp / Slidev** | Markdown, version control, tái lập, khớp skill này | Cần preview/export | Dev, tài liệu kỹ thuật, default của skill |
| **Gamma** | Prompt → slide đẹp nhanh, template hiện đại | Ít kiểm soát brand chặt | Nháp nhanh, cá nhân/startup |
| **Beautiful.ai** | Layout thông minh, chuyên nghiệp | Trả phí, ít linh hoạt | Doanh nghiệp cần đồng bộ |
| **Tome** | Narrative dạng cuộn | Khác PPT truyền thống | Pitch sáng tạo |
| **Canva Magic Design** | Template lớn, dễ chỉnh đẹp | Nội dung AI cơ bản | Marketing, thẩm mỹ tay |
| **PowerPoint Copilot** | Trong PPT / Office | Cần M365 | Công ty Microsoft |
| **Google Slides + Gemini** | Cộng tác, miễn phí cơ bản | Thiết kế AI đơn giản | Google Workspace |
| **ChatGPT/Claude + Canva/PPT** | Kiểm soát nội dung tối đa | 2 bước thủ công | Báo cáo quan trọng |

## Gợi ý chọn nhanh

- **Mặc định (skill này):** Marp `.md` trong repo.
- **Nhanh & đẹp:** Gamma (sau khi đã có storyline từ skill).
- **Chính xác & kiểm soát:** Agent viết nội dung → Canva/PPT thiết kế.
- **Công ty Office:** PowerPoint Copilot.
- **Công ty Google:** Slides + Gemini.

## Export từ Marp (khi user cần PPTX/PDF)

1. Cài [Marp CLI](https://github.com/marp-team/marp-cli) hoặc Marp for VS Code.
2. `npx @marp-team/marp-cli slides/ten-file.md -o slides/ten-file.pptx`
3. PDF: thêm `-o slides/ten-file.pdf`

Không commit secrets; không push file slide trừ khi user yêu cầu.
