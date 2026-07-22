# Cài đặt skill `btg-landingpage`

Gói quy trình landing page chuyển đổi cao (CRO + code). Default output: HTML + Tailwind 1 file, hoặc theo stack repo.

## Nội dung gói

```
btg-landingpage/
├── SKILL.md
├── INSTALL.md
└── references/
    ├── sections.md    # Section map theo mục tiêu + CRO
    ├── themes.md      # Preset theme + anti-generic-AI-look
    └── copy.md        # Hints copy + prompt mẫu
```

File phân phối: **`btg-landingpage.skill`** = ZIP (folder `btg-landingpage/` ở root archive).

```bash
unzip -l btg-landingpage.skill
# Kỳ vọng:
# btg-landingpage/SKILL.md
# btg-landingpage/INSTALL.md
# btg-landingpage/references/...
```

---

## 1. Cursor

### Personal (mọi project)

```bash
cd /đường/dẫn/chứa/btg-landingpage.skill
unzip btg-landingpage.skill -d /tmp
mkdir -p ~/.cursor/skills
cp -R /tmp/btg-landingpage ~/.cursor/skills/btg-landingpage
```

Symlink nếu giữ source trong repo:

```bash
ln -sfn /đường/dẫn/tới/btg-landingpage ~/.cursor/skills/btg-landingpage
```

### Project skill

```bash
unzip btg-landingpage.skill -d /tmp
mkdir -p .cursor/skills
cp -R /tmp/btg-landingpage .cursor/skills/btg-landingpage
```

Gọi: `/btg-landingpage` hoặc `/landing-page`, hoặc “làm landing / trang thu lead…”.

**Không** cài vào `~/.cursor/skills-cursor/`.

---

## 2. Claude.ai

1. Đổi `.skill` → `.zip` nếu UI yêu cầu, hoặc `unzip` rồi nén lại:
   `zip -r btg-landingpage.zip btg-landingpage`
2. Settings → Capabilities / Skills → Upload → chọn zip có folder `btg-landingpage/` ở root.
3. Bật skill trong chat.

---

## 3. Claude Code

```bash
unzip btg-landingpage.skill -d /tmp
mkdir -p ~/.claude/skills
cp -R /tmp/btg-landingpage ~/.claude/skills/btg-landingpage
# hoặc: .claude/skills/btg-landingpage trong repo
```

---

## 4. Cursor Rules (fallback)

Copy thân `SKILL.md` vào `.cursor/rules/btg-landingpage.mdc` và giữ `references/` cạnh đó, hoặc dán tóm tắt workflow + hero budget + anti-AI-look vào User Rules.

---

## 5. ChatGPT / Custom GPT / Projects

Upload `SKILL.md` + `references/`. Instruction:

`When user asks for a landing page, follow SKILL.md. Default: one HTML+Tailwind file unless the repo has a stack. Read references/ as needed.`

---

## 6. Copilot / VS Code agents

Đặt skill trong repo (vd. `.github/skills/btg-landingpage/`). Thêm vào instructions:

```markdown
For landing pages: follow btg-landingpage/SKILL.md (CRO, hero budget, anti-generic look).
```

---

## 7. Agent Skills (agentskills.io)

Đăng ký path tới folder `btg-landingpage` (`name` trong frontmatter phải khớp tên folder).

---

## Kiểm tra sau cài

1. “Default output của btg-landingpage?” → HTML + Tailwind 1 file (hoặc theo repo).
2. “Làm landing thu email” (thiếu context) → hỏi phần thiếu / escape hatch, **không** code ngay trang 10 section.
3. Đủ context → file có hero đúng budget, 1 CTA, không purple-glow mặc định.

---

## Gỡ cài

| Nơi | Gỡ |
|---|---|
| Cursor personal | `rm -rf ~/.cursor/skills/btg-landingpage` |
| Cursor project | `rm -rf .cursor/skills/btg-landingpage` |
| Claude Code | `rm -rf ~/.claude/skills/btg-landingpage` |
| Claude.ai | Settings → Skills → Remove |
