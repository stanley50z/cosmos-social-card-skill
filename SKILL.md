---
name: cosmos-social-card-skill
description: Generate Rednote/Xiaohongshu cover TEXT (主文字 + 副文字) and post titles from an article, script, screenshots, product notes, subtitles, or photos — then emit a self-contained draggable HTML editor for positioning that text over the user's own cover photo. Grounded in the Cosmosworks e-bike workflow. Use when the user asks for 小红书封面文字, 爆款标题, Rednote/Xiaohongshu cover text or titles, 封面文案, 候选组合, or a cover-text template.
---

# COSMOS Cover-Text & Title Skill

Generate the **words that go on a Rednote cover** and the **post titles** — not the cover image itself. The cover photo is the user's own artifact; this skill owns the copywriting and hands placement control back to the human through a self-contained drag-and-drop HTML editor.

Default brand voice is **Cosmosworks** (editorial e-bike / electric-assist). See `references/brand.md`.

## What To Produce

Per invocation, **3 候选组合** for blind selection (盲选), each:

```
标题   —— 偏正式·客观，给正文/搜索（不上封面）
主文字 —— ≤10 字，偏情绪·网感，封面最大的字
副文字 —— ≤12 字，一个具体回报点 / 搜索关键词
```

Plus a copy of `assets/cover-text-editor.html` with the `ZUHE` array filled in — a browser-openable editor where the user loads their photo, drags the two text layers, and tunes position / rotation / size / weight / color / opacity / letter-spacing, then copies all 3 组合 into the WeChat group.

Do **not**:
- Render the finished cover image (no Playwright, no PNG export). The photo is the user's.
- Produce full carousels, content pages, WeChat 21:9/1:1 pairs, maps, or screenshot frames. That was the skill's previous direction — see `references/legacy/`.

## Core Rule

> **封面 ＝ 标题，但不重复** —— 同一件事，透露不同信息点。

The title states the fact (formal, objective, searchable). The cover text reacts to it (emotional, 网感, 口语) and answers "为什么我要点开". If your cover text is just the title with fewer characters, you've failed. The canonical example:

```
标题：骑了一年 Vapor SL：3千公里真实长测
封面：谁懂啊 / 3千公里没进过店   ← 主文字 / 副文字
```

## Required References

- `references/cover-text.md` — **the heart of the skill.** 封面≠标题, 主+副 structure, char limits (≤10/≤12), SEO keyword = hook, 150px safe zones, 平视感 tone, emoji-是-过气, 违禁词 list, 真实感＞精美感, 货架感 shelf test, the 9 cover paradigms, and the delivery self-check.
- `references/title-framework.md` — the 3-候选 contract, 12 title styles × 6 sentence structures × 4-dimension keyword matrix, routing by content type.
- `references/template-editor.md` — how to fill `ZUHE`, deliver the editor, and what it can do.
- `references/brand.md` — Cosmosworks voice + the four cosmos themes (dark / sport / clean / green).
- `references/platform-specs.md` — Rednote ratios and the 3:4 / 900×1200 canvas.
- `references/title-shortener.md` — only if the user also needs a cross-platform short title (e.g. 1:1 reuse).
- `references/content-planning.md` — the compression ladder, when distilling a long source into hooks.
- `references/category-cookbook.md` — to confirm a named Rednote category is in scope.
- `references/legacy/` — the previous carousel image-rendering pipeline. Not part of this flow; read only if explicitly un-pivoting.

## Workflow

### 1. Intake

Gather only what changes the output:

- The source: article / script / product notes / subtitles / screenshots / photos / an existing title.
- The content type (长测 / 评测 / 开箱 / 通勤 / 选购 / 观点 …) — routes title styles and the default cover paradigm. See `title-framework.md`.
- Whether the user already has a cover **photo** (most paradigms assume their own photo). If a photo-required paradigm is chosen and the user has none, pick a no-photo paradigm (大字报型 / 泥石流型 / 提问型 / 清单型) instead — do not fake an image.
- Brand/account if not Cosmosworks.

If enough context is present, proceed with reasonable assumptions. If the content involves live product specs, prices, policy, or claims, verify with browsing and avoid stating unverified numbers (also a 违禁词 risk).

### 2. Distill The Source

Compress to the keyword matrix (主体 / 动作 / 数字 / 情绪) — see `title-framework.md`. Pull the one real number and the one real feeling out of the source; those anchor both the title and the cover text. Use `content-planning.md`'s ladder for long inputs.

### 3. Write 3 候选组合

For each of the 3, vary the **title style** so 盲选 is a real choice (don't write three rewordings of one idea):

1. Write the 标题 — formal/objective,咬住 ≥2 matrix dimensions.
2. Write 主文字 (≤10 字, the emotional hook) and 副文字 (≤12 字, the specific payoff/keyword) — different sentence from the title, same fact.
3. Fold the searchable keyword into the hook line (don't bolt it on).

Then run every line through the **self-check** in `cover-text.md`: 封面≠标题, char limits, size contrast, keyword present, peer tone (no 我来教你), ≤1 emoji, no 违禁词 (最/第一/唯一/…).

### 4. Build The Editor

- Copy `assets/cover-text-editor.html` into the task folder.
- Fill the `ZUHE` array with the 3 组合 (`biaoti` / `zhu` / `fu`).
- Optionally set the `layout` starting positions to match the chosen 范式 (e.g. 大字报型 → 主文字 large & high; 数字证据型 → big number as 主, small 副 below). Keep text between the 150px safe-zone lines.
- See `references/template-editor.md` for the schema and details.

### 5. Deliver

Show the user, in the response itself:

1. The 3 候选组合 as plain text (标题 / 主 / 副), so they can read them without opening anything.
2. One line of design rationale (which 范式, which 3 styles, why).
3. The absolute path to the editor file + a one-liner: "在浏览器打开，载入你的照片，拖文字到合适位置，切组合盲选，点复制贴进群。"

Do not embed usage instructions inside the cover text. Do not render a PNG.

## Non-Negotiables

- **封面 ≠ 标题.** Same fact, different sentence, different info point. This is the rule the whole skill is built around.
- 主文字 ≤ 10 字, 副文字 ≤ 12 字. Cut, don't shrink.
- One searchable keyword inside the cover text; make it the same word as the emotional hook.
- Text stays between the 150px top/bottom safe-zone lines.
- **平视感**: peer voice, never "我来教你".
- **0 emoji** preferred, max 1.
- No **违禁词** — 最 / 第一 / 唯一 / 国家级 / 顶级 / 首个 and any absolute or unverified claim. Replace superlatives with concrete numbers.
- **真实感 ＞ 精美感.** Don't render a polished graphic — the cover is the user's real photo with our text on top.
- The 3 候选 must be genuinely different angles, for real 盲选.
- Don't re-enable the `references/legacy/` image pipeline without an explicit decision to un-pivot.
