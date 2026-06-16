---
name: cosmos-social-card-skill
description: Generate Rednote/Xiaohongshu cover TEXT (主文字 + 副文字) and post titles from an article, script, screenshots, product notes, subtitles, or photos — then emit a self-contained draggable HTML editor for positioning that text over the user's own cover photo. Grounded in the Cosmosworks e-bike workflow. Use when the user asks for 小红书封面文字, 爆款标题, Rednote/Xiaohongshu cover text or titles, 封面文案, 候选组合, or a cover-text template.
---

# COSMOS Cover-Text & Title Skill

Generate the **words that go on a Rednote cover** and the **post titles** — not the cover image itself. The cover photo is the user's own artifact; this skill owns the copywriting and hands placement control back to the human through a self-contained drag-and-drop HTML editor.

Default brand voice is **Cosmosworks** (editorial e-bike / electric-assist). See `references/brand.md`.

**Where this sits:** this skill **is stage 02「标题+封面文字」of the 小红书工作流 V2** (5 stages: 01 需求确认 → **02 标题+封面文字** → 03 图片制作 → 04 正文撰写 → 05 标签发布). It consumes the 01 task card and hands off to 03/04/05 — see Intake (step 1) and the downstream handoff (step 5). It deliberately does **not** do 03 图组 (that's the user's camera, per 真实感＞精美感).

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

- `references/cover-text.md` — **the heart of the skill.** 封面≠标题, 主+副 structure, char limits (≤10/≤12), SEO keyword = hook, 平视感 tone, emoji-是-过气, 违禁词 list, 真实感＞精美感, 货架感 shelf test, the 9 cover paradigms, and the delivery self-check.
- `references/title-framework.md` — the 3-候选 contract, **标题 15-20字 门槛**, the doc's real **K (12 风格) → H (6 句式) → G (4维矩阵)** stacking order, and **L 权重路由 (账号类型 × 内容类型)**.
- `references/template-editor.md` — how to fill `ZUHE`, deliver the editor, and what it can do.
- `references/brand.md` — Cosmosworks voice + the four cosmos themes (dark / sport / clean / green).
- `references/platform-specs.md` — Rednote ratios and the 3:4 / 900×1200 canvas.
- `references/title-shortener.md` — only if the user also needs a cross-platform short title (e.g. 1:1 reuse).
- `references/content-planning.md` — the compression ladder, when distilling a long source into hooks.
- `references/category-cookbook.md` — to confirm a named Rednote category is in scope.
- `references/legacy/` — the previous carousel image-rendering pipeline. Not part of this flow; read only if explicitly un-pivoting.

## Workflow

### 1. Intake (consumes the 01 任务卡)

This is the input side of the workflow handoff. Mirror the doc's intake, sized to the job:

- **日更走 30 秒答 3 题**：给谁看 / 要什么结果（种草·加微信·活动报名·品牌曝光，选**一个**主目标）/ 必出现什么（产品名·活动信息·关键数据，挑 1-2 项）。3 题答不齐就别动笔。
- **重点项目（新品发布 / 大 Campaign / 投流种子 / 招商 / 外部合作）走完整任务卡 8 项**：给谁看 · 要什么结果（一个主目标）· 在哪个节奏里（单篇/系列、关联节点、预热/引爆/收尾）· **产品事实底料**（哪款 Vapor SL/Oi!/Nomad/Model R/Vapor AL、哪些参数/价格可公开、哪些不能透露）· 活动事实底料 · 资源清单 · **红线**（友商能否点名、供应链内部信息、违禁词）· 参考内容（要链接）。

Then derive what changes the output:

- The source: article / script / product notes / subtitles / screenshots / photos / an existing title.
- The content type (新品发布 / 长测 / 赛事 Recap / 教程 / Vlog / 车主故事 / 观点 …) — routes 风格 via `title-framework.md` 的 **L.2**, and the default cover paradigm.
- Whether the user already has a cover **photo**. 照片型范式（极简摄影 / 经典图文 / 人像抠图 / 多图拼贴）需要真照片；若没有就切到 无照片范式（大字报 / 推荐集锦 / 泥石流 / 表情包）——**不要伪造图**。
- Account type (default 品牌主账号) — feeds **L.1**.

If enough context is present, proceed with reasonable assumptions. If the content involves live product specs, prices, policy, or claims, verify with browsing and avoid stating unverified numbers (also a 红线/违禁词 risk).

### 2. Distill The Source

Compress to the 素材蒸馏 matrix (主体 / 动作 / 数字 / 情绪) — see `title-framework.md`. Pull the one real number and the one real feeling out of the source; those anchor both the title and the cover text. Use `content-planning.md`'s ladder for long inputs.

### 3. Write 3 候选组合

Route first: pick 3-4 candidate **风格** from `title-framework.md` 的 **L.1 (账号类型) × L.2 (内容类型)**. Then for each of the 3 组合 pour a **different** 风格 (K) into a 句式 (H) and fill keywords (G), so 盲选 is a real choice:

