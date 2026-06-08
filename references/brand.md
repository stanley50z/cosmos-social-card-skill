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

## Visual anchor (固定识别符号) — TODO

The workflow mentions a visual-anchor strategy (固定识别符号 + 固定颜色) for brand recognition across the feed, but the conversation left the specifics **undecided**. Once the Cosmosworks VI settles its anchor (a fixed corner mark? a fixed accent color? a fixed type treatment for the model name?), encode it here and pre-place it as a locked layer in the editor template.

Until then: keep the cosmos-green accent consistent as a soft anchor, and don't invent a logo/badge that isn't real.

## Out of scope

This brand grounding does **not** mean every request is e-bike. If the user explicitly asks for a different brand/account, switch voice and themes accordingly — but the *structure* (3 候选, 主+副 cover text, 标题≠封面, safe zones, banned-word check) stays the same.
