# batagic-skill

Bộ skill tái sử dụng cho AI agent. Mỗi skill gồm `SKILL.md` + `INSTALL.md` +
`references/`, và một gói phân phối `.skill` (ZIP) trong `packages/`.

Nguyên tắc chung mọi skill: quy trình **3 STEP** (thu thập bối cảnh → thực hiện →
xuất & báo cáo) và **Quy tắc phong cách** — cấm emoji/icon sáo rỗng kiểu AI, ưu tiên
tông clean · sang trọng · luxury · chuyên nghiệp.

## Skills

| Skill | Kích hoạt | Mô tả |
|---|---|---|
| **sk-slides** | `/ai-slides` · `/sk-slides` | Làm slide / báo cáo / PowerPoint (Marp). Khung storyline, theme, prompt mẫu. |
| **sk-landingpage** | `/landing-page` · `/sk-landingpage` | Trang đích chuyển đổi cao (CRO + code). Hero budget, section map, anti-AI-look. |
| **sk-prototype** | `/prototype` · `/sk-prototype` | Hệ thống prototype nhiều trang. Journey-first, design system theo ngành, 3 mức Simple/Standard/Professional. |

## Cấu trúc

```
batagic-skill/
├── README.md
├── skills/
│   ├── sk-slides/        SKILL.md · INSTALL.md · references/(prompts, tools)
│   ├── sk-landingpage/   SKILL.md · INSTALL.md · references/(sections, themes, copy)
│   └── sk-prototype/     SKILL.md · INSTALL.md · references/(journey, pages, design-system)
└── packages/             *.skill (ZIP đóng gói, tải về cài trực tiếp)
```

## Cách dùng ở agent khác

| Agent | Cách cài |
|---|---|
| **Cursor** | Giải nén `.skill` → copy folder vào `~/.cursor/skills/` hoặc `.cursor/skills/` |
| **OpenClaw** | Copy folder skill vào `~/.claude/skills/` hoặc `.claude/skills/` |
| **Claude.ai** | Đổi `.skill`→`.zip`, upload trong Settings → Skills |
| **ChatGPT (Custom GPT)** | Upload `SKILL.md` + `references/` vào Instructions/Knowledge |

Chi tiết từng agent xem `INSTALL.md` trong mỗi skill. Luôn giữ frontmatter `name` +
`description` — đó là thứ giúp agent biết khi nào kích hoạt.

## License

MIT