1. Write the 标题 — formal/objective, **15-20 字** (优质笔记门槛), 咬住 ≥2 蒸馏维度, 带搜索关键词.
2. Write 主文字 (≤10 字, the emotional hook) and 副文字 (≤12 字, the specific payoff/keyword) — different sentence from the title, same fact.
3. Fold the searchable keyword into the hook line (don't bolt it on).

Then run every line through the **self-check** in `cover-text.md`: 可逆性测试（遮一边都想点、两条是补充非复读）, 封面≠标题, char limits (标题 15-20 / 主 ≤10 / 副 ≤12), size contrast, keyword present, peer tone (no 我来教你), ≤1 emoji, no 违禁词 (最/第一/唯一/…).

### 4. Build The Editor (AI first pass, then human fine-tunes)

The editor has four Claude-set starting states: `ZUHE` (文案), `layout` (文字版式), `bg` (底图缩放/平移), `scrim` (可读性蒙版). **You do a first pass on all four; the human adjusts every one of them in the browser.**

- Copy `assets/cover-text-editor.html` into the task folder.
- Fill the `ZUHE` array with the 3 组合 (`biaoti` / `zhu` / `fu`).
- Set `layout` starting positions to match the chosen 范式 (e.g. 大字报型 → 主文字 large & high; 极简摄影型 → 主文字 压在留白处、字号收敛).
- **If the user gave you the actual cover photo** (pasted into chat), read its composition and pre-set the rest from what you see — this is the "AI 先自己操作" pass:
  - **主体位置 → `layout` x/y**: put 主/副文字 over the emptiest region, not on top of the subject (bike/face).
  - **色彩设计 → `layout` color + `scrim`**: make two deliberate color decisions, not just "white on everything":
      - **主文字**: high contrast against the area where it sits (white on dark/busy, near-black on bright/clean).
      - **副文字**: a different color from 主文字 — pull from the photo's palette, use a complementary accent, or use brand green `#c7ff3e` if it earns its place. The goal is visual hierarchy: 主 and 副 should look intentionally different, not identical.
      - **Scrim**: if the text region is bright or has busy texture, set `scrim.on` with `mode` and `opacity` so text stays readable. A scrim is not always needed — dark photos or clean areas may not need one.
      - Don't default to white for both layers. Make a real design call based on the photo.
  - **构图被裁 → `bg` scale/x/y**: `object-fit:cover` center-crops to 900×1200; if the subject would be cut off or too small, pre-set `bg.scale`/`x`/`y` so the subject stays in frame.
  - Say in your delivery message what you pre-set and why ("背景偏亮，已开底部蒙版 35%；车身偏右，主文字预置在左上留白").
- **If you do NOT have the photo**, leave `bg` at defaults and set `scrim` conservatively; tell the user the first pass is paradigm-based and to load their photo + nudge bg/scrim/text once they see it.
- See `references/template-editor.md` for the full schema and details.

### 5. Deliver (+ downstream handoff to 03/04/05)

Show the user, in the response itself:

1. The 3 候选组合 as plain text (标题 / 主 / 副), so they can read them without opening anything.
2. One line of design rationale (which 范式, which 3 风格 via L.2, why).
3. The absolute path to the editor file + a one-liner: "在浏览器打开，载入你的照片，拖文字到合适位置，切组合盲选，点复制贴进群。"
4. **下游 handoff（接上工作流后三段，简短，不喧宾夺主）：**
   - → **03 图组**：编辑器的 A/B/C 切换器就是 doc 要求的"封面定 3 版做 A/B"工具；提醒图组 ≥5 张、图节奏 钩子→展开→细节→收尾。
   - → **04 正文**：选中标题进正文上方；**开头 2 行复述封面钩子**（即复用主文字）再落到一个具体场景。给出这两行的草稿建议。
   - → **05 标签**：吐一组 **6 维关键词种子**（人群 / 场景 / 产品 / 功效 / 类目 / 竞品），其中产品/场景词与封面里选定的搜索关键词同词，供 tag 直接抄；提醒用精准话题、避大词。

Do not embed usage instructions inside the cover text. Do not render a PNG.

## Non-Negotiables

- **封面 ≠ 标题.** Same fact, different sentence, different info point. This is the rule the whole skill is built around. 合格判据：遮住封面只看标题、遮住标题只看封面，**两边都想点**；两条是"补充"不是"复读"。
- **标题 15-20 字** (小红书官方优质笔记门槛). 主文字 ≤ 10 字, 副文字 ≤ 12 字. Cut, don't shrink.
- One searchable keyword inside the cover text; make it the same word as the emotional hook.
- **平视感**: peer voice, never "我来教你".
- **0 emoji** preferred, max 1.
- No **违禁词** — 最 / 第一 / 唯一 / 国家级 / 顶级 / 首个 and any absolute or unverified claim. Replace superlatives with concrete numbers.
- **真实感 ＞ 精美感.** Don't render a polished graphic — the cover is the user's real photo with our text on top.
- The 3 候选 must be genuinely different angles, for real 盲选.
- Don't re-enable the `references/legacy/` image pipeline without an explicit decision to un-pivot.
