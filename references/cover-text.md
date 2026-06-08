# 封面文字 (Cover Text)

How the text that sits **on** the cover image is written. This is the core deliverable of the skill — not the cover image itself. The image is the user's own photo; we generate the words that land on it and the editor template that positions them.

> Sourced from the Cosmosworks workflow doc (Section 02 · 标题+封面文字, Section B · 货架感, Section J · 避坑) plus Rednote cover-text platform research. Where a rule is reconstructed rather than quoted, it is marked `[recon]`.

## The one rule that matters most

> **封面 ＝ 标题，但不重复** —— 是同一件事，但透露不同信息点。

The title and the cover text describe the same content, but they are **not** the same sentence and they do **not** carry the same job:

| | 标题 (title) | 封面文字 (cover text) |
| --- | --- | --- |
| 落点 | 正文上方，给搜索/列表看 | 落在封面图上，给信息流第一眼看 |
| 语气 | 更正式 · 客观 | 偏情绪 · 网感 · 口语 |
| 承担 | "这是什么内容" | "为什么我要点开" |

**Worked example (from the doc):**

```
标题：骑了一年 Vapor SL：3千公里真实长测
封面：谁懂啊，3千公里没进过店
```

Same fact (3000 km, one year). The title states it; the cover text reacts to it. If your cover text is just the title with fewer characters, you have failed this rule.

## 主文字 + 副文字 structure

Cover text is **two fields, not one** (`[recon]` from cover-design research, confirmed by the 大字报+payoff pattern):

- **主文字 (main)** — the emotional hook. The biggest type on the cover. **≤ 10 Chinese characters.** One feeling or one bold claim. This is the "谁懂啊 / 地铁戒断成功 / 爬坡不喘了" line.
- **副文字 (sub)** — the specific payoff or proof. Smaller, sits near the main line. **≤ 12 Chinese characters.** Carries one concrete number/detail: "3千公里没进过店 / 通勤 12km 再没堵过 / 坡道实测 18%".

The main line earns the glance; the sub line earns the tap. Don't merge them into one long line — the size contrast between them is what reads as a poster instead of a caption.

## Character limits (hard)

- 主文字 ≤ 10 字 — one core information point, large font, contrasting color.
- 副文字 ≤ 12 字 — one specific payoff or searchable detail.
- Over the limit ⇒ it stops reading as a headline and starts reading as a sentence. Cut, don't shrink.

## SEO: the hook and the keyword are the same word

Rednote indexes the text **embedded inside the cover image** for search relevance — search drives ~65% of discovery. So:

- Put **one searchable keyword** inside the cover text (ideally in 主文字 or 副文字).
- Make the emotional hook and the SEO keyword the **same word** where possible. Don't bolt a keyword on as dead weight — fold it into the line that already carries the feeling.
- For Cosmosworks that keyword is usually the product/use-case noun: `通勤`, `爬坡`, `长测`, `电助力`, a model name.

## Safe zones (where text is allowed to live)

The feed UI eats both ends of a cover:

- **Top** — avatar + account handle overlay.
- **Bottom** — like / comment / save buttons.

So critical text stays in the **center-upper third**, with **≥ 150px safety margin** top and bottom on a 900×1200 canvas. The editor template draws these as a dashed overlay — keep 主文字 and 副文字 between the two dashed lines. Anything in the margins is gambling that the UI won't cover it.

## Tone: 平视感 (peer, not teacher)

> 叙事立场从"我来教你"变成"我也在练"——平视感是最大的情感连接。

In both 标题 and 封面 avoid the **instructional / lecturing tone**:

- ✗ "教你如何选电助力" → ✓ "我也纠结了三个月才下手"
- ✗ "新手必看的 5 个要点" → ✓ "新手踩过的坑我替你踩了"

Peer voice over expert voice. This is the single biggest emotional connector and the easiest thing to get wrong.

## Emoji: 过气, cut them

