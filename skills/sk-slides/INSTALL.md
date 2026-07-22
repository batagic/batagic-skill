# Cài đặt skill `sk-slides`

Gói này chứa quy trình chuẩn làm slide/báo cáo (Marp mặc định) dùng được với nhiều agent.

## Nội dung gói

```
sk-slides/
├── SKILL.md                 # Chỉ thị chính cho agent
├── INSTALL.md               # File này
└── references/
    ├── prompts.md           # Instruction / prompt theo loại bài
    └── tools.md             # So sánh công cụ & export Marp
```

File phân phối: **`sk-slides.skill`** = ZIP của thư mục `sk-slides/` (folder nằm ở root archive).

Giải nén kiểm tra:

```bash
unzip -l sk-slides.skill
# Kỳ vọng:
# sk-slides/SKILL.md
# sk-slides/INSTALL.md
# sk-slides/references/prompts.md
# sk-slides/references/tools.md
```

---

## 1. Cursor (IDE / Agent)

### Cách A — Personal skill (mọi project)

```bash
# Giải nén vào thư mục skills cá nhân
unzip sk-slides.skill -d /tmp
cp -R /tmp/sk-slides ~/.cursor/skills/sk-slides
```

Hoặc symlink nếu giữ source trong repo:

```bash
ln -sfn /đường/dẫn/tới/sk-slides ~/.cursor/skills/sk-slides
```

### Cách B — Project skill (chia sẻ theo repo)

```bash
unzip sk-slides.skill -d /tmp
mkdir -p .cursor/skills
cp -R /tmp/sk-slides .cursor/skills/sk-slides
```

### Cách dùng

- Gõ `/sk-slides` hoặc `/ai-slides`, hoặc nhờ “làm slide / pitch deck / báo cáo”.
- Agent đọc `SKILL.md`; khi cần chi tiết sẽ mở `references/`.

**Lưu ý:** Không đặt skill vào `~/.cursor/skills-cursor/` (thư mục nội bộ Cursor).

---

## 2. Claude.ai (web) — Custom Skills

1. Giải nén `sk-slides.skill` (hoặc đổi đuôi `.skill` → `.zip` rồi giải nén).
2. Đảm bảo folder gốc tên `sk-slides` và có `SKILL.md`.
3. Nén lại folder: `zip -r sk-slides.zip sk-slides`
4. Claude.ai → **Settings → Capabilities / Skills → Upload skill** → chọn `sk-slides.zip`.
5. Bật skill trong cuộc trò chuyện.

Cấu trúc upload đúng:

```
sk-slides.zip
└── sk-slides/
    ├── SKILL.md
    └── ...
```

Sai: các file nằm thẳng ở root ZIP (không có folder `sk-slides/`).

---

## 3. Claude Code (CLI)

```bash
unzip sk-slides.skill -d /tmp

# User-level
mkdir -p ~/.claude/skills
cp -R /tmp/sk-slides ~/.claude/skills/sk-slides

# Hoặc project-level
mkdir -p .claude/skills
cp -R /tmp/sk-slides .claude/skills/sk-slides
```

Trong phiên Claude Code, gọi skill khi cần làm presentation / Marp slides.

---

## 4. Cursor Rules (fallback nếu không dùng Skills)

Nếu môi trường chỉ hỗ trợ rules, copy phần thân `SKILL.md` (bỏ YAML nếu rule không cần) vào:

- Project: `.cursor/rules/sk-slides.mdc` (hoặc `.md`)
- Hoặc dán tóm tắt workflow vào User Rules

Giữ link tới `references/` cùng thư mục hoặc dán gọn checklist vào rule.

---

## 5. ChatGPT / Custom GPT / Projects

1. Tải lên `SKILL.md` + cả thư mục `references/` vào **Project files** hoặc knowledge của GPT.
2. Trong system/instructions:  
   `When user asks for slides/pitch/report, follow SKILL.md. Default output is Marp markdown. Read references/ as needed.`
3. User kích hoạt bằng: “Làm theo skill sk-slides” hoặc `/sk-slides`.

---

## 6. GitHub Copilot Chat / VS Code agents

1. Đặt `sk-slides/` trong repo (ví dụ `.github/skills/sk-slides/` hoặc `docs/skills/sk-slides/`).
2. Trong Copilot instructions (`.github/copilot-instructions.md`) thêm:

```markdown
For presentations/slides: read and follow sk-slides/SKILL.md (default Marp).
```

3. Hoặc `@`-mention / attach `SKILL.md` khi bắt đầu task làm slide.

---

## 7. Agent Skills chuẩn mở (agentskills.io / tương thích)

Mọi runtime tuân Agent Skills spec:

1. Giải nén gói.
2. Đăng ký đường dẫn tới folder `sk-slides` (chứa `SKILL.md` + frontmatter `name` / `description`).
3. `name` phải khớp tên folder: `sk-slides`.

---

## Kiểm tra sau khi cài

1. Hỏi agent: “Theo skill sk-slides, output mặc định là gì?” → kỳ vọng **Marp `.md`**.
2. Gọi `/sk-slides` với tin ngắn (“làm slide báo cáo Q2”) → agent phải **hỏi phần thiếu** (không nhảy làm đẹp ngay), hoặc tóm tắt + xác nhận nếu đã đủ context.
3. Yêu cầu đủ context → nhận file `slides/....md` có `marp: true` và theme `style:`.

---

## Gỡ cài đặt

| Nơi cài | Lệnh / thao tác |
|---|---|
| Cursor personal | `rm -rf ~/.cursor/skills/sk-slides` |
| Cursor project | `rm -rf .cursor/skills/sk-slides` |
| Claude Code | `rm -rf ~/.claude/skills/sk-slides` (hoặc `.claude/skills/...`) |
| Claude.ai | Settings → Skills → Remove |

---

## Xem slide Marp

- Extension **Marp for VS Code** / Cursor, hoặc
- `npx @marp-team/marp-cli slides/ten-file.md -o slides/ten-file.pptx`

Chi tiết export: `references/tools.md`.
