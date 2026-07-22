# Cài đặt skill `sk-prototype`

Gói quy trình xây hệ thống prototype nhiều trang (user journey → design system → trang bấm được). Default output: HTML + Tailwind nhiều trang liên kết, hoặc theo stack repo.

## Nội dung gói

```
sk-prototype/
├── SKILL.md
├── INSTALL.md
└── references/
    ├── journey.md          # User journey/workflow + journey mẫu theo loại hệ thống
    ├── pages.md            # 3 mức Simple/Standard/Professional + thứ tự dựng
    └── design-system.md    # Design system theo ngành + UI/UX + anti-AI-look
```

File phân phối: **`sk-prototype.skill`** = ZIP (folder `sk-prototype/` ở root archive).

```bash
unzip -l sk-prototype.skill
# Kỳ vọng:
# sk-prototype/SKILL.md
# sk-prototype/INSTALL.md
# sk-prototype/references/...
```

---

## 1. Cursor

### Personal (mọi project)

```bash
cd /đường/dẫn/chứa/sk-prototype.skill
unzip sk-prototype.skill -d /tmp
mkdir -p ~/.cursor/skills
cp -R /tmp/sk-prototype ~/.cursor/skills/sk-prototype
```

### Project skill

```bash
unzip sk-prototype.skill -d /tmp
mkdir -p .cursor/skills
cp -R /tmp/sk-prototype .cursor/skills/sk-prototype
```

Gọi: `/sk-prototype` hoặc `/prototype`, hoặc "dựng prototype / mockup / demo web app…".

---

## 2. Claude.ai

1. Đổi `.skill` → `.zip` nếu UI yêu cầu, hoặc `unzip` rồi nén lại:
   `zip -r sk-prototype.zip sk-prototype`
2. Settings → Capabilities / Skills → Upload → chọn zip có folder `sk-prototype/` ở root.
3. Bật skill trong chat.

---

## 3. OpenClaw

```bash
unzip sk-prototype.skill -d /tmp
mkdir -p ~/.claude/skills
cp -R /tmp/sk-prototype ~/.claude/skills/sk-prototype
# hoặc: .claude/skills/sk-prototype trong repo
```

---

## 4. Cursor Rules (fallback)

Copy thân `SKILL.md` vào `.cursor/rules/sk-prototype.mdc` và giữ `references/` cạnh đó, hoặc dán tóm tắt workflow + quy tắc phong cách + 3 mức quy mô vào User Rules.

---

## 5. ChatGPT / Custom GPT / Projects

Upload `SKILL.md` + `references/`. Instruction:

`When user asks for a prototype/mockup, follow SKILL.md. ALWAYS ask user journey & workflow first. Default: multi-page HTML+Tailwind unless the repo has a stack. Read references/ as needed.`

---

## 6. Copilot / VS Code agents

Đặt skill trong repo (vd. `.github/skills/sk-prototype/`). Thêm vào instructions:

```markdown
For prototypes: follow sk-prototype/SKILL.md (journey-first, design system theo ngành, anti-generic look).
```

---

## 7. Agent Skills (agentskills.io)

Đăng ký path tới folder `sk-prototype` (`name` trong frontmatter phải khớp tên folder).

---

## Kiểm tra sau cài

1. "Default output của sk-prototype?" → HTML + Tailwind nhiều trang (hoặc theo repo).
2. "Dựng prototype cho app đặt lịch" (thiếu context) → **hỏi user journey + workflow trước**, không code ngay.
3. Đủ context → các trang liên kết bấm được, design system nhất quán, không emoji cliché.

---

## Gỡ cài

| Nơi | Gỡ |
|---|---|
| Cursor personal | `rm -rf ~/.cursor/skills/sk-prototype` |
| Cursor project | `rm -rf .cursor/skills/sk-prototype` |
| OpenClaw | `rm -rf ~/.claude/skills/sk-prototype` |
| Claude.ai | Settings → Skills → Remove |