> emoji 过气了，不合时宜地放一堆 emoji 真的是灾难。会分段比会放 emoji 重要得多。能不用就不用。

- **0 emoji preferred.** Max 1, only if it genuinely earns its place.
- Good line-breaking / segmentation beats any emoji.

## 违禁词 (banned words)

Flag and remove absolute superlatives and any regulated claim:

- Hard-banned by platform: `最` / `第一` / `唯一` / `国家级` / `顶级` / `首个` and similar absolutes.
- Brand-risk for an e-bike: medical/safety guarantees, range/speed claims stated as absolute fact.

Always run cover text + title through this check before delivering. If a line needs a superlative to work, the line is weak — rewrite it with a concrete number instead (`最快` → `比上一代快 1.8 秒`).

## 真实感 ＞ 精美感

> 反例：儿科笔记用精美卡通图反而像营销内容。正例：改成挂号单照片反而更真实、点击更高。

The words should sound like a real person typed them, not like ad copy. This is why the skill generates **text for the user's own photo** rather than a polished rendered graphic — an over-designed cover reads as marketing and gets scrolled past.

## 货架感 / the shelf test

> 尺寸：竖图 3:4（占双列流最大面积）。
> 测试法：把封面截原图扔到目标受众的真实信息流里跟周围 3 条对比。

Before delivering, imagine (or actually mock) the cover dropped into the real double-column feed next to three neighbors. If it doesn't out-pull them at thumbnail size, the text is wrong — move it, enlarge the main line, or sharpen the hook.

## 9 cover paradigms (封面范式)

The workflow doc names a paradigm table. The two quoted in the conversation are 大字报型 and 泥石流型; the rest below are `[recon]` brand-fitted reconstructions — **replace with your workflow doc's actual table when you paste it in.** Each maps to a content type and notes whether it needs a photo.

| 范式 | 长什么样 | 适合内容 | 需要照片? |
| --- | --- | --- | --- |
| 大字报型 | 一句超大主文字压满上半屏 | 观点 / 暴论 / 情绪 | 否（纯色或弱底图即可） |
| 泥石流型 | 多行口语堆叠、像聊天截图 | 吐槽 / 真实体验流水账 | 否 |
| 数字证据型 `[recon]` | 一个大数字 + 短副文字背书 | 长测 / 评测 / 数据 | 弱 |
| 对比型 `[recon]` | 前/后、有/无 双栏 | 改装 / 升级 / 减重 | 是 |
| 实拍特写型 `[recon]` | 产品/细节特写 + 角标小字 | 开箱 / 硬件细节 | 是（必须） |
| 场景代入型 `[recon]` | 使用现场照 + 一句主文字 | 通勤 / 骑行场景 | 是（必须） |
| 清单型 `[recon]` | 主文字点题 + 副文字"N 件事" | 攻略 / 避坑 | 否 |
| 提问型 `[recon]` | 一句疑问句主文字 | 选购纠结 / 答疑 | 否 |
| 反差型 `[recon]` | 预期 vs 现实，主副互相打脸 | 体验反转 | 弱 |

Paradigms marked 需要照片 = 是 require a real photo from the user — the skill generates the text layer to sit on it, not the photo. If the user has no photo for a photo-required paradigm, switch to a no-photo paradigm rather than faking an image.

## Self-check before delivery

- [ ] 封面 ≠ 标题 — different sentence, same fact, different info point.
- [ ] 主文字 ≤ 10 字, 副文字 ≤ 12 字.
- [ ] Size contrast between 主 and 副 is obvious.
- [ ] One searchable keyword lives inside the cover text.
- [ ] Text sits between the 150px safe-zone lines.
- [ ] Peer tone — no "我来教你".
- [ ] 0 (max 1) emoji.
- [ ] No 违禁词 (最/第一/唯一/…).
- [ ] Passes the shelf test against 3 neighbors at thumbnail size.
