# Template Editor (`assets/cover-text-editor.html`)

The skill's deliverable is **cover text + titles** plus a **self-contained HTML editor** the user opens in a browser to position that text over their own photo. No build step, no dependencies, no Playwright — it opens directly via `file://`.

## What Claude writes vs. what's static

**Claude sets four starting-state objects: `ZUHE`, `layout`, `bg`, `scrim`.** Everything else (drag logic, sliders, safe-zone overlay, copy button, canvas scaling) is static boilerplate that ships unchanged. Each of the four is fully adjustable by the human in the browser — Claude's values are just the first pass.

```js
const ZUHE = [
  { id:'A', biaoti:'…标题…', zhu:'…主文字 ≤10…', fu:'…副文字 ≤12…' },
  { id:'B', biaoti:'…',     zhu:'…',            fu:'…' },
  { id:'C', biaoti:'…',     zhu:'…',            fu:'…' },
];
```

`ZUHE` schema:
- `biaoti` — 标题, formal/objective, goes to the post body (NOT drawn on the cover). Shown in the panel + copy export.
- `zhu` — 主文字, the big emotional line on the cover, ≤10 字.
- `fu` — 副文字, the specific payoff/keyword, ≤12 字.

`layout` — per-layer text styling, shared across all 3 组合:
```js
const layout = {
  zhu:{ x, y, r, size, weight, color, opacity, letter, align },
  fu :{ x, y, r, size, weight, color, opacity, letter, align },
};
```
Pre-set to a sensible position for the chosen paradigm; the user fine-tunes by drag + sliders.

`bg` — background-photo transform (the photo is loaded at runtime; this is how it's framed):
```js
const bg = { scale:100, x:0, y:0 };  // scale 是百分比(100=object-fit:cover 填满); x/y 平移像素
```
The photo uses `object-fit:cover` (center-crop to 900×1200). When Claude has seen the photo, pre-set `scale`/`x`/`y` so the subject isn't cropped off; otherwise leave defaults and let the user zoom/pan.

`scrim` — legibility overlay between photo and text:
```js
const scrim = { on:true, color:'#000000', opacity:35, mode:'bottom' }; // mode: bottom|top|both|full, opacity 0-90
```
Darkens the band behind the text so it stays readable on a bright/busy photo. Pre-set `on`/`mode`/`opacity` from the photo's brightness where the text sits; the user toggles + tunes it.

**Photo-aware first pass:** when the user pasted the actual cover photo into chat, read its composition and pre-set `layout` (text over empty space), `bg` (keep subject in frame), and `scrim` (darken under text where the photo is bright) accordingly. See SKILL.md step 4.

## How to deliver it

1. Copy `assets/cover-text-editor.html` into the task folder as `cover-text-editor.html`.
2. Fill the `ZUHE` array with the 3 候选组合.
3. (Optional) tweak the `layout` starting positions to match the chosen 范式 (e.g. 大字报型 → 主文字 large, high; 数字证据型 → big number as 主, small 副 below).
4. Give the user the absolute path and a one-line "open this in your browser, load your photo, drag to taste."

Do **not** render a PNG — the cover image is the user's own photo. The skill stops at text + editor.

## Editor capabilities (already built in)

- **Two draggable text layers** — 主文字 / 副文字, mirrored by sidebar sliders.
- **Per-layer controls** — X, Y, rotation (−30°…30°), font-size (24–180px), font-weight (100–900), color, opacity, letter-spacing, text-align. Layout is shared across all 3 组合.
- **组合 A/B/C switcher** — hot-swaps the text content while keeping the layout / bg / scrim, for blind selection.
- **Safe-zone overlay** — dashed lines at 150px top (avatar/handle) and 150px bottom (like/comment buttons); toggle on/off. Keep critical text between them.
- **Load background** — user drops their own cover photo; text composes on top live.
- **底图调整** — 缩放(100–260%) + 水平/垂直平移，把主体挪进安全区、修正 object-fit:cover 的死裁。
- **可读性蒙版 / Scrim** — 文字与底图之间的渐变压暗层；开关 + 方向(底/顶/上下/整体) + 颜色 + 浓度，底图太亮时救回文字。
- **Copy 全部** — formats all 3 组合 (标题 + 主 + 副) for one-paste into the WeChat group 盲选 thread.
- **Auto-fit** — canvas scales to viewport height; drag math accounts for the scale so dragging stays 1:1.

## Canvas spec

- 900 × 1200 px (3:4 vertical — 占双列流最大面积).
- `--safe-margin: 150px` top/bottom (edit in CSS if a platform changes its UI overlay).
- Background is the user's photo (`object-fit: cover`) or the theme color when none loaded.

## Why this and not a rendered cover

The conversation's earlier direction rendered HTML→PNG via Playwright. The final direction deliberately **dropped image rendering**: the cover photo must be the user's real artifact (真实感 ＞ 精美感), and the hard problem is *the words and their placement*, not generating pixels. The editor hands placement control to the human while the skill owns the copywriting. See `cover-text.md` for the principles the text obeys.
