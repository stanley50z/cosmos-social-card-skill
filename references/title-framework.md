# Title Framework (标题框架)

How the **3 candidate titles** per invocation are generated. The workflow's system is **12 named title styles × 6 sentence structures × a 4-dimension keyword matrix**, cross-referenced by account type and content type.

> The conversation confirms this framework exists and is the replacement for the generic "数字获得感 / 痛点提问 / 颠覆认知" formulas. The full tables live in the user's workflow doc. The structures below reconstruct the framework from the conversation's quoted material and brand fit; tables marked `[recon]` should be **replaced with the workflow doc's actual content** when pasted in.

## Output contract: 3 候选组合

> 3 版标题 × 1 条封面文字 ＝ 3 个候选组合，发群里让同事盲选。

Each invocation produces **3 组合**. In the current (text-generation) direction each 组合 is:

```
标题   —— 偏正式·客观（给正文/搜索）
主文字 —— ≤10 字，偏情绪·网感（封面最大的字）
副文字 —— ≤12 字，一个具体回报点/关键词
```

The three should be **genuinely different angles**, not three rewordings of one idea — that's the whole point of blind-selection (盲选). Vary the title style across the three.

## The 4-dimension keyword matrix

Before writing titles, fill the matrix for the piece (`[recon]` dimension set — confirm against doc):

| 维度 | 问什么 | 例（Vapor SL 长测） |
| --- | --- | --- |
| 主体 (who/what) | 产品/人/场景的核心名词 | Vapor SL / 电助力 |
| 动作 (verb) | 核心动词 | 长测 / 通勤 / 爬坡 |
| 数字 (number) | 一个具体可信的数 | 3千公里 / 一年 / 18% 坡 |
| 情绪 (feeling) | 真实的那一下感受 | 没进过店 / 不喘了 / 戒断地铁 |

每个标题至少咬住 2 个维度，封面文字咬住 情绪 + （主体 或 数字）。

## 12 title styles (标题风格)

`[recon]` — replace with workflow doc's 12. Pick by account/content type below.

1. 数字证据型 — 用一个硬数字背书（"3千公里真实长测"）
2. 反差/反转型 — 预期 vs 现实（"买来通勤，结果周末全在山里"）
3. 暴论/观点型 — 一句立得住的判断（"通勤车不需要中置电机"）
4. 提问/纠结型 — 替读者问出他在搜的问题（"这套助力到底够不够爬坡"）
5. 自嘲/真实流水账型 — 平视、口语（"骑了一年，我把油车卖了"）
6. 避坑/清单型 — "我替你踩过的坑"（注意平视，不要教导口吻）
7. 对比评测型 — A vs B（"中置 vs 轮毂，通勤选哪个"）
8. 长期体验型 — 时间跨度做背书（"一年 / 3千公里 / 第三次进山"）
9. 场景代入型 — 把读者放进具体场景（"早高峰 12km，我再没堵过"）
10. 数据拆解型 — 把一个指标讲透（"坡道 18%，助力到底掉多少"）
11. 决策复盘型 — "我为什么最后选了它/没选它"
12. 冷知识/认知型 — 一个反直觉的事实点

> 注意：每一型都必须过 `cover-text.md` 的 平视感 与 违禁词 检查。教导口吻、绝对化用词会直接废掉一个本来不错的角度。

## 6 sentence structures (句式)

`[recon]` — the syntactic mold the style is poured into:

1. `主体 + 时间/数字 + ：+ 结果` —「骑了一年 Vapor SL：3千公里真实长测」
2. `场景 + ，+ 反转`           —「买来通勤，结果周末全在山里」
3. `疑问句`                   —「这套助力到底够不够爬坡」
4. `第一人称动作 + ，+ 后果`   —「骑了一年，我把油车卖了」
5. `A vs B + ，+ 选择问题`     —「中置 vs 轮毂，通勤选哪个」
6. `数字 + 名词 + ，+ 一句判断` —「坡道 18%，助力没掉多少」

Style chooses *what angle*; structure chooses *the grammar*. A "数字证据型" style can be poured into structure 1 or 6; a "提问型" into structure 3.

## Routing by account & content type

`[recon]` — confirm against the doc's cross-reference table.

| 内容类型 | 优先风格 | 默认范式 (见 cover-text.md) |
| --- | --- | --- |
| 长测 / 长期体验 | 长期体验型 · 数字证据型 | 数字证据型 / 大字报型 |
| 评测 / 对比 | 对比评测型 · 数据拆解型 | 对比型 / 数字证据型 |
| 开箱 / 硬件 | 数字证据型 · 冷知识型 | 实拍特写型 |
| 通勤 / 场景 | 场景代入型 · 自嘲型 | 场景代入型 |
| 选购 / 答疑 | 提问纠结型 · 避坑清单型 | 提问型 / 清单型 |
| 观点 / 暴论 | 暴论观点型 · 反差型 | 大字报型 / 泥石流型 |

## Do / Don't

- **Do** vary the style across the 3 候选 so 盲选 is a real choice.
- **Do** keep titles formal/objective and let 封面文字 carry the emotion.
- **Don't** reuse one of the 12 generic placeholder labels as if it were the doc's real framework — flag `[recon]` rows for the user to replace.
- **Don't** write a title that, shortened, *is* the cover text. See the 封面≠标题 rule in `cover-text.md`.
