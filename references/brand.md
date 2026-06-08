# Brand (Cosmosworks)

The skill defaults to the **Cosmosworks** voice and look — an editorial e-bike / electric-assist brand, not a beauty influencer. This grounds the title styles, cover-text tone, and the editor's theme colors.

> Quoted brand signals from the conversation: editorial e-bike brand, peer voice (平视感), real-over-polished, anti-emoji, the 标题/封面 split, and the four cosmos theme names. Visual-anchor specifics are left open — the conversation flagged them as undecided.

## Voice

- **Peer, not teacher.** "我也在练" not "我来教你". See 平视感 in `cover-text.md`.
- **Real over polished.** A genuine photo + a line a real rider would type beats a rendered ad graphic. 真实感 ＞ 精美感.
- **Specific over superlative.** Concrete numbers (`3千公里`, `坡道 18%`) instead of 最/第一/唯一.
- **Dry, a little self-aware.** Self-deprecating flow ("骑了一年，我把油车卖了") reads truer than hype.

## Themes (editor `--accent` / background)

Four brand themes. The editor defaults to **cosmos-green**. Set the relevant color on the canvas/text via the editor sliders, or change `--accent` / `--bg` in `cover-text-editor.html`.

| theme | 何时用 | 主色 | 背景倾向 |
| --- | --- | --- | --- |
| **cosmos-dark** | 夜骑 / 电影感 / 重型号 key art | 冷白文字 + 单点强调 | 深底图 / 黑 |
| **cosmos-sport** | 运动 / 爬坡 / 性能数据 | 高饱和橙或红 | 动态实拍 |
| **cosmos-clean** | 通勤 / 生活方式 / 极简 | 近黑文字 + 低饱和 | 亮底图 / 浅 |
| **cosmos-green** *(default)* | 户外 / 续航 / 环保叙事 | 荧光绿 `#c7ff3e` | 自然/街景实拍 |

Pick the theme by **content feeling**, not by category lookup — same logic as the title styles. A commuting piece is usually cosmos-clean; a 18% 爬坡实测 is cosmos-sport; a night-ride journal is cosmos-dark.

## Visual anchor (固定识别符号) — doc Section I / ch42 (2025-10)

The workflow names a 视觉锚点 long-term strategy: **固定一个识别符号**（doc 例：黄色手套＋拖鞋），用久了就变成账号识别符号。这是封面长期主义打法——不追单篇爆款，而是建立持续识别度。

doc 给宇宙 E-BIKE 的候选方向（仍需团队拍板选一个）：
- **你本人的墨镜**（人像锚点）
- **某个固定颜色**（cosmos-green `#c7ff3e` 是现成的软锚点）
- **某个固定构图**（如整车永远 3/4 侧 + 同一机位）

一旦敲定，把它当作**可锁定图层**预置进编辑器（与可拖动的 主/副文字分离，不参与盲选切换）。在团队选定之前：保持 cosmos-green 强调色一致作为软锚点，**不要编造一个并不存在的 logo/badge**。

## Out of scope

This brand grounding does **not** mean every request is e-bike. If the user explicitly asks for a different brand/account, switch voice and themes accordingly — but the *structure* (3 候选, 主+副 cover text, 标题≠封面, safe zones, banned-word check) stays the same.
